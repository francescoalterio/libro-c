printf("%s\n", nombre);

# Arreglos y cadenas en C

En C, los arreglos (arrays) y las cadenas de texto funcionan de manera diferente a JavaScript. No son objetos dinámicos, sino bloques de memoria de tamaño fijo. Es fundamental entender cómo se almacenan y manipulan.

## Arreglos

Un arreglo es una colección de elementos del mismo tipo, almacenados de forma contigua en memoria. El tamaño debe ser conocido en tiempo de compilación (no puedes hacer `push` como en JS).

```c
int numeros[5] = {1, 2, 3, 4, 5};
float decimales[3];
decimales[0] = 1.1;
```

> En C, los índices empiezan en 0, igual que en JS. Acceder fuera de los límites del arreglo produce comportamiento indefinido (no hay error automático).

## Arreglos multidimensionales

Puedes crear matrices (arreglos de arreglos) de cualquier dimensión, pero debes especificar el tamaño de cada dimensión.

```c
int matriz[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

> No existen arrays asociativos ni objetos como en JS. Todo es numérico y estático.

## Strings (cadenas de caracteres)

En C, una cadena es simplemente un arreglo de `char` terminado en el carácter especial `\0` (null). No hay tipo `string` como tal.

```c
char nombre[] = "Juan";
printf("%s\n", nombre);
```

> ⚠️ Si olvidas el `\0`, las funciones de string pueden leer basura de memoria.

## Funciones útiles de string.h

La librería `<string.h>` provee funciones para manipular cadenas:

- `strlen` (longitud)
- `strcpy` (copiar)
- `strcat` (concatenar)
- `strcmp` (comparar)

```c
#include <string.h>
char a[20] = "hola";
char b[10] = "mundo";
strcat(a, b); // a = "holamundo"
```

> Consejo: Siempre asegúrate de que el arreglo tenga espacio suficiente para la cadena resultante.

## Diferencias con JavaScript

- No existen métodos como `.map()`, `.push()`, `.split()`, etc.
- No hay strings inmutables: puedes modificar los caracteres de una cadena directamente.
- El manejo de memoria es manual: debes reservar suficiente espacio y evitar desbordamientos.
