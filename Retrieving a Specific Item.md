# Retrieving a Specific Item
## Filesystem, PowerShell, Registry 
### URL: https://www.jesusninoc.com/2014/12/18/retrieving-specific-item/
```PowerShell
$(Get-Item c:\scripts).lastaccesstime

```
```PowerShell
$(Get-Item hkcu:\software).subkeycount

```
```PowerShell
Get-Item hkcu:\software | Get-Member

```
