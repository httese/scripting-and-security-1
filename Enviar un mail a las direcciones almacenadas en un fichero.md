# Enviar un mail a las direcciones almacenadas en un fichero
## PowerShell 
### URL: https://www.jesusninoc.com/2016/08/30/enviar-un-mail-a-las-direcciones-almacenadas-en-un-fichero/
```PowerShell
#El fichero mails.txt contiene direcciones de correo
gc D:\mails.txt | % {
$componer="Contenido de prueba"
Send-MailMessage -to "mail2@example.com" -from “mail@example.com” -subject "Correo de prueba" -SmtpServer localhost -Body $componer
}

```
