# Mostrar los cargos directivos de las empresas del IBEX 35
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2015/12/31/mostrar-los-cargos-directivos-de-las-empresas-del-ibex-35/
```PowerShell
$web=Invoke-WebRequest 'http://www.bolsamadrid.es/esp/aspx/Mercados/Precios.aspx?indice=ESI100000000'
$todas=$web.AllElements | Where Class -eq “DifFlBj” | %{$_.innerText}
$todas=$todas+($web.AllElements | Where Class -eq “DifFlSb” | %{$_.innerText})
$todas=$todas+($web.AllElements | Where Class -eq “DifFlIg” | %{$_.innerText})
$todas| %{
$empresa=$_

Start-Sleep -Seconds 5

$urlempresa='https://www.empresia.es/empresa/'+$empresa
$urlempresa

$webempresa=Invoke-WebRequest $urlempresa
$webempresa.AllElements | Where id -eq “ListaRelaciones” | %{$nombresdirectivos+=$_.innerText}

$nombresdirectivos
}

```
