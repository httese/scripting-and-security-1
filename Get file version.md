# Get file version
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2015/03/13/get-file-version/
```PowerShell
(Get-ChildItem -Path $env:windir\system32 -Filter *.dll).VersionInfo

```
