# Realizar miniaturas de los últimos dominios indexados
## Graphics, PowerShell, Servers, Web scraping 
### URL: https://www.jesusninoc.com/2016/02/24/realizar-miniaturas-de-los-ultimos-dominios-indexados/
```PowerShell
#It doesn't work
(((Invoke-WebRequest 'https://es.wsdata.co/2016-02-23/domains-list.html').AllElements).where{$_.class -eq "responsive"}).innerHTML -split '[\r\n]' |%{
if($_ -match 'href')
{
Start-Sleep -Seconds 5
$Domain=$_ -replace "<.*?>"
Start-Process chrome $Domain

$Path=’D:\power\dominios\'+$Domain.replace('.','')+'.bmp’
$Path
$Bitmap=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
$Graphics=[System.Drawing.Graphics]::FromImage($Bitmap)
$Graphics.CopyFromScreen((New-Object System.Drawing.Point(0,0)), (New-Object System.Drawing.Point(0,0)), $Bitmap.Size)
$Graphics.Dispose()
$Bitmap.Save($Path,'Bmp')
$Bitmap.Dispose()

$BitmapT = [System.Drawing.Image]::FromFile($Path)
$Thumbnail = $BitmapT.GetThumbnailImage(200, 200, $null, [intptr]::Zero)
$Thumbnail.Save($Path+".thumbnail.jpg" )
$BitmapT.Dispose()
$Thumbnail.Dispose()
}
}

```
