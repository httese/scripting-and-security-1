# chown (System Call) (example)
## C, Filesystem, Operating Systems, Permissions 
### URL: https://www.jesusninoc.com/2014/12/08/chown-system-call-example/
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <sys/stat.h>

int main(int argc, char **argv)
{
char buf[100] = "/home/user/example.txt";
if (chown (buf,100,100) < 0)
{
exit(1);
}
return(0);
}

```
