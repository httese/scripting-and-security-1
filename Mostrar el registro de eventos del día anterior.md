# Mostrar el registro de eventos del día anterior
## Logs, PowerShell 
### URL: https://www.jesusninoc.com/2015/12/19/mostrar-el-registro-de-eventos-del-dia-anterior/
```PowerShell
Get-EventLog -LogName System -EntryType Error, Warning -After (Get-Date).AddDays(-1)

```
