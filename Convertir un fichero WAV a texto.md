# Convertir un fichero WAV a texto
## Multimedia, PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2016/04/12/convertir-un-fichero-wav-a-texto/
```PowerShell
#Abrir un fichero WAV y convertir a texto el contenido
#En esta versión se lee el fichero WAV mientras que haya sonido por procesar, también se almacena el texto convertido en un fichero

[void][reflection.assembly]::loadwithpartialname(‘system.speech’)
$rec = New-Object ‘System.Speech.Recognition.SpeechRecognitionEngine’
$rec.LoadGrammar((New-Object ‘System.Speech.Recognition.DictationGrammar’))
$rec.SetInputToWaveFile('d:\holas.wav')

do
{
$rec.Recognize().Text | Out-File d:\wavtext.txt -Append
}while($rec.AudioFormat)

```
