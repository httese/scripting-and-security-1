# Tecnologías que hay detrás de un sitio web
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/07/17/tecnologias-que-hay-detras-de-un-sitio-web/
```PowerShell
$url="https://builtwith.com/jesusninoc.com"
$result = Invoke-WebRequest $url
$result.AllElements | Where class -eq “techItem” | %{$_.innerText}

```
