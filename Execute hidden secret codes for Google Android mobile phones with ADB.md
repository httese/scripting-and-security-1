# Execute hidden secret codes for Google Android mobile phones with ADB
## Android 
### URL: https://www.jesusninoc.com/2016/04/21/execute-hidden-secret-codes-for-google-android-mobile-phones-with-adb/
```PowerShell
adb.exe shell am start -a android.intent.action.VIEW tel:*
Start-Sleep -Seconds 5
adb shell input keyevent "KEYCODE_DEL"
Start-Sleep -Seconds 5
adb shell input text "*#*#4636#*#*"

```
