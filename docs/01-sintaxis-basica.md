# Sintaxis básica de C

Un programa en C siempre tiene una función principal llamada `main`. Todo el código comienza a ejecutarse desde ahí.

```c
#include <stdio.h>

int main() {
    // Esto es un comentario
    return 0;
}
```

## Declaración de variables

```c
int edad = 25;
float altura = 1.75;
char inicial = 'F';
```

- `int`: números enteros
- `float`: números decimales
- `char`: un solo carácter

## Variables globales, locales y reglas de alcance

- Una variable declarada fuera de cualquier función es global y accesible desde cualquier parte del archivo.
- Una variable declarada dentro de una función es local y solo existe dentro de esa función.
- El alcance de una variable puede ser restringido a un bloque `{}`.

```c
int global = 10; // global

void foo() {
    int local = 5; // local
    {
        int bloque = 2; // solo existe en este bloque
    }
}
```

## Variables externas (extern)

Puedes declarar una variable en un archivo y usarla en otro con la palabra clave `extern`:

```c
// archivo1.c
int contador = 0;

// archivo2.c
extern int contador;
```

## Variables estáticas (static)

- Una variable local `static` mantiene su valor entre llamadas a la función.
- Una variable global `static` solo es visible en el archivo donde se declara.

```c
void ejemplo() {
    static int veces = 0;
    veces++;
    printf("Llamada número %d\n", veces);
}
```

## Variables tipo registro (register)

La palabra clave `register` sugiere al compilador que almacene la variable en un registro de CPU para acceso rápido (hoy en día rara vez es necesario usarla):

```c
register int rapido = 0;
```

## Tip: Siempre termina las instrucciones con `;` (punto y coma).

En C, los bloques de código se delimitan con llaves `{}` igual que en JavaScript.
