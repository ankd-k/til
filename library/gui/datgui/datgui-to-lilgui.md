# dat.gui -> lil.gui

dat.guiはメンテナンスされずlil.guiに移行しているらしい。

[dat.guiはlil-guiに移行中です](https://qiita.com/masato_makino/items/1e66b7e6b5bb69865ff4#:~:text=lil%2Dgui%E3%81%AFthree.js,%E3%81%AB%E6%8E%A1%E7%94%A8%E3%81%95%E3%82%8C%E3%81%BE%E3%81%97%E3%81%9F%E3%80%82)

Three.jsのサンプルも移行しているとのこと。

インポート文を書き換えるだけで移行できるらしい。

```diff
- import * as dat from 'dat.gui';
- const gui = new dat.GUI();

+ import GUI from "lil.gui"
+ const gui = new GUI();
```
