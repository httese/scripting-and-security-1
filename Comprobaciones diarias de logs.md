# Comprobaciones diarias de logs
## Logs, Security, Servers 
### URL: https://www.jesusninoc.com/2009/05/13/comprobaciones-diarias-de-logs/
```PowerShell
logparser "SELECT [cs-uri], COUNT(*) AS EXPR1 FROM 'C:\WINDOWS\system32\LogFiles\HTTPERR*' GROUP BY [cs-uri] ORDER BY expr1 desc" -i:HTTPERR -o:DATAGRID

```
```PowerShell
logparser "SELECT [cs-uri-query], COUNT(*) AS EXPR1 FROM 'C:\WINDOWS\system32\LogFiles\A_smtp\SMTPSVC1*' GROUP BY [cs-uri-query] ORDER BY expr1 desc" -i:W3C -o:DATAGRID

```
```PowerShell
logparser "SELECT [cs-uri-stem], COUNT(*) AS EXPR1 FROM 'C:WINDOWS\system32\LogFiles\W3SVC1*' GROUP BY [cs-uri-stem] ORDER BY expr1 desc" -i:W3C -o:DATAGRID

```
