# Impresoras que hay en el sistema
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2016/06/18/impresoras-que-hay-en-el-sistema/
```PowerShell
(Get-WmiObject Win32_Printer).name

```
