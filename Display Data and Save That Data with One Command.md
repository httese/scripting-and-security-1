# Display Data and Save That Data with One Command
## Filesystem, PowerShell, Strings 
### URL: https://www.jesusninoc.com/2014/11/07/display-data-save-data-one-command/
```PowerShell
Get-Process | Tee-Object -file c:\scripts\test.txt

```
