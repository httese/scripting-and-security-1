# Windows startup programs
## PowerShell 
### URL: https://www.jesusninoc.com/2016/06/01/windows-startup-programs/
```PowerShell
wmic startup list full | Select-String Command,Location

```
