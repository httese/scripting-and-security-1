# Leer las noticias de Google News mediante la voz del Sistema Operativo y almacenarlo en un fichero de audio
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2014/12/13/leer-las-noticias-de-google-news-mediante-la-voz-del-sistema-operativo-y-almacenarlo-en-un-fichero-de-audio-system-speech/
```PowerShell
$Path = "F:\power\file.wav"

Add-Type -AssemblyName System.Speech

$synthesizer = New-Object -TypeName System.Speech.Synthesis.SpeechSynthesizer
$synthesizer.SetOutputToWaveFile($Path)
[xml]$doc=Invoke-WebRequest ‘https://news.google.es/news?pz=1&cf=all&ned=es&hl=es&output=rss’
$doc.rss.channel.Item | %{$synthesizer.Speak($_.title)}
$synthesizer.SetOutputToDefaultAudioDevice()

Invoke-Item $Path

```
