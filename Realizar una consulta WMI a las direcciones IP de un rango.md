# Realizar una consulta WMI a las direcciones IP de un rango
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/08/19/realizar-una-consulta-wmi-a-las-direcciones-ip-de-un-rango/
```PowerShell
1..254 | %{
Get-WmiObject -Class Win32_BIOS -ComputerName ('192.168.1.'+$_)
}

```
