# SVG要素をjsから追加する

追加するメソッド自体は同じ`appendChild()`でいいが、要素の作り方が異なる。
他のDOMと同じ様に作ると表示されない。  
要素の見た目自体は同じなので気づきにくい。  

```js
// incorrect
const el = document.createElement("rect");
// correct
const el = document.createElementNS("http://www.w3.org/2000/svg","rect");
```

ref: https://little-strange.hatenablog.com/entry/2021/03/06/201143
