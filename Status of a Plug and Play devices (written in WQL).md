# Status of a Plug and Play devices (written in WQL)
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2015/11/18/status-of-a-plug-and-play-devices-written-in-wql/
```PowerShell
Get-WmiObject -query “select Name,Status from Win32_PnPEntity”

```
```PowerShell
Get-WmiObject -query “select * from Win32_PnPEntity” | Select-Object Name, Status

```
