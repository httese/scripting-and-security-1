# Buscar una cadena entro de la caché del DNS
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/10/06/buscar-una-cadena-entro-de-la-cache-del-dns/
```PowerShell
Get-DnsClientCache | Select-String "jesusninoc"

```
