# 開発環境自動ビルドツール選定

[Choosing development tool](https://webpack.js.org/guides/development/#choosing-a-development-tool)  

## TD;SR

とりあえずwebpack-dev-server使っておけばおｋ

---

開発時の自動ビルドで使える方法は3つ。

1. `webpack --watch`
2. webpack-dev-server (`webpack serve`)
3. webpack-dev-middleware

1はコマンドだけだから一番簡単。ただしホットリロードがない。  
2が安定。  
3は2の内部で使っているやつ。  
