# Convertir un cmdlet a Base64
## PowerShell 
### URL: https://www.jesusninoc.com/2016/09/23/convertir-un-cmdlet-a-base64/
```PowerShell
#Es necesario convertir con codificación Unicode
[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes('Get-Process'))

```
