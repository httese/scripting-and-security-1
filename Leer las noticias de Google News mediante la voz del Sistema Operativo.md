# Leer las noticias de Google News mediante la voz del Sistema Operativo
## Automation, Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2014/12/09/leer-las-noticias-de-google-news-mediante-la-voz-del-sistema-operativo/
```PowerShell
$sam = New-Object -comObject SAPI.SpVoice
[xml]$doc=Invoke-WebRequest 'https://news.google.es/news?pz=1&cf=all&ned=es&hl=es&output=rss'
$doc.rss.channel.Item | %{$sam.Speak($_.title)}

```
```PowerShell
$sam = New-Object -comObject SAPI.SpVoice
[xml]$doc = (New-Object System.Net.WebClient).DownloadString('https://news.google.es/news?pz=1&cf=all&ned=es&hl=es&output=rss')
$doc.rss.channel.Item | %{$sam.Speak($_.title)}

```
