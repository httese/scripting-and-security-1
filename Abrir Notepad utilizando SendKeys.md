# Abrir Notepad utilizando SendKeys
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2016/01/21/abrir-notepad-utilizando-sendkeys/
```PowerShell
#Abrir PowerShell y escribir:
[System.Windows.Forms.SendKeys]::SendWait("^({ESC})")
[System.Windows.Forms.SendKeys]::SendWait("EJECUTAR")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")
Start-Sleep -Seconds 2
[System.Windows.Forms.SendKeys]::SendWait("notepad.exe")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

```
