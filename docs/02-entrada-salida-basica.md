# Entrada y salida básica en C

La librería estándar `stdio.h` permite mostrar información en pantalla y leer datos del usuario.

## printf: Imprimir en pantalla

```c
#include <stdio.h>

int main() {
    printf("Hola, mundo!\n");
    printf("Mi edad es %d años\n", 25);
    printf("Altura: %.2f metros\n", 1.75);
    return 0;
}
```

- `%d` para enteros
- `%f` para decimales (usa `%.2f` para 2 decimales)
- `%c` para caracteres
- `%s` para cadenas de texto

## puts: Imprimir texto simple

```c
puts("Texto simple\n");
```

## scanf: Leer datos del usuario (básico)

```c
int edad;
printf("¿Cuántos años tienes? ");
scanf("%d", &edad);
printf("Tienes %d años\n", edad);
```

> Nota: Siempre debes pasar la dirección de memoria de la variable con `&` en scanf.

## Resumen

- Incluye `#include <stdio.h>` para usar estas funciones.
- Usa `printf` para mostrar resultados mientras practicas.
