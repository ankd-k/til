# 全てのマージ済みブランチを削除する

ref: [Qiita - Gitでマージ済みブランチを一括削除](https://qiita.com/hajimeni/items/73d2155fc59e152630c4)  

```bash
git branch --merged|egrep -v '\*|develop|main'|xargs git branch -d
```

↑はunixコマンドなのでPowerShellだと動かない。  
ならPowerShellのコマンドに置き換えよう↓  

```powershell
git branch --merged | Select-String -Pattern "hoge" -NotMatch |  % { "$_".Trim() } | %{ git branch -d $_ } 
```

1. `git branch --merged`  
マージ済みブランチ一覧を取得する。
2. `Select-String -Pattern "hoge" -NotMatch`  
一覧からhogeを含むものを除外。残したいブランチを文字列部分に突っ込む。  
本当はここでもう少し正規表現とか使って楽するべき。
3. `%{ "$_".Trim() }`  
`%{}`はForEach-Objectのエイリアスみたいなもの。リストの各要素に対して{}内のスクリプトを実行する。各要素は`$_`に入る。  
1で取得した文字列は頭に空白が入っているので, "$_"で文字列型にしてTrim()で前後のスペースを消す。  
現在のブランチに入る`*`など、スペース以外の記号が入ることは考慮しない。  
4. `%{ git branch -d $_ }`  
一覧の各文字列に対して`git branch -d branch_name`を実行する。  
