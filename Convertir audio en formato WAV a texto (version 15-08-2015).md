# Convertir audio en formato WAV a texto (version 15-08-2015)
## Multimedia, PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2015/08/15/convertir-audio-en-formato-wav-a-texto-version-15-08-2015/
```PowerShell
#Partir un fichero WAV en partes, después abrir cada uno de los ficheros WAV y convertirlos a texto

[void][reflection.assembly]::LoadWithPartialName(‘system.speech’)

#Partir un fichero WAV dividiendo por segundos y almacenarlo en una ruta
$ficherooriginal='F:\power\sonido\original.wav'

$rutaficherospartidos='F:\power\sonido\partido\'
$ficherodestino='ficheropartidoN.wav'
$ficherocompletodestino=$rutaficherospartidos+$ficherodestino

#Dividir el fichero WAV en partes de 5 minutos
F:\power\sonido\sox-14.4.2\sox.exe $ficherooriginal $ficherocompletodestino trim 0 300 : newfile : restart

#Para cada uno de los ficheros partidos, convertir a texto el contenido del audio
ls $rutaficherospartidos -Filter *.wav | %{
$_.name
$rec = New-Object ‘System.Speech.Recognition.SpeechRecognitionEngine’
$rec.LoadGrammar((New-Object ‘System.Speech.Recognition.DictationGrammar’))
$rec.SetInputToWaveFile($_.FullName)
[String]$almacenarcadena=''
[String]$cadenaconvert=''

do
{
$cadena=$rec.Recognize().Text
$cadenaconvert=[String]$cadena.ToString()
$almacenarcadena=$almacenarcadena+$cadenaconvert
}while($rec.AudioFormat)

#Almacenar el número del minuto que se procesa junto con el texto convertido
#El número del minuto depende del tiempo que dure cada fichero partido, en este caso 5 minutos
[Int]($_.Name.Replace('.wav','').Split('N')[1])*5 | Out-File $rutaficherospartidos\wavtext.txt -Append
$almacenarcadena | Out-File $rutaficherospartidos\wavtext.txt -Append
}

```
