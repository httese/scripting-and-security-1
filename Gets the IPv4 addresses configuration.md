# Gets the IPv4 addresses configuration
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/05/05/gets-the-ipv4-addresses-configuration/
```PowerShell
Get-NetIPAddress | Where-Object AddressFamily -EQ IPv4 | Select-Object IPAddress

```
