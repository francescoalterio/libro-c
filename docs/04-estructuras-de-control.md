# Estructuras de control en C

Las estructuras de control permiten modificar el flujo de ejecución de tu programa, igual que en JavaScript, pero con una sintaxis más estricta y sin palabras reservadas como `else if` (en C es `else if`, no `elseif`).

## Condicionales

### if, else if, else

Permiten ejecutar bloques de código según una condición. La sintaxis es muy parecida a JS, pero siempre debes usar paréntesis y llaves (aunque sea una sola línea, es buena práctica).

```c
int edad = 20;
if (edad >= 18) {
    printf("Eres mayor de edad\n");
} else if (edad > 0) {
    printf("Eres menor de edad\n");
} else {
    printf("Edad no válida\n");
}
```

> En C, cualquier valor distinto de 0 es considerado verdadero. 0 es falso.

### switch

Permite comparar una variable contra varios valores posibles. Es útil cuando tienes muchas opciones. A diferencia de JS, los casos deben ser valores constantes (no expresiones).

```c
int opcion = 2;
switch (opcion) {
    case 1:
        printf("Uno\n");
        break;
    case 2:
        printf("Dos\n");
        break;
    default:
        printf("Otra opcion\n");
}
```

> ⚠️ Si olvidas el `break`, la ejecución continúa con el siguiente caso (fallthrough).

### Operador ternario

Permite escribir condicionales simples en una sola línea, igual que en JS.

```c
int a = 5, b = 8;
int max = (a > b) ? a : b;
printf("El mayor es %d\n", max);
```

## Bucles

Los bucles permiten repetir instrucciones. La sintaxis es muy similar a JS, pero recuerda que en C debes declarar el tipo de la variable de control.

### for

```c
for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}
```

### while

```c
int i = 0;
while (i < 5) {
    printf("%d\n", i);
    i++;
}
```

### do-while

El bucle se ejecuta al menos una vez, porque la condición se evalúa al final.

```c
int i = 0;
do {
    printf("%d\n", i);
    i++;
} while (i < 5);
```

### break y continue

- `break` sale del bucle inmediatamente.
- `continue` salta a la siguiente iteración del bucle.

> Consejo: Usa bucles para recorrer arreglos, pedir datos al usuario, repetir cálculos, etc.
> int i = 0;
> do {

    printf("%d\n", i);
    i++;

} while (i < 5);

````

### break y continue

- `break` sale del bucle
- `continue` salta a la siguiente iteración

## goto y etiquetas

El uso de `goto` permite saltar a una etiqueta definida en el código. No se recomienda su uso salvo en casos muy específicos (por ejemplo, para salir de bucles anidados), ya que puede dificultar la lectura y el mantenimiento del código.

```c
goto fin;
printf("Esto no se ejecuta\n");
fin:
printf("Fin del programa\n");
````

> Evita usar `goto` salvo que sea estrictamente necesario.

## Recursividad

Una función es recursiva si se llama a sí misma. Es útil para problemas que pueden dividirse en subproblemas similares (como factorial, Fibonacci, recorridos de árboles, etc.).

```c
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

> En C, la recursividad es posible pero debes tener cuidado con el consumo de memoria (stack overflow).
