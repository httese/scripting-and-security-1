# Abrir una página web en Internet Explorer utilizando SendKeys
## Automation, PowerShell, Web 
### URL: https://www.jesusninoc.com/2016/03/29/abrir-una-pagina-web-en-internet-explorer-utilizando-sendkeys/
```PowerShell
#Abrir PowerShell
[System.Windows.Forms.SendKeys]::SendWait("^({ESC})")
[System.Windows.Forms.SendKeys]::SendWait("EJECUTAR")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")
Start-Sleep -Seconds 2
[System.Windows.Forms.SendKeys]::SendWait("iexplore www.jesusninoc.com")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

```
