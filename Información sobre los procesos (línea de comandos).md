# Información sobre los procesos (línea de comandos)
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2016/04/14/informacion-sobre-los-procesos-linea-de-comandos/
```PowerShell
(Get-WmiObject win32_process) | Select-Object Name,CommandLine

```
