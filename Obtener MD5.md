# Obtener MD5
## Cryptography, PowerShell, Security, Web 
### URL: https://www.jesusninoc.com/2014/07/02/obtener-md5/
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")
[System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile("Hola", "MD5")
[System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile("hola", "MD5")

```
