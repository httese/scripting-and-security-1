# Parar un proceso en Windows desde Python
## PowerShell, Processes, Python 
### URL: https://www.jesusninoc.com/2016/05/17/parar-un-proceso-en-windows-desde-python/
```Python
import os
os.system("powershell stop-process -name notepad")

```
