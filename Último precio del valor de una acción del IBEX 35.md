# Último precio del valor de una acción del IBEX 35
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/03/19/ultimo-precio-del-valor-de-una-accion-del-ibex-35/
```PowerShell
#Cotización del mismo día
$fechamismodia=(Get-Date -Format dd/MM/yyyy)
$fechamismodia;((((((Invoke-WebRequest 'https://www.bolsamadrid.es/esp/aspx/Empresas/FichaValor.aspx?ISIN=ES0148396007').AllElements).where{$_.Class -eq "TblPort"}).innerHTML | Select-String $fechamismodia) -split '[\r\n]' | Select-String $fechamismodia) -replace "<td>","*" -replace "<.*?>").split('*')[3]
#Cotización del día anterior
$fechaundiamenos=(Get-Date).AddDays(-1).ToString("dd/MM/yyyy")
$fechaundiamenos;((((((Invoke-WebRequest 'https://www.bolsamadrid.es/esp/aspx/Empresas/FichaValor.aspx?ISIN=ES0148396007').AllElements).where{$_.Class -eq "TblPort"}).innerHTML | Select-String $fechaundiamenos) -split '[\r\n]' | Select-String $fechaundiamenos) -replace "<td>","*" -replace "<.*?>").split('*')[3]
#Cotización de hace dos días
$fechadosdiasmenos=(Get-Date).AddDays(-2).ToString("dd/MM/yyyy")
$fechadosdiasmenos;((((((Invoke-WebRequest 'https://www.bolsamadrid.es/esp/aspx/Empresas/FichaValor.aspx?ISIN=ES0148396007').AllElements).where{$_.Class -eq "TblPort"}).innerHTML | Select-String $fechadosdiasmenos) -split '[\r\n]' | Select-String $fechadosdiasmenos) -replace "<td>","*" -replace "<.*?>").split('*')[3]

```
