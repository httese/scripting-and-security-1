# Detectar si hay un APK infectado en Android
## Android, PowerShell 
### URL: https://www.jesusninoc.com/2016/04/11/detectar-si-hay-un-apk-infectado-en-android/
```PowerShell
.\adb shell pm list packages | %{if($_ -match "meta"){"Android infectado";$_}}

```
