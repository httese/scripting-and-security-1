# Ejecutar un script en Android mediante ADB a través de PowerShell
## Android, Bash, PowerShell 
### URL: https://www.jesusninoc.com/2016/04/06/ejecutar-un-script-en-android-mediante-adb-a-traves-de-powershell/
```PowerShell
Set-Location "C:\Program Files (x86)\Android\android-sdk\platform-tools"
New-Item -Name script.sh -Value "echo hola"
.\adb push .\script.sh /sdcard/
.\adb shell sh /sdcard/script.sh

```
