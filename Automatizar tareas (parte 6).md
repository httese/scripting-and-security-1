# Automatizar tareas (parte 6)
## Automation, Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2015/10/23/automatizar-tareas-parte-6/
```PowerShell
#Leer operaciones desde un fichero

#Ejemplo de contenido
#Dibujar y colorear una casa en Paint

#Guardar el siguiente contenido sin el carácter # en un fichero llamado accionescasa.txt
#abrir,mspaint.exe
#principio,450,350
#fin,400,400
#principio,450,350
#fin,500,400
#principio,400,400
#fin,500,400
#esperar,5
#principio,400,500
#fin,500,500
#esperar,5
#principio,400,400
#fin,400,500
#esperar,5
#principio,500,400
#fin,500,500
#colorearrojo,451,380
#colorearmarron,448,446

#Importante:
#Sustituir las comillas en la variable $MouseEventSig

$MouseEventSig=@’
[DllImport("user32.dll",CharSet=CharSet.Auto, CallingConvention=CallingConvention.StdCall)]
public static extern void mouse_event(long dwFlags, long dx, long dy, long cButtons, long dwExtraInfo);
‘@

Get-Content D:\power\accionescasa.txt | %{
$MouseEvent = Add-Type -memberDefinition $MouseEventSig -name “MouseEventWinApi” -passThru

$operacion=$_.split(‘,’)[0]
$param1=$_.split(‘,’)[1]
$param2=$_.split(‘,’)[2]

switch($operacion){
‘abrir'{
Start-Process $param1
Start-Sleep -Seconds 5
break
}
‘escribir'{
[System.Windows.Forms.SendKeys]::SendWait($param1)
break
}
‘clic'{
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
break
}
‘esperar'{
Start-Sleep -Seconds $param1
break
}
‘mover'{
for($i=0;$i -ne $param1;$i=$i+1){
Start-Sleep -Milliseconds 10
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($i,$param2)
}
break
}
‘clicderecho'{
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000008, 0, 0, 0, 0);
$MouseEvent::mouse_event(0x00000010, 0, 0, 0, 0);
break
}
‘principio'{
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
break
}
‘fin'{
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
break
}
‘colorearrojo'{
#Hacer clic en bote de pintura, la posición se puede cambiar, en este caso es 363,155
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(363,155)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
#Hacer clic en el color rojo, la posición se puede cambiar, en este caso es 767,146
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(767,146)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
#Colorear con el bote de pintura una vez obtenido el color en la posición que se indica en el fichero
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
break
}
‘colorearmarron'{
#Hacer clic en bote de pintura, la posición se puede cambiar, en este caso es 363,155
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(363,155)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
#Hacer clic en el color rojo, la posición se puede cambiar, en este caso es 767,146
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(746,167)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
#Colorear con el bote de pintura una vez obtenido el color en la posición que se indica en el fichero
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($param1,$param2)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
break
}
}
}

```
