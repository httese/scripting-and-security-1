# Create users with passwords on a remote computers
## Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2014/04/17/create-users-with-passwords-on-a-remote-computers/
```PowerShell
#Create users with passwords on a remote computers

#Important
#Need activate:
#PS C:\Windows\System32\WindowsPowerShellv1.0> C:\Windows\System32\svchost.exe -k NetworkService
#PS C:\Windows\System32\WindowsPowerShellv1.0> winrm quickconfig
#Execute PowerShell as administrator

#Content file user.txt:
#(line 1)pepito,pass1
#(line 2)juanito,pass2

$userandpass=Get-Content C:\powershell\fichero.txt
foreach($i in $userandpass)
{
$partiruserandpass=$i.Split(“,”)
Invoke-Command{ net user $partiruserandpass[0] /add $partiruserandpass[1]} -Computername computer
}

```
