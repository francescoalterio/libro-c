# Memoria dinámica en C

En C, la memoria dinámica te permite reservar espacio en tiempo de ejecución, a diferencia de los arreglos estáticos cuyo tamaño debe ser conocido en tiempo de compilación. Esto es similar a cómo los arrays y objetos en JS pueden crecer dinámicamente, pero en C debes gestionar la memoria manualmente.

## malloc, calloc, realloc, free

Las funciones de la librería `<stdlib.h>` permiten reservar y liberar memoria:

- `malloc`: reserva memoria sin inicializar
- `calloc`: reserva e inicializa en 0
- `realloc`: cambia el tamaño de un bloque ya reservado
- `free`: libera la memoria

```c
#include <stdlib.h>

int *arr = (int*) malloc(5 * sizeof(int));
if (arr == NULL) {
    printf("Error de memoria\n");
}
// ... usar arr ...
free(arr);
```

> Siempre verifica que el puntero no sea NULL antes de usar la memoria reservada.

## Errores comunes

- Memory leaks: no liberar memoria reservada con `free`.
- Dangling pointers: usar punteros después de liberar la memoria.
- Acceso fuera de los límites: puede corromper datos o causar fallos.

## Diferencias con JavaScript

- En JS, el garbage collector libera la memoria automáticamente.
- En C, tú eres responsable de liberar toda la memoria que reservas.
- Un error en la gestión de memoria puede causar bugs difíciles de detectar.
