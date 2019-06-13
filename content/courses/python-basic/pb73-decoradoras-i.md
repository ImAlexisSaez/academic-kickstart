---
title: 73. Decoradoras I
linktitle: 73. Decoradoras I
toc: true
type: docs
date: "2019-06-13T00:00:02+01:00"
lastmod: "2019-06-13T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 73

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 73
---

## Vídeo

{{< youtube DQXm6bIZgvk >}}

## Notas personales

En esta lección, introduciremos el uso de las **decoradoras** (o *funciones decoradoras*), que son funciones que añaden ciertos comportamientos a otras (de ahí el nombre, puesto que las ''decoran'' incorporando funcionalidades adicionales).

La estructura de una decoradora, de forma abstracta, es la siguiente:

- Son tres funciones (`A`, `B` y `C`), donde `A` recibe como parámetro a `B` para devolver `C`.
- Esto es, una decoradora devuelve siempre una función.

Su sintaxis queda como sigue:

```python
def funcion_decoradora(funcion):  # funcion_A(funcion_B)
    def funcion_interna():        # funcion_C
        # codigo funcion interna
    return funcion_interna
```

Veamos su aplicación práctica mediante un ejemplo muy sencillo, en el que la utilidad de la decoradora será casi nula y nos servirá únicamente para comprender su funcionamiento, sin añadir excesiva complejidad al código fuente.

En primer lugar, tecleamos:

```python
def suma():
    print(15 + 20)


def resta():
    print(30 - 10)


suma()
resta()
```

```bash
35
20
```

Acto seguido, supongamos que deseamos añadir a todas las funciones cierto comportamiento adicional. Para ello, podemos acudir a su código y modificarlas una por una (en este ejemplo son dos, pero imaginemos un caso donde hubiera cientos de funciones) o utilizar una decoradora:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior():
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro()
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

A continuación, para añadir el decorador a cualquiera de las funciones ya previamente existentes, escribimos:

```python
@funcion_decoradora
def suma():
    print(15 + 20)


def resta():
    print(30 - 10)


suma()
resta()
```

```bash
Vamos a realizar un cálculo: 
35
Hemos terminado el cálculo.
20
```

Notemos cómo el decorador solo afecta a la función `suma()`, pues así lo hemos declarado arriba. Bastaría replicar la estrategia para decorar asimismo la función `resta()`.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/73/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
