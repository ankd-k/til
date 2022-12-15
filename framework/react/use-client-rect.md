# useClientRect

## TL;DR

基本的に`useEffect()`でイベントの登録とかはする。

## useClientRect is 何

[How can I measure a DOM node](https://ja.reactjs.org/docs/hooks-faq.html#how-can-i-measure-a-dom-node)  

refでDOMを保持してそのRectを返すHooks。  

```js
function MeasureExample() {
  const [rect, ref] = useClientRect();
  return (
    <>
      <h1 ref={ref}>Hello, world</h1>
      {rect !== null &&
        <h2>The above header is {Math.round(rect.height)}px tall</h2>
      }
    </>
  );
}

function useClientRect() {
  const [rect, setRect] = useState(null);
  const ref = useCallback(node => {
    if (node !== null) {
      setRect(node.getBoundingClientRect());
    }
  }, []);
  return [rect, ref];
}
```

## 問題点・改善

ただしこれそのままだとウィンドウリサイズ時に更新されないためバグることがある（実際某案件の実装中にバグった）。

なのでこれをウィンドウリサイズ時またはDOMリサイズ時に更新するためにイベント登録したい。

イベント登録は登録と削除をセットで定義すべき。だけどuseCallback単体では削除処理を書くところがわからん。

なので中でdom再描画時にイベントハンドラの更新、それに応じたuseEffectを書いてイベント登録・削除をする。

```js
function useClientRect() {
  const [rect, setRect] = useState(null);
  const [node, setNode] = useState(null);

  const handleResize = useCallback(() => {
    if (node !== null) {
      setRect(node.getBoundingClientRect());
    }
  }, [node]);

  const ref = useCallback(node => {
    if (node !== null) {
      setNode(node);
      setRect(node.getBoundingClientRect());// 初回時実行
      // handleResize(); // ←この実行時点ではまだnodeに要素が入っていないため動かない。✕。
    }
  }, []);

  useEffect(() => {
    window.addEventListener('resize', handleResize);
    return () => {
      window.removeEventListener('resize', handleResize);
    }
  }, [handleResize]);

  return [rect, ref];
}
```
