# Mostrar los procesos que se están ejecutando en relación con los servicios
## PowerShell, Processes, Services 
### URL: https://www.jesusninoc.com/2015/10/24/mostrar-los-procesos-que-se-estan-ejecutando-en-relacion-con-los-servicios/
```PowerShell
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name
}

```
