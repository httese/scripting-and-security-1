# Obtener información sobre los controladores USB
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2015/02/12/obtener-informacion-sobre-los-controladores-usb/
```PowerShell
gwmi Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort Manufacturer,Description,DeviceID | Ft -GroupBy Manufacturer Description,Service,DeviceID

```
