# Leer las tendencias de búsqueda en Google Trends mediante la voz del sistema operativo en Linux
## Automation, Bash, Multimedia 
### URL: https://www.jesusninoc.com/2016/02/29/leer-las-tendencias-de-busqueda-en-google-trends-mediante-la-voz-del-sistema-operativo-en-linux/
```Shell
wget --quiet -O - https://www.google.es/trends/hottrends/atom/feed?pn=p26 | sed -n -e 's!.*<title>\(.*\)</title>.*!\1!p' | festival --tts --pipe

```
