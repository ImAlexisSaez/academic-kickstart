---
title: 20. Generadores II
linktitle: 20. Generadores II
toc: false
type: docs
date: "2019-05-05T00:03:01+01:00"
lastmod: "2019-05-05T00:03:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 20

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 20
---

## Vídeo

{{< youtube ucaHqGII350 >}}

## Notas personales

Estudiemos el uso de la instrucción `yield from`, cuya utilidad reside en la simplificación del código de los generadores en el caso de utilizar bucles anidados.

Por ejemplo, elaboremos un generador que nos devuelva ciudades:

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        yield elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # Madrid

print(next(ciudades_devueltas))  # Barcelona
```

*Nota*: en *Python*, cuando colocamos un `*` delante de un parámetro, estamos indicando que podemos pasar un número indeterminado de argumentos, que los recibirá en forma de tupla.

Imaginemos que ahora deseamos acceder a los elementos de cada una de las ciudades (sus letras en este caso):

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        for sub_elemento in elemento:
            yield sub_elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # M

print(next(ciudades_devueltas))  # a
```

El anterior ejemplo lo podemos simplificar utilizando la instrucción `yield from`:

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        yield from elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # M

print(next(ciudades_devueltas))  # a
```
