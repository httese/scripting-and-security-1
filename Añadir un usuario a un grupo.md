# Añadir un usuario a un grupo
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2016/06/23/anadir-un-usuario-a-un-grupo/
```PowerShell
#Añadir usuario a un grupo
$ComputerName = $env:COMPUTERNAME
$nombregrupo='administradores'
$group = [ADSI]"WinNT://$($Computername)/$($nombregrupo),group" 

#Nombre del usuario
$user = 'usuario'
$group.add("WinNT://$($user),user")

```
