# Cómo ver las contraseñas de las conexiones inalámbricas
## Network, PowerShell, Wireless 
### URL: https://www.jesusninoc.com/2015/11/17/como-ver-la-contrasena-de-las-conexiones-inalambricas/
```PowerShell
(netsh wlan show interface | Select-String SSID)[0] | %{
[String]$SSID=$_
$SSID=$SSID.replace("SSID","").replace(":","").trim()
$SSID
netsh wlan show profile name=$SSID key=clear | Select-String 'Contenido de la clave'
}

```
