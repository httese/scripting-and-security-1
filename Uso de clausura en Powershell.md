# Uso de clausura en Powershell
## PowerShell 
### URL: https://www.jesusninoc.com/2016/02/27/uso-de-clausura-en-powershell/
```PowerShell
function Nuevo-Contador ($incremento=1)
{
$contador=0
{
$script:contador += $incremento
$contador
}.GetNewClosure()
}

```
```PowerShell
$var1 = Nuevo-Contador
#Incremento normal
& $var1
& $var1

$var2 = Nuevo-Contador 2
#Incremento con un nuevo contador
& $var2
& $var2

```
