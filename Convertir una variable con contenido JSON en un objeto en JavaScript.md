# Convertir una variable con contenido JSON en un objeto en JavaScript
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2016/03/30/convertir-una-variable-con-contenido-json-en-un-objeto-en-javascript/
```PowerShell
$ie = New-Object -com "InternetExplorer.Application"
$ie.Navigate("about:blank")
$ie.visible = $true

$ie.document.write("
<p id=""mostrar""></p>
<script>
var contenidojson = '{""usuario"":[' +
'{""nombre"":""Pepe""},' + '{""nombre"":""Juan""}]}';
objeto = JSON.parse(contenidojson);
document.getElementById(""mostrar"").innerHTML = objeto.usuario[0].nombre + "" "" + objeto.usuario[1].nombre;
</script>
") 
$ie.document.getElementById("mostrar").innerHTML

```
