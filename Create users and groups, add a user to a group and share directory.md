# Create users and groups, add a user to a group and share directory
## PowerShell, Security, Users 
### URL: https://www.jesusninoc.com/2014/03/03/create-users-and-groups-add-user-to-a-group-and-share-directory/
```PowerShell
#Read file, create users and groups, add user to group, create a directory for each user and share directory
#File content:
#g,grupo
#u,pepe,pass,grupo

foreach($val in Get-Content d:\usergroup.txt)
{
$sli=$val.Split(",")
if($sli.Length -eq 2)
{
Write-Host "Create group"

#Create a group $sli[1]
net localgroup $sli[1] /add
}
elseif($sli.Length -eq 4)
{
Write-Host "Create user"

#Crete user $sli[1], value $sli[2]
net user $sli[1] /add $sli[2]

#Add user to group $sli[3]
net localgroup $sli[3] $sli[1] /add

#Add directory and share
[string]$ruta="d:\"+$sli[1]
New-Item $ruta -ItemType directory

#Command use string parameters
[string]$aux=$sli[1]
net share $aux=$ruta
}
else
{
Write-Host "Error"
}
}

```
