# Simular la transmisión de vídeo entre un cliente y un servidor (streaming)
## Graphics, Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2016/03/12/simular-la-transmision-de-video-entre-un-cliente-y-un-servidor-streaming/
```PowerShell
D:\program\ffmpeg\bin\ffmpeg.exe -i D:\power\video\thesmash.mp4 -f image2 -pix_fmt bgr8 D:\power\video\capturas2\%01d.bmp

```
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

ls F:\power\video\captura\ | %{send-msg($_.FullName)}

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
[System.IO.File]::WriteAllBytes('F:\power\video\capturas2\'+$contador+'.bmp', $filebytes)

$reader.Dispose()
$stream.Dispose()
$client.Dispose()

} while (1)

```
```PowerShell
D:\program\ffmpeg\bin\ffmpeg.exe -i D:\power\video\capturas3\%01d.bmp -r 10 D:\power\video\thesmash23.mp4

```
