# PowerShellプロファイルの編集方法

プロファイルのフルパスは`$PROFILE`で取得可能。  

> 自動 $PROFILE 変数には、現在のセッションで使用できる PowerShell プロファイルへのパスが格納されます。

`.`でつなげて対象のユーザー・ホストを指定できる。

```powershell
# 例
$PROFILE # 現在のユーザー、現在のホスト
$PROFILE.AllUsersAllHosts # すべてのユーザー、すべてのホスト
```

プロファイルを編集するには、↑のパスにあるファイルを編集すればよい。

```powershell
code $PROFILE # vscodeでプロファイルを開く
```

各OSでの実ファイルの場所も公式Docsに載っているので必要があれば確認できる。  
[the-profile-files](https://docs.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2#the-profile-files)  

## ref

- [about_Profiles - Microsoft PowerShell ドキュメント](https://docs.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2)
