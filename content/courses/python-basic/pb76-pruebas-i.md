---
title: 76. Pruebas I
linktitle: 76. Pruebas I
toc: true
type: docs
date: "2019-06-16T00:00:01+01:00"
lastmod: "2019-06-16T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 76

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 76
---

## Vídeo

{{< youtube BUNEkSFlmys >}}

## Notas personales

En esta lección, analizaremos cómo realizar pruebas, utilizando la documentación para ello. Esta forma de proceder la podemos llevar a cabo con el módulo `doctest` de *Python*.

Para empezar, partamos de este sencillo código, que contiene una función que calcula el área del triángulo dada su base y su altura:

```python
def area_triangulo(base, altura):
    return base * altura / 2.


print(area_triangulo(2, 4))
```

```bash
4.0
```

A continuación, documentemos la función `area_triangulo()` siguiendo el procedimiento visto en la lección anterior e incluyamos ahí nuestra primera prueba (antecediéndola mediante `>>>`). Luego, una vez importado el módulo `doctest`, incluimos la instrucción `doctest.testmod()`:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    9.0

    """
    return base * altura / 2.


doctest.testmod()
```

Al ejecutar el anterior bloque de código, no observamos respuesta alguna en la consola de *Python*, lo cual es una buena señal, pues significa que se han superado los tests planteados sin encontrar ningún problema.

Ahora, imaginemos que nos hemos equivocado escribiendo el test (también valdría modificando la expresión que devuelve la instrucción `return`) y decimos que ha de resultar `8.0` el área de un triángulo de base `3` y altura `6`:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    8.0

    """
    return base * altura / 2.


doctest.testmod()
```

```bash
**********************************************************************
File "pruebas_2.py", line 8, in __main__.area_triangulo
Failed example:
    area_triangulo(3, 6)
Expected:
    8.0
Got:
    9.0
**********************************************************************
1 items had failures:
   1 of   1 in __main__.area_triangulo
***Test Failed*** 1 failures.
```

Acto seguido, compliquemos ligeramente el ejemplo y hagamos que la función `area_triangulo()` devuelva una cadena de caracteres en lugar de un valor numérico. Ello implica redactar con cuidado la prueba:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    'El área del triángulo es 9.0'

    """
    return "El área del triángulo es " + str(base * altura / 2.)


doctest.testmod()
```

*Nota*: hemos de proceder con cautela porque, en esta ocasión, las comillas `'` y `"` no son intercambiables.

Obviamente, tenemos la posibilidad de realizar varias pruebas:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    'El área del triángulo es 9.0'

    >>> area_triangulo(2, 4)
    'El área del triángulo es 4.0'

    >>> area_triangulo(4, 5)
    'El área del triángulo es 10.0'

    """
    return "El área del triángulo es " + str(base * altura / 2.)


doctest.testmod()
```

No obstante, llevar a cabo múltiples pruebas tiene sentido cuando la complejidad del código se incrementa. Recordemos el código que generamos para comprobar si una dirección de correo electrónico era correcta en función de si presentaba o no el carácter `@`:

```python
import doctest


def check_mail(mail_user):
    """
    Evalúa un mail recibido en busca de @.
    Si tiene una @ es correcto.
    Si tiene más de una @ es incorrecto.
    Si la @ está al final es incorrecto.

    >>> check_mail("alexis@cursos.es")
    True

    >>> check_mail("alexiscursos.es@")
    False

    >>> check_mail("alexis.cursos.es")
    False

    >>> check_mail("alexis@cursos@es")
    False
    """

    arroba = mail_user.count("@")
    return not (arroba != 1 or mail_user.rfind('@') == len(mail_user) - 1)


doctest.testmod()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/76/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

