# Create users, add into a group and share directory with permissions in Active Directory
## Filesystem, Permissions, PowerShell, Security 
### URL: https://www.jesusninoc.com/2014/03/05/create-users-add-into-a-group-and-share-directory-with-permissions-in-active-directory/
```PowerShell
#Important: remember change ""

#Create file:
#Users.csv
#cn,sAMAccountname,FirstName,LastName,Password,Group
#user1,user1,username,userlast,secret1123,group

Import-Module ActiveDirectory

#Read file
Import-Csv F:\power\users.csv |%{
$nombreco=$_.FirstName + " " + $_.LastName
$ru="OU=" + $_.Group + ",OU=ou3,OU=ou2,OU=ou1,DC=domain,DC=local"

#Create directory in \serverdepartament
$HomeDirectory="\serverdepartament" + $_.Group + "" + $_.sAMAccountname
mkdir $HomeDirectory
$HomeDirectory
$HomeDrive=’Q:’

#Add user
New-ADUser -Name $_.FirstName -SamAccountName $_.sAMAccountname -HomeDrive $HomeDrive –HomeDirectory $HomeDirectory -DisplayName $nombreco -Enabled $true -ChangePasswordAtLogon $false -AccountPassword (ConvertTo-SecureString $_.Password -AsPlainText -force) -PassThru -UserPrincipalName $_.sAMAccountname -Path $ru

#Add permission for each user (sAMAccountname)
$usereta="domain" + $_.sAMAccountname + ":F"
$HomeDirectory + "-" + $usereta
cacls $HomeDirectory /G $usereta /E

#Add user into a group
Add-ADGroupMember -Identity "CN=groupusers,CN=Builtin,DC=domain,DC=local" $_.sAMAccountname
}

```
