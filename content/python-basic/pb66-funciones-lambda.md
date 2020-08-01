---
title: 66. Funciones lambda
linktitle: 66. Lambdas
toc: true
type: book
date: "2019-06-07T00:00:01+01:00"
lastmod: "2019-06-07T00:00:01+01:00"
draft: false
weight: 66
---

## Vídeo

{{< youtube tfYLcHbjc_A >}}

## Notas personales

En esta lección, estudiaremos las funciones *lambda*. Una función **lambda** es una función anónima, y se utilizan en *Python* a la hora de programar para abreviar, ya que aligera la sintaxis del código. Además, no ocupan lugar en el espacio de nombres asociado a las funciones de una aplicación.

Cualquier tarea que llevemos a cabo con una función *lambda* se puede desarrollar mediante una función normal, pero no así a la inversa (sobre todo cuando su lógica es compleja).

Por ejemplo, para calcular el área de un triángulo, podemos construir la función:

```python
def area_triangulo(b, h):
    return b * h / 2
```

```python
for b in range(1, 10, 5):
    for h in range(1, 10, 5):
        print(
            f"El área del triángulo de base {b} y altura {h} es {area_triangulo(b, h)}."
        )
```

```bash
El área del triángulo de base 1 y altura 1 es 0.5.
El área del triángulo de base 1 y altura 6 es 3.0.
El área del triángulo de base 6 y altura 1 es 3.0.
El área del triángulo de base 6 y altura 6 es 18.0.
```

No obstante, una función tan sencilla puede ser abreviada como una función *lambda*.

```python
area_triangulo = lambda b, h: b * h / 2

for b in range(1, 10, 5):
    for h in range(1, 10, 5):
        print(
            f"El área del triángulo de base {b} y altura {h} es {area_triangulo(b, h)}."
        )
```

```bash
El área del triángulo de base 1 y altura 1 es 0.5.
El área del triángulo de base 1 y altura 6 es 3.0.
El área del triángulo de base 6 y altura 1 es 3.0.
El área del triángulo de base 6 y altura 6 es 18.0.
```

*Nota*: las funciones *lambda*, generalmente, no se asignan a variables. En tales casos, conviene hacer uso de la instrucción `def` y definir una función tal y como estamos habituados.

Usadas ''al vuelo'', su sintaxis queda como sigue:

```python
print("El cubo de 3 es " + str((lambda x:x**3) (3)))
```

```bash
El cubo de 3 es 27
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/66/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
