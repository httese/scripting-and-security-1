# List all IP addresses and Host Names connected to your Server
## Network, PowerShell, Servers 
### URL: https://www.jesusninoc.com/2014/10/10/list-all-ip-addresses-and-host-names-connected-to-your-server/
```PowerShell
(((@(Get-NetTCPConnection).RemoteAddress | % {if($_ -notcontains (Get-NetIPAddress).IPv4Address -and ($_ -notcontains "::") -and ($_ -notcontains "0.0.0.0")){$_}}) | Group-Object).name) | % {$_,[System.Net.Dns]::GetHostbyAddress($_).HostName}

```
