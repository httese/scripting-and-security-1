# Dividir en dos partes una captura de pantalla
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2015/03/09/dividir-en-dos-partes-una-captura-de-pantalla/
```PowerShell
$path='F:\power\captura.png'
$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
$g=[System.Drawing.Graphics]::FromImage($b)
$g.CopyFromScreen((New-Object System.Drawing.Point(0,0)), (New-Object System.Drawing.Point(0,0)), $b.Size)
$g.Dispose()
$b.Save($path)

```
```PowerShell
$path='F:\power\capturap1.png'
$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
$g=[System.Drawing.Graphics]::FromImage($b)
$g.CopyFromScreen(0,0,0,$b.Size.Height/2, $b.Size)
$g.Dispose()
$b.Save($path)

```
```PowerShell
$path='F:\power\capturap2.png'
$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
$g=[System.Drawing.Graphics]::FromImage($b)
$g.CopyFromScreen(0,$b.Size.Height/2,0,0, $b.Size)
$g.Dispose()
$b.Save($path)

```
