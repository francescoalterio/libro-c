printf("%s %d\n", p.nombre, p.edad);
d.i = 10;

# Estructuras y uniones en C

En C, las estructuras (`struct`) y uniones (`union`) permiten agrupar varios datos bajo un mismo nombre, pero funcionan de forma diferente a los objetos en JavaScript.

## struct

Una estructura es un conjunto de variables (campos) agrupadas bajo un mismo tipo. Es útil para modelar entidades complejas.

```c
struct Persona {
    char nombre[20];
    int edad;
};

struct Persona p = {"Ana", 30};
printf("%s %d\n", p.nombre, p.edad);
```

- Los campos pueden ser de distintos tipos.
- El acceso a los campos se hace con el operador `.`

> A diferencia de JS, no puedes agregar ni quitar campos dinámicamente.

## union

Una unión permite almacenar diferentes tipos de datos en la misma posición de memoria, pero solo uno a la vez. Todos los miembros comparten el mismo espacio.

```c
union Dato {
    int i;
    float f;
};

union Dato d;

```

> Útil para ahorrar memoria cuando solo necesitas un valor a la vez.

## typedef

Permite crear alias de tipos para simplificar el código.

```c
typedef struct Persona Persona;
Persona p2;
```

## Estructuras y funciones

Puedes pasar estructuras a funciones por valor (se copia toda la estructura) o por puntero (se pasa la dirección, más eficiente y permite modificar el original):

```c
struct Persona {
    char nombre[20];
    int edad;
};

void imprimir(struct Persona p) { // por valor
    printf("%s %d\n", p.nombre, p.edad);
}

void envejecer(struct Persona *p) { // por puntero
    p->edad++;
}
```

## Arreglos de estructuras

Puedes crear arreglos de estructuras para manejar colecciones de datos complejos:

```c
struct Persona personas[2] = {
    {"Ana", 30},
    {"Luis", 25}
};
printf("%s\n", personas[1].nombre); // Luis
```

## Apuntadores a estructuras

Puedes usar punteros a estructuras y el operador `->` para acceder a sus campos:

```c
struct Persona p = {"Ana", 30};
struct Persona *ptr = &p;
printf("%s %d\n", ptr->nombre, ptr->edad);
```

## Estructuras autorreferenciadas

Una estructura puede contener un puntero a su propio tipo, lo que permite crear listas, árboles, etc.:

```c
struct Nodo {
    int valor;
    struct Nodo *siguiente;
};
```

## Búsqueda en tablas (arreglos de estructuras)

Puedes buscar en un arreglo de estructuras usando un bucle:

```c
int buscarPorEdad(struct Persona arr[], int n, int edad) {
    for (int i = 0; i < n; i++) {
        if (arr[i].edad == edad) return i;
    }
    return -1;
}
```

## Campos de bits

Puedes definir campos de bits dentro de una estructura para ahorrar memoria cuando solo necesitas unos pocos bits por campo:

```c
struct Bandera {
    unsigned int a:1;
    unsigned int b:3;
    unsigned int c:4;
};
```

> Los campos de bits son útiles para representar flags compactos o protocolos binarios.

## Comparación con objetos en JS

- No hay métodos ni herencia, solo agrupación de datos.
- No existen propiedades dinámicas ni prototipos.
- Las estructuras son estáticas y su tamaño es fijo en tiempo de compilación.
