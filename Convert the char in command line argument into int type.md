# Convert the char in command line argument into int type
## C 
### URL: https://www.jesusninoc.com/2015/10/08/convert-the-char-in-command-line-argument-into-int-type/
```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
int i;
//print the char in *argv[]
for(i = 0; i < argc; i++)
{
fprintf(stdout, "Arg %d: %s\n", i, argv[i]);
}

if (argc > 1)
{
i = atoi(argv[1]); //convert char to int
fprintf(stdout, "Int version of 1st arg: %d\n", i);
}

return 0;
}

```
