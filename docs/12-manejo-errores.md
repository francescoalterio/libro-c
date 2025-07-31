# Manejo de errores en C

A diferencia de JavaScript, C no tiene excepciones (`try/catch`). El manejo de errores es manual y depende de verificar los valores de retorno de las funciones y, a veces, de variables globales como `errno`.

## errno y perror

Muchas funciones de la librería estándar devuelven un valor especial (como `NULL` o `-1`) para indicar error. Además, pueden modificar la variable global `errno` para indicar el tipo de error.

```c
#include <errno.h>
#include <stdio.h>

FILE *f = fopen("noexiste.txt", "r");
if (f == NULL) {
    perror("Error al abrir archivo"); // imprime un mensaje según errno
}
```

> Consejo: Siempre revisa el valor de retorno de las funciones que pueden fallar.

## exit

Permite finalizar el programa con un código de salida. Por convención, 0 es éxito y cualquier otro valor indica error.

```c
if (error) {
    exit(1);
}
```

- Código 0: éxito
- Otro valor: error

## Diferencias con JavaScript

- En JS puedes lanzar y capturar excepciones; en C debes comprobar manualmente los errores.
- El manejo de errores en C es más bajo nivel y requiere disciplina.
