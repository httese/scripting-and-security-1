# Detectar los puertos abiertos que tienen las direcciones IP de un rango utilizando Nmap mediante un escaneo rápido
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/09/07/detectar-los-puertos-abiertos-que-tienen-las-direcciones-ip-de-un-rango-utilizando-nmap-mediante-un-escaneo-rapido/
```PowerShell
1..254 | %{nmap -F ('192.168.1.'+$_)}

```
