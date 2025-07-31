# Punteros en C

Los punteros son uno de los conceptos más poderosos y complejos de C. Un puntero es una variable que almacena la dirección de memoria de otra variable. Esto permite manipular directamente la memoria, crear estructuras dinámicas y pasar datos por referencia.

En JavaScript no existen punteros explícitos, pero en C son fundamentales para trabajar con arreglos, strings, memoria dinámica y funciones.

printf("%d\n", \*p); // accede al valor de x

## Declaración y uso

Para declarar un puntero, usa el operador `*`. Para obtener la dirección de una variable, usa `&`.

```c
int x = 10;
int *p = &x; // p apunta a x
printf("%d\n", *p); // accede al valor de x (desreferenciación)
```

- `*` se usa para declarar y desreferenciar punteros
- `&` obtiene la dirección de una variable

> ⚠️ Usar un puntero sin inicializar o apuntando a memoria inválida puede causar errores graves (segmentation fault).

printf("%d\n", \*(p+1)); // 2

## Punteros y arreglos

En C, el nombre de un arreglo es en realidad un puntero al primer elemento. Puedes recorrer un arreglo usando aritmética de punteros:

```c
int arr[3] = {1, 2, 3};
int *p = arr;
printf("%d\n", *(p+1)); // 2
```

> Consejo: Los punteros permiten recorrer y modificar arreglos de forma eficiente.

printf("%d\n", pf(2, 3)); // 5

## Punteros a funciones

Puedes almacenar la dirección de una función en un puntero y llamarla indirectamente. Esto es útil para callbacks y estructuras de datos avanzadas.

```c
int suma(int a, int b) { return a + b; }
int (*pf)(int, int) = suma;
printf("%d\n", pf(2, 3)); // 5
```

## Punteros como argumentos de funciones

Puedes pasar punteros como argumentos a funciones para modificar el valor original de una variable (paso por referencia). Esto es fundamental para manipular datos fuera del alcance local de la función.

```c
void incrementar(int *n) {
    (*n)++;
}

int main() {
    int x = 5;
    incrementar(&x);
    printf("%d\n", x); // 6
    return 0;
}
```

> Así puedes modificar variables fuera de la función, algo que en JS ocurre automáticamente con objetos y arrays.

## Aritmética de punteros

Puedes sumar o restar enteros a un puntero para moverlo a través de un arreglo. El incremento depende del tamaño del tipo apuntado.

```c
int arr[3] = {10, 20, 30};
int *p = arr;
printf("%d\n", *p);     // 10
p++;
printf("%d\n", *p);     // 20
```

> Sumar 1 a un puntero a int lo mueve al siguiente entero, no al siguiente byte.

## Punteros a caracteres (strings)

Un string en C es un puntero a char. Puedes manipular cadenas usando punteros:

```c
char mensaje[] = "Hola";
char *p = mensaje;
printf("%c\n", *p);     // H
p++;
printf("%c\n", *p);     // o
```

También puedes recorrer cadenas con punteros:

```c
for (char *c = mensaje; *c != '\0'; c++) {
    printf("%c ", *c);
}
```

## Arreglos de punteros y punteros a punteros

Puedes tener arreglos cuyos elementos son punteros, o punteros que apuntan a otros punteros.

### Arreglo de punteros

```c
const char *dias[] = {"Lunes", "Martes", "Miércoles"};
printf("%s\n", dias[1]); // Martes
```

### Punteros a punteros

```c
int x = 10;
int *p = &x;
int **pp = &p;
printf("%d\n", **pp); // 10
```

> Los punteros a punteros son útiles para manejar matrices dinámicas y argumentos de la función main (`char **argv`).

## Punteros y arreglos multidimensionales

Un arreglo multidimensional (como una matriz) es en realidad un arreglo de arreglos. Puedes acceder a sus elementos usando punteros:

```c
int matriz[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
int *p = &matriz[0][0];
printf("%d\n", *(p + 4)); // 5 (accede al elemento [1][1])
```

También puedes usar punteros a arreglos:

```c
int (*fila)[3] = matriz;
printf("%d\n", fila[1][2]); // 6
```

> Los punteros permiten recorrer matrices de forma eficiente, pero debes tener cuidado con el orden y el tamaño de cada dimensión.

## Argumentos en línea de órdenes (main y argv)

Puedes recibir argumentos desde la línea de comandos usando la forma extendida de `main`:

```c
int main(int argc, char *argv[]) {
    printf("Cantidad de argumentos: %d\n", argc);
    for (int i = 0; i < argc; i++) {
        printf("Argumento %d: %s\n", i, argv[i]);
    }
    return 0;
}
```

- `argc` es el número de argumentos.
- `argv` es un arreglo de punteros a char (strings).

## Declaraciones complicadas

En C puedes tener declaraciones complejas combinando punteros, arreglos y funciones. Aquí algunos ejemplos y cómo leerlos:

```c
int *a[5];      // arreglo de 5 punteros a int
int (*b)[5];    // puntero a un arreglo de 5 int
int *(*c[3])(); // arreglo de 3 punteros a funciones que devuelven int*
int (*d())[];   // función que devuelve un puntero a un arreglo de int
```

> Consejo: Lee las declaraciones de adentro hacia afuera y usa paréntesis para aclarar la precedencia.

## Diferencias con referencias en JS

- En C, los punteros son explícitos y pueden manipular memoria directamente.
- En JS, las referencias son automáticas y seguras, pero no puedes acceder a la memoria directamente.

> Aprender punteros te dará una comprensión profunda de cómo funciona la memoria y el paso de datos en C.
