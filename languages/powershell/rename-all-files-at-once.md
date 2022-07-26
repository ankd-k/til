# 複数ファイル一括リネーム

https://nyanblog2222.com/programming/2366/

```powershell
Get-ChildItem "C:\sample\in\*.jpg" | Rename-Item -NewName{$_.Name -Replace "\.jpg",".jpeg"}
```
