# Obtener el número de resultados sobre búsquedas en Google Hacking Database (GHDB)
## PowerShell, Security, Web scraping 
### URL: https://www.jesusninoc.com/2015/12/06/obtener-el-numero-de-resultados-sobre-busquedas-en-google-hacking-database-ghdb/
```PowerShell
(Invoke-WebRequest 'https://www.exploit-db.com/google-hacking-database/').AllElements | %{$_.href | Select-String https://www.exploit-db.com/ghdb/} | %{
$buscar=((Invoke-WebRequest $_.tostring()).AllElements | Where class -eq “w-pagehead”).outerText
$buscar
$url='https://www.google.es/search?q='+$buscar
(Invoke-WebRequest $url).AllElements | Where Class -eq “sd” | %{$_.innerText}
Start-Sleep -Seconds 10
}

```
