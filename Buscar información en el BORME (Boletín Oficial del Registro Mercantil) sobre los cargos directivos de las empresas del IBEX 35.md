# Buscar información en el BORME (Boletín Oficial del Registro Mercantil) sobre los cargos directivos de las empresas del IBEX 35
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/01/01/buscar-informacion-en-el-borme-boletin-oficial-del-registro-mercantil-sobre-los-cargos-directivos-de-las-empresas-del-ibex-35/
```PowerShell
$web=Invoke-WebRequest 'http://www.bolsamadrid.es/esp/aspx/Mercados/Precios.aspx?indice=ESI100000000'
$web.AllElements | Where Class -eq “DifFlBj” | %{
$empresa=$_.innerText
$empresa

Start-Sleep -Seconds 5

$urlempresa='https://www.empresia.es/empresa/'+$empresa
$urlempresa

$webempresa=Invoke-WebRequest $urlempresa
$webempresa.AllElements | Where id -eq “ListaRelaciones” | %{$nombresdirectivos+=$_.innerText}

$nombresdirectivos
Start-Sleep -Seconds 5

foreach($directivo in $nombresdirectivos -split '[\r\n]')
{
$urlgoogle='https://www.google.es/search?q=inurl:boe.es+'+$directivo
Start-Sleep -Seconds 5
$webgoogle=Invoke-WebRequest $urlgoogle
$informaciondirectivo=@($webgoogle.AllElements | Where Class -eq “st”).innerText
$informaciondirectivo
Start-Sleep -Seconds 5
}
}

#
#IMPORTANTE TENER EN CUENTA A LA HORA DE UTILIZAR EL SIGUIENTE SCRIPT
#
#Invoke-WebRequest : 
#To continue, please type the characters below:
#About this page
#Our systems have detected unusual traffic from your computer network. This page checks to see if it's really you sending the requests, and not a robot. Why did this happen?
#This page appears when Google automatically detects requests coming from your computer network which appear to be in violation of the Terms of Service. The block will expire 
#shortly after those requests stop. In the meantime, solving the above CAPTCHA will let you continue to use our services.
#This traffic may have been sent by malicious software, a browser plug-in, or a script that sends automated requests. If you share your network connection, ask your administrator 
#for help — a different computer using the same IP address may be responsible. Learn more
#Sometimes you may be asked to solve the CAPTCHA if you are using advanced terms that robots are known to use, or sending requests very quickly.

```
