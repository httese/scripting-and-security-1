# Create users with passwords
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2014/02/05/create-users-with-passwords/
```PowerShell
#Content file user.txt:
#(line 1)pepito,pass1
#(line 2)juanito,pass2

$userandpass=Get-Content .user.txt
foreach($i in $userandpass)
{
    $partiruserandpass=$i.Split(",")
    net user $partiruserandpass[0] /add $partiruserandpass[1]
}

```
