# Send the cursor’s position between client and server (Sockets UDP)
## Network, PowerShell, Security, Servers 
### URL: https://www.jesusninoc.com/2015/07/06/send-the-cursors-position-between-client-and-server-sockets-udp/
```PowerShell
##Server
while(1)
{
$port=2040
$IPEndPoint=New-Object System.Net.IPEndPoint([IPAddress]::Any,$port)

$UdpClient=New-Object System.Net.Sockets.UdpClient $port

#Receive position x,y
$positions=[Text.Encoding]::ASCII.GetString($UdpClient.Receive([ref]$IPEndPoint))
$positions

#Set cursor's position
$x=[Int]$positions.Split(',')[0]
$y=[Int]$positions.Split(',')[1]+100
[System.Windows.Forms.Cursor]::Position=New-Object System.Drawing.Point($x,$y)

$UdpClient.close()
}

```
```PowerShell
##Client
$port=2040
$IPEndPoint=new-object System.Net.IPEndPoint([IPAddress]::Loopback,$port)

#Position x,y
$x=([System.Windows.Forms.Cursor]::Position).x
$y=([System.Windows.Forms.Cursor]::Position).y
$positions=[Text.Encoding]::ASCII.GetBytes($x.ToString()+','+$y.ToString())

#Send position x,y
$UdpClient=New-Object System.Net.Sockets.UdpClient
$UdpClient.Send($positions,$positions.Length,$IPEndPoint)
$UdpClient.Close()

```
