# Ejemplos de ejecución de comandos en Bash y PowerShell (parte 3)
## Bash, Filesystem, PowerShell, Web 
### URL: https://www.jesusninoc.com/2008/10/01/ejemplos-de-ejecucion-de-comandos-en-bash-y-powershell-parte-3/
```Shell
awk '{print $2,$5;}' empleados.txt

```
```PowerShell
Get-Content .\empleados.txt | %{Write-Host $_.Split(' ')[1], $_.Split(' ')[4]}

```
```Shell
wc empleados.txt

```
```PowerShell
(Get-Content .\empleados.txt).Length

```
```Shell
sed '1d' empleados.txt

```
```PowerShell
@(Get-Content .\empleados.txt).Where{$_ -notmatch "Juan"}

```
