# Comprobar si se utiliza la batería o la corriente alterna
## PowerShell 
### URL: https://www.jesusninoc.com/2016/01/05/comprobar-si-se-utiliza-la-bateria-o-la-corriente-alterna/
```PowerShell
if((Get-WmiObject -Class Win32_Battery).BatteryStatus -eq 1){'Batería interna activada'}else{'Utilizando de corriente alterna'}

```
