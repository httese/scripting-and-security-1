# Ver la temperatura de los equipos que hay en la red local utilizando credenciales almacenados en un fichero
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2016/08/28/ver-la-temperatura-de-los-equipos-que-hay-en-la-red-local-utilizando-credenciales-almacenados-en-un-fichero/
```PowerShell
#Es necesario ejecutar PowerShell como administrador
$credenciales=Import-Clixml -Path credenciales.xml
#$credenciales=Get-Credential
1..254 | %{
$Temperatura=Get-WmiObject MSAcpi_ThermalZoneTemperature -Namespace "root/wmi" -ComputerName ('192.168.1.'+$_) -Credential $credenciales
$Kelvin = $Temperatura.CurrentTemperature / 10
$Celsius = $Kelvin - 273.15
$Celsius.ToString() + " C "
}

```
