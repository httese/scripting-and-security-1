# List computers using net view, compare the MAC and search in the Public MA-L Listing
## Database, Network, PowerShell 
### URL: https://www.jesusninoc.com/2014/05/29/list-computers-using-net-view-compare-mac-search-public-ma-l-listing/
```PowerShell
function Get-NetView
{
switch -regex (NET.EXE VIEW)
{
"^\\(?<Name>S+)s+"
{
$matches.Name
}
}
}

#Search MAC in https://standards.ieee.org/
#https://www.jesusninoc.com/powershell/2014/05/16/search-the-public-ma-l-listing-example-mac/
foreach($i in Get-NetView)
{
Write-Host "Computer: "$i
foreach($mac in (get-wmiobject -class "Win32_NetworkAdapterConfiguration" -computername $i).MACAddress)
{
Write-Host "MAC: "$mac.Substring(0,8)
$url="https://standards.ieee.org/cgi-bin/ouisearch?"+$mac.replace(":","-").Substring(0,8)
$result=Invoke-WebRequest $url
#Here are the results of your search through the public section of the IEEE Standards MA-L database report for MAC
$result.AllElements | Where tagName -eq “PRE”
}
}

```
