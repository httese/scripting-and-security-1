# Cambiar el fondo de escritorio
## PowerShell, Registry, Web 
### URL: https://www.jesusninoc.com/2015/11/06/cambiar-el-fondo-de-escritorio/
```PowerShell
$RegKey='HKCU:\Control Panel\Desktop\'
Set-ItemProperty -Path $RegKey -Name ‘Wallpaper’ -Value ‘C:\Windows\web\wallpaper\Windows\img1.jpg’

```
