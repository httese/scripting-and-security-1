# Compose and send mail messages using Outlook
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/01/11/compose-send-e-mail-messages-using-outlook/
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
STRING $create = New-Object -comObject Outlook.Application
ENTER
STRING $Mail = $create.CreateItem(0)
ENTER
STRING $Mail.Recipients.Add("example@example.com")
ENTER
STRING $Mail.Subject = "Ducky Scripts"
ENTER
STRING $Mail.Body = "Test Mail"
ENTER
STRING $Mail.Send()
ENTER
DELAY 2050
F5

```
