# Mover el ratón a las posiciones que están guardadas en un fichero
## Automation, Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2015/03/01/mover-el-raton-a-las-posiciones-que-estan-guardadas-en-un-fichero/
```PowerShell
#Leer las posiciones que están en un fichero que previamente se han guardado
#https://www.jesusninoc.com/2015/01/26/save-screen-position/

Get-Content F:\power\p1.txt | %{
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($_.split(',')[0],$_.split(',')[1])
Start-Sleep -Milliseconds 5
$_}

```
