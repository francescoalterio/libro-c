# Funciones en C

Las funciones en C te permiten dividir tu código en bloques reutilizables, igual que en JavaScript, pero con una sintaxis más estricta y sin soporte para funciones anidadas ni closures. Son fundamentales para estructurar programas grandes y evitar repetir código.

## Declaración y definición

En C, primero debes declarar el tipo de retorno, el nombre y los parámetros de la función. Puedes declarar la función antes de `main` o solo su prototipo (firma) y luego definirla después.

```c
// Declaración (prototipo)
int sumar(int a, int b);

// Definición
int sumar(int a, int b) {
    return a + b;
}

int main() {
    int resultado = sumar(2, 3);
    printf("%d\n", resultado);
    return 0;
}
```

> En C, todas las funciones deben tener un tipo de retorno explícito. Si no devuelven nada, usa `void`.

## Paso de argumentos

Por defecto, los argumentos se pasan por valor (se copia el dato). Si quieres modificar el valor original, debes pasar un puntero (la dirección de memoria):

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

> En JS, los objetos y arrays se pasan por referencia. En C, todo se pasa por valor, salvo que uses punteros.

## Valor de retorno

Usa `return` para devolver un valor. Si la función no retorna nada, declara el tipo como `void`.

```c
void saludar() {
    printf("Hola!\n");
}
```

## Ámbito de variables

- Variables locales: solo existen dentro de la función donde se declaran.
- Variables globales: declaradas fuera de cualquier función, accesibles desde cualquier parte del archivo.

> Consejo: Evita el uso de variables globales salvo que sea estrictamente necesario.

## Diferencias con JavaScript

- No existen funciones anidadas ni funciones flecha.
- No hay closures ni contexto de this.
- No puedes retornar múltiples valores directamente (usa punteros o structs para eso).
