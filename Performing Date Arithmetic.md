# Performing Date Arithmetic
## PowerShell 
### URL: https://www.jesusninoc.com/2014/12/04/performing-date-arithmetic/
```PowerShell
New-TimeSpan $(Get-Date) $(Get-Date -month 12 -day 31 -year 2016)

```
```PowerShell
Days : 760
Hours : 0
Minutes : 0
Seconds : 0
Milliseconds : 0
Ticks : 656640000000000
TotalDays : 760
TotalHours : 18240
TotalMinutes : 1094400
TotalSeconds : 65664000
TotalMilliseconds : 65664000000

```
```PowerShell
$(Get-Date)

```
```PowerShell
New-TimeSpan $(Get-Date) $(Get-Date -month 12 -day 31 -year 2016)

```
```PowerShell
New-TimeSpan $(Get-Date) $(Get-Date -month 12 -day 31 -year 2016 -hour 23 -minute 30)

```
