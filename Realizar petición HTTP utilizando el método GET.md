# Realizar petición HTTP utilizando el método GET
## PHP, PowerShell, Servers, Web 
### URL: https://www.jesusninoc.com/2016/01/02/realizar-peticion-http-utilizando-el-metodo-get/
```PowerShell
#Crear el fichero PHP con el contenido:
#<?php echo htmlspecialchars($_GET['nombre']); ?> tiene <?php echo (int)$_GET['edad']; ?> años.

$postParams = @{nombre='Juan';edad='34'}
$web=Invoke-WebRequest -Uri 'https://localhost/exampleget.php' -Method Get -Body $postParams
#$web=Invoke-WebRequest -Uri 'https://localhost/exampleget.php?nombre=Juan&edad=34'
$web.content

```
