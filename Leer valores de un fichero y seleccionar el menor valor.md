# Leer valores de un fichero y seleccionar el menor valor
## PowerShell 
### URL: https://www.jesusninoc.com/2016/08/12/leer-valores-de-un-fichero-y-seleccionar-el-menor-valor/
```PowerShell
#El fichero valores tiene un valor por línea 40, 90, 100
gc D:\valores.txt | %{
    #Mostrar el valor cuando es menor de 50
    if($_ -lt 50){$_}
}

```
