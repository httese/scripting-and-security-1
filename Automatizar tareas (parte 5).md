# Automatizar tareas (parte 5)
## Automation, Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2015/10/20/automatizar-tareas-parte-5/
```PowerShell
#Leer operaciones desde un fichero

#Ejemplo de contenido
#Dibujar una casa en Paint

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

#Importante:
#Sustituir las comillas en la variable $MouseEventSig, en concreto al importar "user32.dll"

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
}
}

```
