# Buscar una palabra dentro de un PDF
## PowerShell 
### URL: https://www.jesusninoc.com/2016/02/18/buscar-una-palabra-dentro-de-un-pdf/
```PowerShell
#Download https://sourceforge.net/projects/itextsharp/
#Set paths: iTextSharp, PDF
$iTextSharpFilePath = "D:\power\pdf\pdf\PowerShell.PDF\itextsharp.dll"
$pdfFilePath = "D:\power\pdf\pdf\ejem"

#Load iTextSharp
[System.Reflection.Assembly]::LoadFrom($iTextSharpFilePath)

#PDF example
$reader = New-Object iTextSharp.text.pdf.pdfreader -ArgumentList "$pdfFilePath\pdf.pdf"

Start-Sleep -Seconds 2

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
($line | Select-String "Security").Line
}
}

```
