# Screen position
## PowerShell 
### URL: https://www.jesusninoc.com/2012/12/29/screen-position/
```PowerShell
for ()
{
Start-Sleep -m 500
$dY = ([System.Windows.Forms.Cursor]::Position.Y) #Y coordinates
$dX = ([System.Windows.Forms.Cursor]::Position.X) #X coordinates
Write-Host $dX,$dY #print
}

```
