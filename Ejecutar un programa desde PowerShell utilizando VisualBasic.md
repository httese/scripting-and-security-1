# Ejecutar un programa desde PowerShell utilizando VisualBasic
## PowerShell, Visual Basic 
### URL: https://www.jesusninoc.com/2016/02/10/ejecutar-un-programa-desde-powershell-utilizando-visualbasic/
```PowerShell
#Ejecuta un programa y devuelve un entero que contiene el identificador de proceso del programa si aún se está ejecutando.
#https://msdn.microsoft.com/en-us/library/microsoft.visualbasic.interaction.shell(v=vs.110).aspx

Add-Type -AssemblyName Microsoft.VisualBasic

[Microsoft.VisualBasic.Interaction]::Shell("C:\Windows\system32\calc.exe")

```
