# Enviar un mail con las últimas entradas publicadas en una web
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2016/06/26/enviar-un-mail-con-las-ultimas-entradas-publicadas-en-una-web/
```PowerShell
$rss='https://www.jesusninoc.com/feed/'
$url='https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20rss%20where%20url%3D%22' + $rss + '%22&format=json&diagnostics=true&callback='
((Invoke-WebRequest -Uri $url).Content | ConvertFrom-JSON) | %{
    $titulo=$_.query.results.item.title
    $link=$_.query.results.item.link
    $componer=$titulo+$link+$componer
}
Send-MailMessage -to "mail2@example.com" -from “mail@example.com” -subject "Nuevos posts" -SmtpServer localhost -Body $componer

```
