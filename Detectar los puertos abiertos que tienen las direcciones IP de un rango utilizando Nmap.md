# Detectar los puertos abiertos que tienen las direcciones IP de un rango utilizando Nmap
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/09/05/detectar-los-puertos-abiertos-que-tienen-las-direcciones-ip-de-un-rango-utilizando-nmap/
```PowerShell
1..254 | %{nmap ('192.168.1.'+$_)}

```
