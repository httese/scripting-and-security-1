# Mostrar los cargos directivos de una empresa que aparece en la lista de deudores publicada por la Agencia Tributaria
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/01/06/mostrar-los-cargos-directivos-de-una-empresa-que-aparece-en-la-lista-de-deudores-publicada-por-la-agencia-tributaria/
```PowerShell
#Obtener cada fichero con la lista de deudores publicada por la Agencia Tributaria
#https://www.jesusninoc.com/2015/12/28/buscar-un-nombre-dentro-de-la-lista-de-deudores-publicada-por-la-agencia-tributaria/

ls 'D:\power\pdf\pdf\convertir\deudores' *.txt | %{
#Para deudor buscar información sobre la empresa en Empresia
foreach($listado in gc $_.FullName)
{
#Solo nos quedamos con el identificador deudor
#Quitamos los números de las líneas (NIF/CIF y el importe total de deudas/sanciones pendientes)
$patron = '[^a-z A-Z]'
$empresa=$listado -replace $patron
$empresa

Start-Sleep -Seconds 10

$web=Invoke-WebRequest 'https://www.empresia.es/busqueda/?q='$empresa
$web.AllElements | Where id -eq “ListaRelaciones” | %{$_.innerText}
}
}

```
