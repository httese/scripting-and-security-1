# Estimación del porcentaje de la carga de la batería restante
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2016/06/16/estimacion-del-porcentaje-de-la-carga-de-la-bateria-restante/
```PowerShell
(Get-WmiObject Win32_Battery).EstimatedChargeRemaining

```
