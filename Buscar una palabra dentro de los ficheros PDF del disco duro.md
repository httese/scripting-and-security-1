# Buscar una palabra dentro de los ficheros PDF del disco duro
## PowerShell 
### URL: https://www.jesusninoc.com/2016/02/19/buscar-una-palabra-dentro-de-los-ficheros-pdf-del-disco-duro/
```PowerShell
#Download https://sourceforge.net/projects/itextsharp/
#Set paths: iTextSharp, PDF
$iTextSharpFilePath = "D:\power\pdf\pdf\PowerShell.PDF\itextsharp.dll"
$pdfFilePath = "D:\"

#Load iTextSharp
[System.Reflection.Assembly]::LoadFrom($iTextSharpFilePath)

#List PDF
ls $pdfFilePath *.pdf -Recurse | %{

$_.FullName

Start-Sleep -Seconds 2

$reader = New-Object iTextSharp.text.pdf.pdfreader -ArgumentList $_.FullName

for ($page = 1; $page -le $reader.NumberOfPages; $page++)
{
$lines = [char[]]$reader.GetPageContent($page) -join "" -split "`n"
foreach ($line in $lines)
{
if ($line -match "^\[")
{
$line=$line -replace "\\([\S])", $matches[1]
$line=$line -replace "^\[\(|\)\]TJ$", "" -split "\)\-?\d+\.?\d*\(" -join ""
}
else
{
}
($line | Select-String "Secret").Line
}
}
}

```
