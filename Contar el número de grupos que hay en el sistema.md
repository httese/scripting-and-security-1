# Contar el número de grupos que hay en el sistema
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2016/07/16/contar-el-numero-de-grupos-que-hay-en-el-sistema/
```PowerShell
(Get-WmiObject Win32_Group | Select-Object Name).count

```
