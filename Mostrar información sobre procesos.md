# Mostrar información sobre procesos
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2016/02/28/mostrar-informacion-sobre-procesos/
```PowerShell
#Name
#CPUSeconds
#WorkingSetMB
#TotalProcessorTime
#Description
Get-Process | ? {$_.TotalProcessorTime -ne $Null} | Select-Object -Property Name, @{Name="CPUSeconds"; Expression = {($_.CPU)}},@{Name="WorkingSetMB"; Expression = {($_.WorkingSet / 1mb)}},TotalProcessorTime, Description

```
