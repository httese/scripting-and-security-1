# Ejecutar el comando “Ejecutar” utilizando SendKeys
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2015/11/09/ejecutar-el-comando-ejecutar-utilizando-sendkeys/
```PowerShell
#Abrir PowerShell
[System.Windows.Forms.SendKeys]::SendWait("^({ESC})")
[System.Windows.Forms.SendKeys]::SendWait("EJECUTAR")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

```
