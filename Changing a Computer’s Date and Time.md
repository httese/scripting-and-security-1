# Changing a Computer’s Date and Time
## PowerShell 
### URL: https://www.jesusninoc.com/2014/12/03/changing-computers-date-time/
```PowerShell
Set-Date -date "6/6/2015 1:11 AM"

```
```PowerShell
Set-Date (Get-Date).AddDays(2)

```
```PowerShell
Set-Date (Get-Date).AddHours(-1)

```
```PowerShell
Set-Date -adjust 1:11:11

```
