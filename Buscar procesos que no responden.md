# Buscar procesos que no responden
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2015/10/10/buscar-procesos-que-no-responden/
```PowerShell
(Get-Process).Where{-not $_.Responding}

```
