# Leer mensajes de correo electrónico de Outlook mediante la voz del Sistema Operativo
## PowerShell 
### URL: https://www.jesusninoc.com/2015/01/21/leer-mensajes-de-correo-electronico-de-outlook-mediante-la-voz-del-sistema-operativo/
```PowerShell
Clear-Host
Add-Type -Assembly "Microsoft.Office.Interop.Outlook"
$Outlook = New-Object -ComObject Outlook.Application
$sam = New-Object -comObject SAPI.SpVoice
$Namespace = $Outlook.GetNameSpace("MAPI")
$NameSpace.Folders.Item(6)
$Email = $NameSpace.Folders.Item(6).Folders.Item(2).Items
$Email | Sort-Object LastModificationTime -Descending | % {
$_.TaskSubject
$sam.Speak($_.ConversationTopic)
($_.CreationTime).Date
($_.LastModificationTime).Date
}

```
