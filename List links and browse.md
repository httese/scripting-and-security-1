# List links and browse
## PowerShell 
### URL: https://www.jesusninoc.com/2013/01/01/list-links-and-browse/
```PowerShell
$clave=0;
for($jp=0;$jp -le 1052;$jp++)
{
$psObject = $null
$psObject = New-Object psobject
$urls="https://example.com?val=" + $jp
$result=Invoke-WebRequest $urls
$lucky = $result.AllElements | ? {$_.tagName -eq "tr"}
$i=0
foreach($aen in $lucky.outerHTML){
$aen=$aen.Replace("","")
$aen=$aen.Replace("","")
$aen=$aen.Replace("","#")
$a=$aen.Split("#")
if ($i -gt 1 -and $a[1] -ne "")
{
#Add-Member -InputObject $psobject -MemberType noteproperty -Name $a[0].Trim() -Value $a[1].Trim()
Add-Member -InputObject $psobject -MemberType noteproperty -Name $clave -Value $a[1].Trim()
$clave=$clave+1
}
$i=$i+1
}
$psObject >> joinCSV.csv
echo "vez" + $jp
}

```
