# Buscar procesos que se están ejecutando
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2015/10/06/buscar-procesos-que-se-estan-ejecutando/
```PowerShell
(Get-Process).Where{$_.Name -like "chrome"}

```
