# Introducción a C

C es un lenguaje de programación de propósito general, creado en los años 70. Es conocido por su eficiencia, cercanía al hardware y por ser la base de muchos otros lenguajes modernos (como C++, Java, Go, entre otros).

## ¿Por qué aprender C?

- Permite entender cómo funciona la memoria y el sistema operativo.
- Es ampliamente usado en sistemas embebidos, sistemas operativos y software de alto rendimiento.
- Te da control total sobre el hardware y los recursos.

## Diferencias clave con JavaScript

- C es compilado, no interpretado.
- No tiene recolección automática de basura (garbage collector).
- El manejo de memoria es manual.
- No existen objetos ni clases nativos (aunque puedes usar `struct`).

## Compilar y ejecutar un programa

Para compilar un archivo llamado `programa.c`:

```sh
gcc programa.c -o programa.exe
```

Para ejecutarlo en Windows:

```sh
./programa.exe
```

En Linux o MacOS:

```sh
./programa
```

Puedes usar `printf` para mostrar información en pantalla (lo veremos en detalle en el siguiente tema).
