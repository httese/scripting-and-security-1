# Buscar comportamientos extraños en los logs
## Logs, Security, Servers 
### URL: https://www.jesusninoc.com/2009/05/04/buscar-comportamientos-extranos-en-los-logs/
```PowerShell
SELECT     Date, [c-ip], [cs(Referer)], [cs-uri-stem], [cs-uri-query], [cs-uri]
FROM         tabla
WHERE     (Date > '2009-04-27')
ORDER BY Date

```
