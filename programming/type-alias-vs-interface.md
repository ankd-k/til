# Type Alias vs Interfaceの話

TypeScriptでtypeとinterfaceをうまく使い分けたい

→Googleが出しているTypeScriptのコーディングガイドラインがあるらしい  

[Google Typescript Style Guide](https://google.github.io/styleguide/tsguide.html)  
[Zenn - Google TypeScript Style Guideを読む](https://zenn.dev/kakkoyakakko/articles/1031af1d38d038)

これいつ出されたやつかわからん（多くの古い記事にある主張と同じだった）  
typeでできることはinterfaceでできる→今は逆もしかりじゃね？

他言語においてinterfaceは振る舞いを定義するのに使われるから、単にオブジェクトの型を定義するためにinterfaceを用いるのが違和感ある。

個人的にはこれがしっくりきている↓

[クラス、構造体、およびインターフェイスの名前](https://docs.microsoft.com/ja-jp/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces)

TypeScriptでinterfaceのPrefixにIをつけないみたいな話がどこかにあったはず→何個かあったうちの1つ↓  

[You don’t need to prefix Interfaces in Typescript with “I”](https://passionfordev.com/you-dont-need-to-prefix-interfaces-in-typescript-with-i/)

```typescript
// Situation 1: Simple props being passed in:
interface IProps {
  greeting: string,
}

export class InterfacesAreFun extends React.Component<IProps, never> {
  render() {
    return <span>The old world: IProps: {this.props.greeting}</span>
  }
}

// Situation 2: Using Redux with React with dispatch actions:
interface IProps {
  greeting: string,
}

interface IPropsDispatch {
  fetchGreeting: () => void,
}

type Props = IProps & IPropsDispatch;

export class InterfacesAreFun extends React.Component<Props, never> {
  render() {
    return <span>The old world: IProps: {this.props.greeting}</span>
  }
}

//omitting the Redux binding code
```

> このように、インターフェースには "I "という接頭辞がありますが、型にはありません。しかし、結局のところ、「型」と「インターフェース」は本当に同じように使うことができ、区別することは完全に無駄になってしまいます。要は、コード上では、インターフェイスかどうかは気にせず、型（「型」というキーワードではなく、「型」という一般的な概念）であることを気にすればいいのです。

- ここで`interface IProps`になっているやつは両方`type Props`になるべきでは？
- なぜ`type`または`interface`に統一するべきなのか？それは同じ書き方ができるからと言って使用用途に応じた使い分けができていないだけでは？
