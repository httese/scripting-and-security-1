# Zombie process
## Bash, Processes 
### URL: https://www.jesusninoc.com/2014/11/13/zombie-processes/
```Shell
ps -A -ostat,ppid,pid,cmd | grep -e ‘^[Zz]‘

```
