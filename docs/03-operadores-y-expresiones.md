# Operadores y expresiones en C

En C, los operadores funcionan de manera similar a otros lenguajes como JavaScript, pero hay diferencias importantes en la sintaxis, los tipos de datos y el comportamiento. Entender bien los operadores es clave para escribir código correcto y eficiente.

## Constantes: const y #define

Puedes definir constantes de dos formas:

- `#define` crea una constante de preprocesador (no tiene tipo, solo reemplazo de texto):

  ```c
  #define PI 3.1416
  ```

- `const` crea una variable cuyo valor no puede cambiar (sí tiene tipo):

  ```c
  const int diasSemana = 7;
  ```

> Usa `const` para variables con tipo y alcance, y `#define` para valores globales o macros.

## Operadores aritméticos

Permiten realizar operaciones matemáticas básicas. Son casi idénticos a los de JavaScript, pero debes tener cuidado con los tipos de datos (por ejemplo, la división entre enteros descarta la parte decimal).

- `+` suma
- `-` resta
- `*` multiplicación
- `/` división (si ambos operandos son enteros, el resultado será entero)
- `%` módulo (resto de la división entera)

```c
int a = 10, b = 3;
printf("%d\n", a + b); // 13
printf("%d\n", a % b); // 1
printf("%f\n", 10.0 / 3); // 3.333333 (división flotante)
```

> ⚠️ En C, si divides dos enteros, el resultado siempre es entero. Por ejemplo, `5 / 2` da `2`, no `2.5`.

## Operadores de incremento y decremento

Permiten aumentar o disminuir el valor de una variable en 1. Son idénticos a los de JavaScript, pero en C es más común verlos en bucles y expresiones compactas.

- `++` incremento
- `--` decremento

```c
int x = 5;
x++; // x ahora vale 6
--x; // x vuelve a 5
```

> Puedes usar `x++` (post-incremento) o `++x` (pre-incremento). La diferencia importa cuando usas el valor en la misma expresión.

## Conversiones de tipo (casting)

En C, puedes convertir tipos de forma implícita (automática) o explícita (forzada):

- Conversión implícita: ocurre cuando mezclas tipos compatibles.

  ```c
  int a = 5;
  double b = a; // a se convierte a double automáticamente
  ```

- Conversión explícita (casting): usas el tipo entre paréntesis para forzar la conversión.

  ```c
  int a = 5;
  double b = (double)a / 2; // b = 2.5
  ```

> ⚠️ El casting es útil para evitar errores de precisión o para trabajar con punteros y memoria.

## Operadores relacionales

Sirven para comparar valores. Devuelven 1 (verdadero) o 0 (falso), no `true` o `false` como en JS.

- `==` igual a
- `!=` distinto de
- `>` mayor que
- `<` menor que
- `>=` mayor o igual
- `<=` menor o igual

```c
int x = 5;
printf("%d\n", x == 5); // 1
printf("%d\n", x != 5); // 0
```

## Operadores lógicos

Permiten combinar condiciones. En C, cualquier valor distinto de 0 es considerado verdadero.

- `&&` AND lógico (ambas condiciones verdaderas)
- `||` OR lógico (al menos una verdadera)
- `!` NOT lógico (niega la condición)

```c
int a = 1, b = 0;
if (a && !b) {
    printf("Se cumple la condición\n");
}
```

## Operadores de asignación

Sirven para asignar valores a variables. Puedes combinarlos con operadores aritméticos.

- `=` asignación simple
- `+=`, `-=`, `*=`, `/=`, `%=` (igual que en JS)

```c
int x = 5;
x += 2; // x ahora vale 7
```

## Operadores bit a bit

Permiten manipular los bits individuales de los números enteros. Son menos usados en JS, pero muy comunes en C para programación de bajo nivel.

- `&` AND bit a bit
- `|` OR bit a bit
- `^` XOR bit a bit
- `~` NOT bit a bit
- `<<` desplazamiento a la izquierda
- `>>` desplazamiento a la derecha

```c
int x = 5; // 0101 en binario
int y = x << 1; // 1010 (10 en decimal)
```

> ℹ️ Los operadores bit a bit son útiles para manipular flags, máscaras y trabajar con hardware.

## Precedencia y asociatividad

La precedencia determina qué operador se evalúa primero en una expresión. Es similar a JS, pero siempre es recomendable usar paréntesis para evitar errores y mejorar la legibilidad.

```c
int x = 2 + 3 * 4; // x = 14 (primero * luego +)
int y = (2 + 3) * 4; // y = 20
```

> Consejo: Si tienes dudas sobre el orden de evaluación, usa paréntesis.
