# Insert image into a PDF
## PowerShell 
### URL: https://www.jesusninoc.com/2015/08/04/insert-image-into-a-pdf/
```PowerShell
[System.Reflection.Assembly]::LoadFrom(“F:\power\PowerShell.PDF\itextsharp.dll”)

$document=New-Object itextsharp.text.document
$stream=[IO.File]::OpenWrite(“F:\power\output.pdf”)
[itextsharp.text.pdf.PdfWriter]::GetInstance($document, $stream)

$document.Open()

$document.Add([iTextSharp.text.Image]::GetInstance('F:\power\captura.bmp'));

$document.Close()
$stream.Close()

```
