# Realizar ping a las direcciones IP de un rango
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/08/18/realizar-ping-a-las-direcciones-ip-de-un-rango/
```PowerShell
1..254 | %{Test-Connection ('192.168.1.'+$_)}

```
