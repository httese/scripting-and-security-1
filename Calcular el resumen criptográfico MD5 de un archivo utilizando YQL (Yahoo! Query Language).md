# Calcular el resumen criptográfico MD5 de un archivo utilizando YQL (Yahoo! Query Language)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/06/13/calcular-el-resumen-criptografico-md5-de-un-archivo-utilizando-yql-yahoo-query-language/
```PowerShell
$urls='https://query.yahooapis.com/v1/public/yql?q=SELECT%20*%20FROM%20filemd5.hash%20WHERE%20url%3D%22http%3A%2F%2Fwww.yahoo.com%2Ffavicon.ico%22&format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys&callback='
$result=(Invoke-WebRequest -Uri $urls)
$conv=$result.Content
$convi = $conv | ConvertFrom-JSON
$convi.query.results.map.entry

```
