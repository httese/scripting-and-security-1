# Utilizar credenciales almacenados
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/08/17/utilizar-credenciales-almacenados/
```PowerShell
$credenciales=Import-Clixml -Path credenciales.xml
#Utilizar credenciales en otro equipo remoto
Get-WmiObject -Class Win32_BIOS -ComputerName 192.168.1.2 -Credential $credenciales

```
