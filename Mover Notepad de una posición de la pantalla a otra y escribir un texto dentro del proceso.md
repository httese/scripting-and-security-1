# Mover Notepad de una posición de la pantalla a otra y escribir un texto dentro del proceso
## PowerShell 
### URL: https://www.jesusninoc.com/2016/03/23/mover-notepad-de-una-posicion-de-la-pantalla-a-otra-y-escribir-un-texto-dentro-del-proceso/
```PowerShell
#Activar Notepad, moverlo a otra posición de la pantalla a otra y escribir un texto dentro de notepad

Add-Type @"
using System;
using System.Runtime.InteropServices;
public class Win32 {
[DllImport("user32.dll")]
public static extern bool MoveWindow(IntPtr hWnd, int X, int Y, int nWidth, int nHeight, bool bRepaint);
}
"@

$codigo='
[DllImport("user32.dll", EntryPoint = "FindWindowEx")]public static extern IntPtr FindWindowEx(IntPtr hwndParent, IntPtr hwndChildAfter, string lpszClass, string lpszWindow);
[DllImport("User32.dll")]public static extern int SendMessage(IntPtr hWnd, int uMsg, int wParam, string lParam);
'
$acciones=Add-Type -MemberDefinition $codigo -Name TextoNotepad -PassThru
#FindWindowEx(IntPtr hwndParent, IntPtr hwndChildAfter, string lpszClass, string lpszWindow)
#SendMessage(IntPtr hWnd, int uMsg, int wParam, string lParam)

$notepad=Start-Process notepad -PassThru
$notepad.WaitForInputIdle()

Start-Sleep -Seconds 3

$Script=New-Object -ComObject WScript.Shell
$Script.AppActivate($notepad.MainWindowTitle)
[Win32]::MoveWindow(($notepad).MainWindowHandle, 100, 200, 300, 400, $true)

Start-Sleep -Seconds 3

$acciones::SendMessage([IntPtr]$acciones::FindWindowEx($notepad.MainWindowHandle, [IntPtr]::Zero, "Edit", $null), 0x000C, 0, "Texto")

```
