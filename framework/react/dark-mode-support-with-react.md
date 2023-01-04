# ダークモード対応

## 最終ゴール

「ダークモード対応」のゴールはざっと考えて３通り。

1. OS の設定依存 ... OS 側で指定されているテーマの通りの配色にする。
2. 好みの配色を選ぶ ... プリセットがいくつかある場合など、ユーザーが自由に選べるようにする。
3. 両方組み合わせる ... デフォルトは OS の設定、選択したらそちらを優先して切り替えるとか。

結局スタイルの話なので、最終的に何らかの方法で CSS を切り替えられれば OK。

---

## 前提知識

### OS の設定に応じてスタイルを変える

[`prefes-color-scheme`](https://developer.mozilla.org/ja/docs/Web/CSS/@media/prefers-color-scheme)クエリを使う。

```html
<!-- HTML -->
<div class="day">Day (initial)</div>
<div class="day light-scheme">Day (changes in light scheme)</div>
<div class="day dark-scheme">Day (changes in dark scheme)</div>
<br />

<div class="night">Night (initial)</div>
<div class="night light-scheme">Night (changes in light scheme)</div>
<div class="night dark-scheme">Night (changes in dark scheme)</div>
```

```css
/* CSS */
.day {
  background: #eee;
  color: black;
}
.night {
  background: #333;
  color: white;
}

@media (prefers-color-scheme: dark) {
  .day.dark-scheme {
    background: #333;
    color: white;
  }
  .night.dark-scheme {
    background: black;
    color: #ddd;
  }
}

@media (prefers-color-scheme: light) {
  .day.light-scheme {
    background: white;
    color: #555;
  }
  .night.light-scheme {
    background: #eee;
    color: black;
  }
}

.day,
.night {
  display: inline-block;
  padding: 1em;
  width: 7em;
  height: 2em;
  vertical-align: middle;
}
```

### クラスを当ててスタイルを変える

その名の通り。クリックした時に`.active`とかつけたり消したりするような感じ。

### JS から OS のカラーテーマを取得する

JS から`window.matchMedia('(prefers-color-scheme: dark)')`で OS のカラーテーマ状態を取得できる。  
イベントも登録できるので変更時に処理を走らせることもできる。

```js
const darkModeMediaQuery = window.matchMedia("(prefers-color-scheme: dark)");
const darkModeOn = darkModeMediaQuery.matches;

darkModeMediaQuery.addListener((e) => {
  const darkModeOn = e.matches;
});
```

---

## 対応方針

基本的にアプリの状態で持ち、OS 側の設定が切り替わったらその状態も切り替える。  
Cookie の登録・取得も忘れずに。

- ページ遷移時に Cookie から状態を取得、初期状態を設定。Cookie にない場合 OS の状態をデフォルトにする。
- 各種 UI でテーマを操作 → 状態を更新・Cookie に保存。

---

## 参考

- [Web のダークモードを実現するには - freee Developers Hub](https://developers.freee.co.jp/entry/dark-mode-web)
- [`prefes-color-scheme` - MDN](https://developer.mozilla.org/ja/docs/Web/CSS/@media/prefers-color-scheme)
- [【React】サイトにダークモード機能を実装する - ツクログネット](https://tsukulog.net/2021/06/15/react-dark-mode/)
- [Next.js で MUI と Recoil を用いたダークモードの実装 - Tech blog produced by FOURIER](https://www.fourier.jp/techblog/articles/dark-mode-with-nexthjs-mui-recoil-localstorage/)
