# List processes by % CPU
## Bash, Processes 
### URL: https://www.jesusninoc.com/2016/01/18/list-processes-by-cpu/
```Shell
ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'

```
