# Obtener las descripciones de los resultados de una búsqueda en Bing
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/01/10/obtener-las-descripciones-de-los-resultados-de-una-busqueda-en-bing/
```PowerShell
$url='https://www.bing.com/search?q=powershell'
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “b_caption” | %{$_.innerText}

```
