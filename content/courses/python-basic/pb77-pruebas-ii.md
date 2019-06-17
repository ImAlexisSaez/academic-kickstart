---
title: 77. Pruebas II
linktitle: 77. Pruebas II
toc: true
type: docs
date: "2019-06-17T00:00:01+01:00"
lastmod: "2019-06-17T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 77

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 77
---

## Vídeo

{{< youtube 64v9X7K-iuc >}}

## Notas personales

En esta lección, continuaremos el estudio de las pruebas que realizamos utilizando la documentación, pero incrementando un tanto su complejidad (con expresiones anidadas), para así ver las opciones que nos plantea el módulo `doctest`.

Para empezar, partamos del siguiente código fuente, que no es todo lo eficiente que debería, pero que cumple su propósito a efectos metodológicos para ilustrar pruebas con expresiones anidadas:

```python
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.
    """
    return [math.sqrt(n) for n in lista_numeros]


print(raiz_cuadrada([1, 4, 9, 16]))
```

```bash
[1.0, 2.0, 3.0, 4.0]
```

A continuación, para diseñar una prueba que contenta estructuras complejas como condicionales o bucles, simplemente hemos de utilizar `...` apropiadamente para anidar instrucciones:

```python
import doctest
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.

    >>> lista = []
    >>> for i in [4, 9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    [2.0, 3.0, 4.0]
    """
    return [math.sqrt(n) for n in lista_numeros]


doctest.testmod()
```

Acto seguido, analicemos cómo implementar pruebas que arrojen excepciones. Por ejemplo, incluyamos un elemento negativo en la lista que pasamos como argumento a la función `raiz_cuadrada()`:

```python
print(raiz_cuadrada([4, -9, 16]))
```

```bash
Traceback (most recent call last):
  File "pruebas_2.py", line 27, in <module>
    print(raiz_cuadrada([4, -9, 16]))
  File "pruebas_2.py", line 22, in raiz_cuadrada
    return [math.sqrt(n) for n in lista_numeros]
  File "pruebas_2.py", line 22, in <listcomp>
    return [math.sqrt(n) for n in lista_numeros]
ValueError: math domain error
```

No obstante, para diseñar una prueba que contemple el uso de número negativos en general (y no el de esta lista en concreto), utilizaremos `...` y nos quedaremos únicamente con la primera y última línea de la excepción arrojada arriba:

```python
import doctest
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.

    >>> lista = []
    >>> for i in [4, 9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    [2.0, 3.0, 4.0]

    >>> lista = []
    >>> for i in [4, -9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    Traceback (most recent call last):
    ...
    ValueError: math domain error
    """
    return [math.sqrt(n) for n in lista_numeros]


doctest.testmod()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/77/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

