# Ejecutar Google Chrome en Android mediante ADB a través de PowerShell
## Android, PowerShell 
### URL: https://www.jesusninoc.com/2016/03/25/ejecutar-google-chrome-en-android-mediante-adb-a-traves-de-powershell/
```PowerShell
#Abrir Google Chrome en Android mediante ADB
#Es necesario habilitar el modo depuración en Android
#Link: https://www.elandroidelibre.com/2015/01/como-activar-el-modo-depuracion-usb-en-android.html
#Link: https://theunlockr.com/2009/10/06/how-to-set-up-adb-usb-drivers-for-android-devices/
cd "D:\program\android-sdk-windows\platform-tools"
.\adb shell am start -n com.android.chrome/com.google.android.apps.chrome.Main

```
