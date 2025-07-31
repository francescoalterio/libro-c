# Entrada y salida con archivos en C

En C, la manipulación de archivos se realiza a través de la librería estándar `stdio.h`. A diferencia de JS (donde puedes usar módulos como `fs` en Node.js), aquí todo se hace con funciones y punteros a archivos.

## Abrir y cerrar archivos

Para trabajar con archivos, debes abrirlos con `fopen`, que devuelve un puntero de tipo `FILE*`. Siempre verifica que el archivo se haya abierto correctamente antes de usarlo.

```c
FILE *f = fopen("datos.txt", "r");
if (f == NULL) {
    printf("No se pudo abrir el archivo\n");
} else {
    // ... leer o escribir ...
    fclose(f);
}
```

> Si olvidas cerrar el archivo con `fclose`, puedes perder datos o bloquear recursos del sistema.

## Leer y escribir

Puedes escribir con `fprintf` (formato) o `fputs` (texto simple), y leer con `fscanf`, `fgets` o funciones de bajo nivel como `fread`/`fwrite` para binarios.

```c
FILE *f = fopen("datos.txt", "w");
if (f != NULL) {
    fprintf(f, "Hola archivo\n");
    fclose(f);
}
```

- `fopen`, `fclose`, `fprintf`, `fscanf`, `fread`, `fwrite`

> Consejo: Siempre revisa el valor de retorno de las funciones de lectura/escritura para detectar errores.

## Modos de apertura

- "r": solo lectura
- "w": solo escritura (sobrescribe)
- "a": solo agregar
- "rb", "wb", "ab": binario (lectura/escritura/agregar en modo binario)

## Diferencias con JavaScript

- En JS puedes manipular archivos de forma asíncrona y con promesas; en C todo es síncrono.
- En C, debes gestionar manualmente la apertura y cierre de archivos.
