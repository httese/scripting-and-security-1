# Abrir direcciones en Safari leyendo desde un fichero, para cada una de las direcciones hacer clic en una posición del navegador y después cerrarlo
## AppleScript, Automation 
### URL: https://www.jesusninoc.com/2016/02/05/abrir-direcciones-en-safari-leyendo-desde-un-fichero-para-cada-una-de-las-direcciones-hacer-clic-en-una-posicion-del-navegador-y-despues-cerrarlo/
```AppleScript
set direcciones to paragraphs of (read POSIX file "/Users/lamac/Desktop/fichero.txt")
repeat with linea in direcciones
	tell application "Safari"
		open location linea
		activate
	end tell
	delay 10
	activate application "Safari"
	tell application "System Events"
		tell process "Safari"
			clic at {544, 273}
		end tell
	end tell
	delay 20
	tell application "Safari"
		quit
	end tell
	delay 10
end repeat

```
