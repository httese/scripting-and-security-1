# Analizar resultados de búsqueda en Google y crear un gráfico de barras con los resultados
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2015/01/25/analizar-resultados-de-busqueda-en-google-y-crear-un-grafico-de-barras-con-los-resultados/
```PowerShell
#Más información sobre el gráfico
#https://google-developers.appspot.com/chart/interactive/docs/gallery/barchart#SimpleExample
#Google Charts provides a perfect way to visualize data on your website. From simple line charts to complex hierarchical tree maps, the chart gallery provides a large number of ready-to-use chart types.
#Muy importante escribir correctamente los caracteres " y '

#Inicio del gráfico
$inicio="<html><head><script type=""text/javascript"" src=""https://www.google.com/jsapi""></script><script type=""text/javascript"">google.load(""visualization"", ""1"", {packages:[""corechart""]});google.setOnLoadCallback(drawChart);function drawChart() {var data = google.visualization.arrayToDataTable([['Nombre', 'Valor'],"
$inicio | Out-File F:\power\grafico.html

#Leer nombres en un fichero para buscar en Google
Get-Content F:\power\nombres.txt | %{

#La primera búsqueda se realiza con el nombre que aparece en el fichero
$urls='https://www.google.com/search?q='+ $_ +''
$result=Invoke-WebRequest $urls
$valor=($result.AllElements | ? {$_.id -eq “resultStats”}).innerText
$valor=$valor.replace("Aproximadamente","")
$valor=$valor.replace("resultados","")
$valor=$valor.replace(".","")
$valor=$valor.Trim()
Write-Host $_
Write-Host $valor
"['$_', $valor]," | Out-File F:\power\grafico.html -Append

#La segunda búsqueda se realiza con el nombre que aparece en el fichero convertido a minúsculas
$lower=$_.tolower()
$urls='https://www.google.com/search?q='+ $lower +''
$result=Invoke-WebRequest $urls
$valor=($result.AllElements | ? {$_.id -eq “resultStats”}).innerText
$valor=$valor.replace("Aproximadamente","")
$valor=$valor.replace("resultados","")
$valor=$valor.replace(".","")
$valor=$valor.Trim()
Write-Host $lower
Write-Host $valor
"['$lower', $valor]," | Out-File F:\power\grafico.html -Append

#La tercera búsqueda se realiza con el nombre que aparece en el fichero convertido a mayúsculas
$upper=$_.ToUpper()
$urls='https://www.google.com/search?q='+ $upper +''
$result=Invoke-WebRequest $urls
$valor=($result.AllElements | ? {$_.id -eq “resultStats”}).innerText
$valor=$valor.replace("Aproximadamente","")
$valor=$valor.replace("resultados","")
$valor=$valor.replace(".","")
$valor=$valor.Trim()
Write-Host $upper
Write-Host $valor
"['$upper', $valor]," | Out-File F:\power\grafico.html -Append
}

#Final del gráfico
$fin="]);var options = {title: 'Valoracion de nombres',vAxis: {title: 'Nombre', titleTextStyle: {color: 'red'}}};var chart = new google.visualization.BarChart(document.getElementById('chart_div'));chart.draw(data, options);}</script></head><body><div id=""chart_div"" style=""width: 900px; height: 500px;""></div></body></html>"
$fin | Out-File F:\power\grafico.html -Append

```
