# Get entries from the IPv6 neighbor cache
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/05/03/get-entries-from-the-ipv6-neighbor-cache/
```PowerShell
Get-NetNeighbor | Where-Object AddressFamily -EQ IPv6

```
