# Hora y fecha del último arranque
## PowerShell 
### URL: https://www.jesusninoc.com/2016/06/05/hora-y-fecha-del-ultimo-arranque/
```PowerShell
(Get-CimInstance -ClassName Win32_OperatingSystem).LastBootUpTime

```
