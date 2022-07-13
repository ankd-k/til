# エイリアスを追加する

PowerShellのコマンドレットは基本的に長くてそのまま打つのが面倒。  
短く済ませるためにエイリアスが設定されているコマンドがある。

```powershell
cd hoge # cd = Set-Locationのエイリアス。
```

エイリアスは自分で追加することも可能。  
追加するにはプロセス実行毎にコマンドを打つか、そのコマンドを実行時に走るスクリプト＝プロファイルに追記する。  

```powershell
Set-Alias alias cmdlets # aliasという名前でcmdletsを実行する
```

プロファイルの追加方法は[こちら](./edit-profiles.md)を参照。

## ref

- [PowerShell使い方メモ#エイリアス - Qiita](https://qiita.com/opengl-8080/items/bb0f5e4f1c7ce045cc57#%E3%82%A8%E3%82%A4%E3%83%AA%E3%82%A2%E3%82%B9)
- [about_Profiles - Microsoft PowerShell ドキュメント](https://docs.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2)
