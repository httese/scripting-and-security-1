# Obtener cuentas relacionadas con una cuenta de Twitter
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2015/12/29/obtener-cuentas-relacionadas-con-una-cuenta-de-twitter/
```PowerShell
#Apartado "También te puede gustar"
$idcuenta='15670515'
$ur='https://twitter.com/i/related_users/'+$idcuenta
$result=(Invoke-WebRequest -Uri $ur)
$conv=$result.Content
$convi=$conv | ConvertFrom-JSON
$convi.related_users_html

```
