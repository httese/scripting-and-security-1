# Activar y poner en primer plano una aplicación que se está ejecutando
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2016/02/18/activar-y-poner-en-primer-plano-una-aplicacion-que-se-esta-ejecutando/
```PowerShell
$Script=New-Object -ComObject WScript.Shell
$Proceso=(Get-Process notepad).MainWindowTitle
$Script.AppActivate($Proceso)

```
