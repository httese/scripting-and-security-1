# Capture a single image from a webcam and transfer image between server and client (Sockets TCP)
## Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/07/18/capture-a-single-image-from-a-webcam-and-transfer-image-between-server-and-client-sockets-tcp/
```PowerShell
##Server
$port=2050
$IPEndPoint=New-Object System.Net.IPEndPoint([IPAddress]::Any,$port)
$TcpListener=New-Object System.Net.Sockets.TcpListener $IPEndPoint
$TcpListener.Start()

$AcceptTcpClient=$TcpListener.AcceptTcpClient()
$GetStream=$AcceptTcpClient.GetStream()
$StreamReader=New-Object System.IO.StreamReader $GetStream

$ReadAllLines = $StreamReader.ReadToEnd()
$Bytes = ([system.Text.Encoding]::Default).GetBytes($ReadAllLines)
[System.IO.File]::WriteAllBytes('F:\power\screenshotcopy.bmp',$Bytes)

$StreamReader.Dispose()
$GetStream.Dispose()
$AcceptTcpClient.Dispose()
$TcpListener.Stop()

```
```PowerShell
##Client
$port=2050
$TcpClient=New-Object System.Net.Sockets.TcpClient([IPAddress]::Loopback, $port)
$GetStream = $TcpClient.GetStream()
$StreamWriter = New-Object System.IO.StreamWriter $GetStream

$path=’F:\power\capture.bmp’
#Download CommandCam https://www.jesusninoc.com/2015/06/21/commandcam/
F:\power\CommandCam.exe /filename $path

$Bytes = [System.IO.File]::ReadAllBytes($path)
$StreamWriter.Write($Bytes,0,$Bytes.length)

$StreamWriter.Dispose()
$GetStream.Dispose()
$TcpClient.Dispose()

```
