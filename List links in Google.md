# List links in Google
## PowerShell 
### URL: https://www.jesusninoc.com/2012/04/23/list-links-in-google/
```PowerShell
$IE= new-object -com InternetExplorer.Application
$IE.navigate2(“https://www.google.es”)

while ($IE.busy) {
sleep -milliseconds 100
}

$IE.visible=$true
$IE.Document.getElementById(“q”).value=”PowerShell”
$IE.visible=$false
$IE.visible=$true
$IE.Document.getElementById(“gbqf”).submit()

while ($IE.busy) {
sleep -milliseconds 1000
}

$links=@($ie.document.getElementsByTagName("a"));
$links | select href

```
