# Detectar las palabras que están en el diccionario dentro de una frase
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2015/01/05/detectar-las-palabras-que-estan-en-el-diccionario-dentro-de-una-frase/
```PowerShell
$texto='La casa nueva de Pablo'
Get-Content F:\power\diccionario\dict.txt | %{
if($texto -match $_){
$_
}
}

```
