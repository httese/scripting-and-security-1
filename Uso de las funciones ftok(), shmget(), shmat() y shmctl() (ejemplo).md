# Uso de las funciones ftok(), shmget(), shmat() y shmctl() (ejemplo)
## C, Processes 
### URL: https://www.jesusninoc.com/2014/11/22/uso-de-las-funciones-ftok-shmget-shmat-y-shmctl-ejemplo/
```PowerShell
#ifndef _SVID_SOURCE
#define _SVID_SOURCE

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/shm.h>
#include <sys/sem.h>
#include <sys/ipc.h>

#endif
typedef struct
{
int num1;
}zona_mem1;
int main (void)
{

//Declaración de variables

key_t clave1; //clave de acceso a la memoria 1
int shmid1; //identificador de la zona de memoria 1
zona_mem1 *pmem1; //Puntero a la 1 zona de memoria
int comprobar; //variable que me indica la posibilidad de error en la llamada a funciones!
char opc; //indicación de continuación de programa o terminación

//Algoritmo de programa padre.c

clave1 = ftok(".",'s');

//Creación de zona_mem1

shmid1 = shmget(clave1,sizeof(zona_mem1),IPC_CREAT | 0660);

if(shmid1 !=-1)
{
printf("Zona de memoria 1 creada OK! con identificador %d \n", shmid1);
}
else
{
printf("ERROR al crear zona de memoria 1 !! \n");
exit(1);
}

//He obtenido los recursos que necesito, vinculo el proceso con la zona de memoria!!

pmem1 = shmat(shmid1,0,0);

if(pmem1 == -1)
{
printf("Error al vincular el proceso a la zona de memoria 1! \n");
exit(1);
}

pmem1 -> num1 = 0;

//Mantengo en ejecución al programa padre para dar tiempo a leer
do
{
printf("Desea Terminar?? S/N \n");
scanf("%s", &opc);

if(opc == 's')
{

//Elimino las zonas de memoria!!

comprobar = shmctl (shmid1, IPC_RMID,0);

if(comprobar == -1)
{
printf("ERROR al eliminar la 1 zona de memoria!! \n");
exit(1);
}
else
{
printf("Zona de memoria 1 eliminada OK !!\n");
}

}

}while(opc !='s');
}

```
```PowerShell
#ifndef SOURCE
#define SOURCE

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/ipc.h>
#include <sys/sem.h>
#include <sys/shm.h>

#endif

typedef struct
{
int num1;
}zona_mem1;
int main (void)
{

//Declaración de variables

key_t clave1; //clave de acceso a la memoria 1
int shmid1; //identificador de la zona de memoria 1
zona_mem1 *pmem1; //Puntero a la 1 zona de memoria
int comprobar; //variable que me indica la posibilidad de error en la llamada a funciones!
char opc; //indicación de continuación de programa o terminación

//Algoritmo de programa lector.c

clave1 = ftok(".",'s');

//Creación de zona_mem1

shmid1 = shmget(clave1,sizeof(zona_mem1),0);

if(shmid1 !=-1)
{
printf("Zona de memoria 1 creada OK! con identificador %d \n", shmid1);
}
else
{
printf("ERROR al crear zona de memoria 1 !! \n");
exit(1);
}

//He obtenido los recursos que necesito, vinculo el proceso con la zona de memoria!!

pmem1 = shmat(shmid1,0,0);

if(pmem1 == -1)
{
printf("Error al vincular el proceso a la zona de memoria 1! \n");
exit(1);
}
else
{
printf("%d",pmem1 -> num1);
}
}

```
