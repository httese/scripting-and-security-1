# Descargar todos los documentos PDF del BORME (Boletín Oficial del Registro Mercantil) de un día en concreto
## PHP, PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/01/08/descargar-todos-los-documentos-pdf-del-borme-boletin-oficial-del-registro-mercantil-de-un-dia-en-concreto/
```PowerShell
$urlboe='https://www.boe.es/borme/dias/2016/01/07/index.php?s=c'
foreach($pdfboe in (((Invoke-WebRequest $urlboe).AllElements).where{$_.href -match "BORME-A-"}))
{
Start-Sleep -Seconds 5
$origen='https://www.boe.es/'+$pdfboe.href
$destino='D:\power\pdf\pdf\boe\'+$pdfboe.tittle
Start-BitsTransfer -Source $origen -Destination $destino
}

```
