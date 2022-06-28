# volta pinがnot found packageで通らない

問題：`volta pin node`を実行してもnot foun packageエラーが表示される。  
パッケージ自体はインストールされている様子。

原因：以前wingetで入れたNodeが邪魔をしていただけ。  

解決策：↑を削除すると問題なく`volta pin node`が通った。