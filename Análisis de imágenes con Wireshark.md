# Análisis de imágenes con Wireshark
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/03/14/analisis-de-imagenes-con-wireshark/
```PowerShell
function send-msg($file)
{
$client = New-Object System.Net.Sockets.TcpClient "localhost", 8982
$stream = $client.GetStream()
$writer = New-Object System.IO.StreamWriter $stream

$bytes = [System.IO.File]::ReadAllBytes($file)
#$writer.WriteLine($bytes)
$writer.Write($bytes,0,$bytes.length)
$writer.Dispose()
$stream.Dispose()
$client.Dispose()
}

#Enviar solo una imagen al servidor
ls d:\power\video\captura\ | Select-Object -First 1 | %{send-msg($_.FullName)}

```
```PowerShell
$endpoint = new-object System.Net.IPEndPoint ([system.net.ipaddress]::any, 8982)
$listener = new-object System.Net.Sockets.TcpListener $endpoint
$listener.start()
$contador=0
do {
$client = $listener.AcceptTcpClient()
$stream = $client.GetStream();

$reader = New-Object System.IO.StreamReader $stream

$lines=$reader.ReadToEnd()

$enc = [system.Text.Encoding]::Default
$filebytes = $enc.GetBytes($lines)

$contador=$contador+1
[System.IO.File]::WriteAllBytes('f:\power\video\capturas2\'+$contador+'.bmp', $filebytes)

$reader.Dispose()
$stream.Dispose()
$client.Dispose()

} while (1)

```
