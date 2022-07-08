# isColor()

文字列が色として使用できるかを判定する関数。  
適当なスタイルに突っ込んでそこから色を取得した時に値を得られるかどうかで判定する。  

```javascript
const isColor = (strColor) => {
  const s = new Option().style;
  s.color = strColor;
  return s.color !== '';
}
```
