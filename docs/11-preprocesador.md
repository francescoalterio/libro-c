# El preprocesador en C

El preprocesador ejecuta instrucciones antes de compilar el código.

## #define

Define constantes o macros.

```c
#define PI 3.1416
#define CUADRADO(x) ((x)*(x))
```

## #include

Incluye archivos de cabecera.

```c
#include <stdio.h>
#include "miarchivo.h"
```

## Otras directivas

Sirven para compilación condicional.

# El preprocesador en C

El preprocesador es una etapa previa a la compilación que procesa directivas especiales (líneas que comienzan con `#`). No existe un equivalente directo en JavaScript, aunque algunas herramientas de build hacen cosas similares.

## #define

Permite definir constantes o macros (fragmentos de código que se reemplazan antes de compilar).

```c
#define PI 3.1416
#define CUADRADO(x) ((x)*(x))
```

- Las macros no tienen tipo y pueden causar errores difíciles de depurar si no usas paréntesis correctamente.
- No uses macros para funciones complejas; prefiere funciones normales.

## #include

Incluye archivos de cabecera (headers) en tu código. Es como importar módulos en JS, pero aquí solo se copian declaraciones, no código ejecutable.

```c
#include <stdio.h>
#include "miarchivo.h"
```

> Usa comillas para archivos propios y < > para librerías estándar.

## Archivos de encabezado (header)

Un archivo de encabezado (`.h`) contiene declaraciones de funciones, variables externas, macros y estructuras que quieres compartir entre varios archivos `.c`.

Ejemplo de archivo `util.h`:

```c
#ifndef UTIL_H
#define UTIL_H

void saludar();

#endif
```

Y en tu archivo `.c`:

```c
#include "util.h"

void saludar() {
    printf("Hola!\n");
}
```

> Usa encabezados para organizar y reutilizar tu código. Recuerda protegerlos con directivas `#ifndef`/`#define`/`#endif` para evitar inclusiones múltiples.

## Otras directivas

- `#ifdef`, `#ifndef`, `#endif`, `#undef`: compilación condicional, útil para evitar dobles inclusiones o compilar código solo en ciertas plataformas.

```c
#ifndef MI_HEADER_H
#define MI_HEADER_H
// ... contenido ...
#endif
```

## Diferencias con JavaScript

- En JS, la importación de módulos es dinámica y en tiempo de ejecución.
- En C, el preprocesador solo copia y reemplaza texto antes de compilar.
