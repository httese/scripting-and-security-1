# Mostrar el estándar de radio de las conexiones inalámbricas
## Network, PowerShell, Wireless 
### URL: https://www.jesusninoc.com/2016/01/19/mostrar-el-estandar-de-radio-de-las-conexiones-inalambricas/
```PowerShell
netsh wlan show networks mode=bssid | Select-String SSID,BSSID,'Tipo de radio'

```
