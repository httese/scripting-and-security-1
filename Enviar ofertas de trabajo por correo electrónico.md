# Enviar ofertas de trabajo por correo electrónico
## Automation, PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2015/11/15/enviar-ofertas-de-trabajo-por-correo-electronico/
```PowerShell
#Crear ArrayList para almacenar la fecha de publicación de la oferta y el nombre de la oferta
[System.Collections.ArrayList] $arraylistm = New-Object System.Collections.ArrayList
[System.Collections.ArrayList] $arrayliste = New-Object System.Collections.ArrayList

#Petición a la web que tiene las ofertas
$Resultado=Invoke-WebRequest ‘https://www.infojobs.net/ofertas-trabajo’
$Resultado.AllElements | %{
#Almacenar la fecha de la oferta y el nombre de la oferta
$Minuto=($_ | Where-Object Class -eq ‘marked’).innerText
$Empleo=($_ | Where-Object Class -eq ‘job-list-title’).innerText
if($Minuto){[void]$arraylistm.Add($Minuto)}
if($Empleo){[void]$arrayliste.Add($Empleo)}
}

$Enviar=""
#Recorrer la oferta por fecha de publicación y mostrar la oferta que tenga la fecha de publicación menor que 10 minutos
0..$arraylistm.Count | %{
[String]$MinutosContados=$arraylistm[$_+1]
#Sustituir las comillas (“”)
$MinutosContados=$MinutosContados.replace("Hace","").replace("m","").Replace("h","60")
if([Int]$MinutosContados -lt 10 -and !$MinutosContados.Contains(‘h’)){
$Enviar+=$MinutosContados,$arrayliste[$_],"`n"
}
}

#Utilizar un servidor SMTP por ejemplo https://www.jesusninoc.com/2015/01/12/instalar-hmailserver-imap-smtp-y-pop3/
Send-MailMessage -to "mail2@example.com" -from “mail@example.com” -subject “Ofertas de trabajo” -SmtpServer localhost -Body $Enviar

```
