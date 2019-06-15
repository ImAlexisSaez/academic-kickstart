---
title: 75. Documentación
linktitle: 75. Documentación
toc: true
type: docs
date: "2019-06-15T00:00:01+01:00"
lastmod: "2019-06-15T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 75

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 75
---

## Vídeo

{{< youtube SJqANWdRG4I >}}

## Notas personales

En esta lección, estudiaremos cómo documentar nuestros programas, esto es, incluir comentarios en clases, métodos, módulos, etc., con el objetivo de facilitar el trabajo en equipo sobre todo; resultando especialmente útil cuando las aplicaciones son complejas.

Para empezar, tomemos como referencia este sencillo código, que contiene la definición de dos funciones y llamadas a estas:

```python
def area_cuadrado(lado):
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    return "El área del triángulo es: " + str(base * altura / 2.)


print(area_cuadrado(5))
print(area_triangulo(3, 6))
```

```bash
El área del cuadrado es: 25
El área del triángulo es: 9.0
```

A continuación, para documentarlas, tras su definición insertamos el comentario oportuno encerrado por una triple comilla. De esta manera, mediante el atributo `__doc__`, incluso podemos acceder a la documentación de una función en tiempo de ejecución:

```python
def area_cuadrado(lado):
    """Calcula el área de un cuadrado dado su lado."""
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    """Calcula el área de un triángulo dada su base y su altura."""
    return "El área del triángulo es: " + str(base * altura / 2.)


# print(area_cuadrado(5))
# print(area_triangulo(3, 6))

print(area_cuadrado.__doc__)
print(area_triangulo.__doc__)
```

```bash
Calcula el área de un cuadrado dado su lado.
Calcula el área de un triángulo dada su base y su altura.
```

Por otro lado, obtenemos el mismo resultado empleando la función `help()` que, además, nos ofrece acceso a la cabecera de la definición de la función y al módulo donde se encuentra:

```python
def area_cuadrado(lado):
    """Calcula el área de un cuadrado dado su lado."""
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    """Calcula el área de un triángulo dada su base y su altura."""
    return "El área del triángulo es: " + str(base * altura / 2.)


# print(area_cuadrado(5))
# print(area_triangulo(3, 6))

# print(area_cuadrado.__doc__)
# print(area_triangulo.__doc__)

help(area_cuadrado)
help(area_triangulo)
```

```bash
Help on function area_cuadrado in module __main__:

area_cuadrado(lado)
    Calcula el área de un cuadrado dado su lado.

Help on function area_triangulo in module __main__:

area_triangulo(base, altura)
    Calcula el área de un triángulo dada su base y su altura.
```

Ahora, modifiquemos ligeramente el código para generar una clase `Areas`, en cuyo interior se encuentren las dos anteriores funciones, y veamos cómo acceder a la documentación generada antes:

```python
class Areas:
    def area_cuadrado(lado):
        """Calcula el área de un cuadrado dado su lado."""
        return "El área del cuadrado es: " + str(lado * lado)

    def area_triangulo(base, altura):
        """Calcula el área de un triángulo dada su base y su altura."""
        return "El área del triángulo es: " + str(base * altura / 2.)


help(Areas.area_cuadrado)
help(Areas.area_triangulo)
```

```bash
Help on function area_cuadrado in module __main__:

area_cuadrado(lado)
    Calcula el área de un cuadrado dado su lado.

Help on function area_triangulo in module __main__:

area_triangulo(base, altura)
    Calcula el área de un triángulo dada su base y su altura.
```

Además, para obtener una documentación general de la clase basta teclear:

```python
help(Areas)
```

```bash
Help on class Areas in module __main__:

class Areas(builtins.object)
 |  Methods defined here:
 |  
 |  area_cuadrado(lado)
 |      Calcula el área de un cuadrado dado su lado.
 |  
 |  area_triangulo(base, altura)
 |      Calcula el área de un triángulo dada su base y su altura.
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
```

Finalmente, también podemos documentar la propia clase:

```python
class Areas:
    """Esta clase calcula las áreas de diferentes figuras geométricas."""
    def area_cuadrado(lado):
        """Calcula el área de un cuadrado dado su lado."""
        return "El área del cuadrado es: " + str(lado * lado)

    def area_triangulo(base, altura):
        """Calcula el área de un triángulo dada su base y su altura."""
        return "El área del triángulo es: " + str(base * altura / 2.)


help(Areas)
```

```bash
Help on class Areas in module __main__:

class Areas(builtins.object)
 |  Esta clase calcula las áreas de diferentes figuras geométricas.
 |  
 |  Methods defined here:
 |  
 |  area_cuadrado(lado)
 |      Calcula el área de un cuadrado dado su lado.
 |  
 |  area_triangulo(base, altura)
 |      Calcula el área de un triángulo dada su base y su altura.
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
```

*Nota*: utilizando esta misma estrategia, podemos documentar asimismo módulos.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/75/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

