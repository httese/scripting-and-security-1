# Automatizar el inicio de sesión en Facebook
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2015/01/13/automatizar-el-inicio-de-sesion-en-facebook/
```PowerShell
#ES POSIBLE QUE NO FUNCIONE EN NUEVAS VERSIONES DE INTERNET EXPLORER
#Para que funcione correctamente es necesario realizar los pasos que aparecen en el siguiente post "El método getElementById() del objeto InternetExplorer.Application no funciona correctamente en IE11‏"
#https://www.jesusninoc.com/2015/01/12/el-metodo-getelementbyid-del-objeto-internetexplorer-application-no-funciona-correctamente-en-ie/

$IE= new-object -com InternetExplorer.Application
$IE.navigate2(“https://www.facebook.es”)

while ($IE.busy) {
sleep -milliseconds 100
}

$IE.visible=$true
$IE.Document.getElementById(“email”).value=”email@example.com”
$IE.Document.getElementByID("Pass").value="pass"

$IE.visible=$false
$IE.visible=$true

while ($IE.busy) {
sleep -milliseconds 1000
}

$IE.Document.getElementById(“loginbutton”).clic()

```
