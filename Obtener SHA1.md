# Obtener SHA1
## Cryptography, PowerShell, Security, Web 
### URL: https://www.jesusninoc.com/2015/10/23/obtener-sha1/
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")
[System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile("Hola", "SHA1")
[System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile("hola", "SHA1")

```
