# Searching TeamViewer in our system
## Network, PowerShell, Processes, Registry, Security 
### URL: https://www.jesusninoc.com/2014/11/10/searching-teamviewer-system/
```PowerShell
#Process id
$processid=Get-Process -Name TeamViewer_Service
netstat -ano | ForEach-Object {
Select-String $processid.Id -input $_ -AllMatches
}

```
```PowerShell
Get-ChildItem HKCU:\ -rec -ea SilentlyContinue | ForEach-Object {
Select-String "TeamViewer" -input (Get-ItemProperty -Path $_.PsPath) -AllMatches
}

```
```PowerShell
Get-ChildItem c:\ -rec -ea SilentlyContinue | ForEach-Object {
Select-String "TeamViewer" -input (Get-ItemProperty -Path $_.PsPath) -AllMatches
}

```
