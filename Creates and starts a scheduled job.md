# Creates and starts a scheduled job
## PowerShell, Schedule tasks 
### URL: https://www.jesusninoc.com/2016/05/14/creates-and-starts-a-scheduled-job/
```PowerShell
#Creates a scheduled job (Daily 11pm)
$tarea=New-JobTrigger -Daily -At 11pm
Register-ScheduledJob -Name LsDaily -Trigger $tarea -ScriptBlock {ls}

#Starts a Windows PowerShell background job
Start-Job -DefinitionName LsDaily

#Gets Windows PowerShell background jobs that are running in the current session
Get-Job -Name LsDaily | Receive-Job

```
