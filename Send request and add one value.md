# Send request and add one value
## PHP, PowerShell, Security 
### URL: https://www.jesusninoc.com/2014/02/26/send-request-and-add-one-value/
```PowerShell
(Invoke-WebRequest "https://www.example.net/redirect.php?id_publicacion=988&url=www.prueb.as&pais_mas=10").statuscode
#Add one value
((Invoke-WebRequest "https://www.example.net/visitados.php").AllElements | Where Class -eq "listado_gde" | Select -ExpandProperty innerText)[0]

```
