# Añadir los nombres de los procesos a una ArrayList
## PowerShell 
### URL: https://www.jesusninoc.com/2016/09/14/anadir-los-nombres-de-los-procesos-a-una-arraylist/
```PowerShell
#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList

ForEach ($elemento in (ps | Group-Object Name).Name){
#Agrega un objeto al final de ArrayList, en este caso el objeto es cada nombre de proceso
[void]$arraylist.Add($elemento)
}

#Número de elementos de ArrayList
$arraylist.Count
 
#Muestra todos los elementos de ArrayList ordenados
$arraylist

```
