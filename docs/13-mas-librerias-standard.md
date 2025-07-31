# Otras librerías estándar útiles en C

Además de las librerías vistas antes, C incluye muchas otras librerías estándar que facilitan tareas comunes. Aquí tienes algunas de las más útiles y sus diferencias con lo que podrías encontrar en JavaScript.

## math.h

Proporciona funciones matemáticas como `sqrt`, `pow`, `sin`, `cos`, etc. Es similar al objeto `Math` en JS, pero aquí debes incluir la cabecera y enlazar la librería matemática al compilar (a veces con `-lm`).

```c
#include <math.h>
double raiz = sqrt(16.0);
```

> Consejo: Para usar funciones trigonométricas y de potencias, los argumentos suelen ser de tipo `double`.

## time.h

Permite trabajar con fechas y horas, medir intervalos y obtener la hora actual. No es tan flexible como las Date de JS, pero es suficiente para la mayoría de tareas básicas.

```c
#include <time.h>
time_t ahora = time(NULL);
printf("%ld\n", ahora);
```

> El valor retornado es el número de segundos desde el 1 de enero de 1970 (época Unix).

## stdbool.h

Define el tipo booleano `bool` y los valores `true` y `false`. Antes de esta librería, se usaban enteros (0 y 1) para representar booleanos.

```c
#include <stdbool.h>
bool activo = true;
```

## assert.h

Permite hacer afirmaciones en tiempo de ejecución para depuración. Si la condición es falsa, el programa termina y muestra un mensaje.

```c
#include <assert.h>
assert(2 + 2 == 4);
```

## Operaciones sobre cadenas (string.h)

Además de las funciones ya vistas (`strlen`, `strcpy`, `strcat`, `strcmp`), existen otras útiles:

- `strncpy`, `strncat` (copiar/concatenar con límite)
- `strchr`, `strrchr` (buscar carácter)
- `strstr` (buscar substring)
- `sprintf`, `snprintf` (formatear cadenas)

```c
char origen[] = "Hola mundo";
char destino[20];
strncpy(destino, origen, 5); // copia "Hola "
```

## Prueba y conversión de clases de caracteres (ctype.h)

La librería `<ctype.h>` permite probar y convertir caracteres:

- `isdigit`, `isalpha`, `isalnum`, `isspace`, etc.
- `toupper`, `tolower`

```c
#include <ctype.h>
char c = 'a';
if (isalpha(c)) printf("Es letra\n");
printf("%c\n", toupper(c)); // A
```

## ungetc

Permite devolver un carácter al flujo de entrada (útil en parsers):

```c
#include <stdio.h>
int c = getchar();
ungetc(c, stdin); // devuelve el carácter leído
```

## Ejecución de órdenes (system)

Puedes ejecutar comandos del sistema operativo con `system()`:

```c
#include <stdlib.h>
system("dir"); // en Windows
system("ls");  // en Linux/Mac
```

## Generación de números aleatorios

La librería `<stdlib.h>` provee `rand()` y `srand()`:

```c
#include <stdlib.h>
#include <time.h>
srand(time(NULL)); // inicializa la semilla
int aleatorio = rand() % 100; // número entre 0 y 99
```

> Recuerda inicializar la semilla con `srand` para obtener resultados diferentes cada vez.

## Diferencias con JavaScript

- En JS, muchas de estas utilidades están integradas en el lenguaje o en el entorno de ejecución.
- En C, debes incluir explícitamente cada cabecera y conocer las funciones disponibles.
