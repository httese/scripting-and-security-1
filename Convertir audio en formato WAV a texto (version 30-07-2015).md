# Convertir audio en formato WAV a texto (version 30-07-2015)
## Multimedia, PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2015/07/30/convertir-audio-en-formato-wav-a-texto-version-30-07-2015/
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
