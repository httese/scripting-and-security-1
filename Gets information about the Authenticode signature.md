# Gets information about the Authenticode signature
## PowerShell 
### URL: https://www.jesusninoc.com/2016/05/22/gets-information-about-the-authenticode-signature/
```PowerShell
Get-WmiObject -Class win32_systemdriver | % {Get-AuthenticodeSignature $_.pathname}

```
