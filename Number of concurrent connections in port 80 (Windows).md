# Number of concurrent connections in port 80 (Windows)
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2014/12/06/number-concurrent-connections-port-80/
```PowerShell
netstat -ano | Where-Object {$_ -match ":80" -and $_ -match "ESTABLISHED"} | Measure-Object

```
```PowerShell
netstat -ano | Select-String ":80" | Select-String "ESTABLISHED" | Measure-Object

```
```PowerShell
netsh interface ipv4 show tcpconnections | Select-String "80" | Select-String "Establecido" | Measure-Object

```
