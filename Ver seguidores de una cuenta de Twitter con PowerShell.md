# Ver seguidores de una cuenta de Twitter con PowerShell
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/06/25/ver-seguidores-de-una-cuenta-de-twitter-con-powershell/
```PowerShell
$url="https://mobile.twitter.com/Microsoft/followers"
$result = Invoke-WebRequest $url
$result.AllElements | Where class -eq “user-item” | %{$_.innerText}

```
