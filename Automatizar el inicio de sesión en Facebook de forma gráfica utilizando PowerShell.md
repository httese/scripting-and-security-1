# Automatizar el inicio de sesión en Facebook de forma gráfica utilizando PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2015/07/17/automatizar-el-inicio-de-sesion-en-facebook-de-forma-grafica-utilizando-powershell/
```PowerShell
#Importar DLL para simular el clic del ratón
$MouseEventSig=@'
[DllImport("user32.dll",CharSet=CharSet.Auto, CallingConvention=CallingConvention.StdCall)]
public static extern void mouse_event(long dwFlags, long dx, long dy, long cButtons, long dwExtraInfo);
'@
$MouseEvent = Add-Type -memberDefinition $MouseEventSig -name "MouseEventWinApi" -passThru

Start-Process chrome https://www.facebook.com

#Esperar a cargar correctamente la página
Start-Sleep -Seconds 10

#Situar el ratón en la caja de texto "Correo o teléfono"
[System.Windows.Forms.Cursor]::Position=New-Object System.Drawing.Point(819,104)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
[System.Windows.Forms.SendKeys]::SendWait('facebook@facebook.com')

#Situar el ratón en la caja de texto "Contraseña"
[System.Windows.Forms.Cursor]::Position=New-Object System.Drawing.Point(945,104)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)
[System.Windows.Forms.SendKeys]::SendWait('contracontra')

#Pulsar la tecla ENTER
[System.Windows.Forms.SendKeys]::SendWait(‘{ENTER}’)

```
