# Abrir un documento utilizando una caja de diálogo
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2015/02/15/abrir-un-documento-utilizando-una-caja-de-dialogo/
```PowerShell
[reflection.assembly]::loadwithpartialname("System.Windows.Forms")
$openFile = New-Object System.Windows.Forms.OpenFileDialog
$openFile.Filter = 'txt files (*.txt)|*.txt|All files (*.*)|*.*'
If($openFile.ShowDialog() -eq "OK")
{
    Get-Content $openFile.FileName
}

```
