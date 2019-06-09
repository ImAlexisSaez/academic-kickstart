---
title: 67. La función filter
linktitle: 67. Filter
toc: true
type: docs
date: "2019-06-08T00:00:01+01:00"
lastmod: "2019-06-08T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 67

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 67
---

## Vídeo

{{< youtube mTJKU7IxL0U >}}

## Notas personales

En esta lección, estudiaremos la función `filter()`, que forma parte de un conjunto de funciones conocidas como ''de orden superior'' y nos permiten utilizar en *Python* el paradigma de **programación funcional**. La mencionada función verifica que los elementos de una secuencia cumplen una condición, devolviendo un iterador compuesto por aquellos que la satisfacen.

Por ejemplo, podemos construir un programa que detecte qué números son pares y cuáles no lo son, devolviéndonos una lista compuesta por los que verifiquen dicha condición:

```python
def numero_par(num):
    if num % 2 == 0:
        return True


numeros = [17, 24, 7, 39, 8, 51, 92]

print(filter(numero_par, numeros))  # objeto iterable

print(list(filter(numero_par, numeros)))
```

```bash
<filter object at 0x0000029E5BA262B0>
[24, 8, 92]
```

La función `numero_par()` la podemos abreviar un tanto como sigue:

```python
def numero_par(num):
    return num % 2 == 0
```

Es más, como es tan sencilla, incluso podemos prescindir de ella utilizando una función *lambda*:

```python
numeros = [17, 24, 7, 39, 8, 51, 92]

print(list(filter(lambda x: x % 2 == 0, numeros)))
```

```bash
[24, 8, 92]
```

Habitualmente, utilizaremos la función `filter()` para filtrar objetos. Por ejemplo, supongamos que tenemos varias instancias de la clase `Empleado` y deseamos filtrarlas por el valor de uno de sus atributos:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 75000),
    Empleado("Ana", "Presidenta", 85000),
    Empleado("Antonio", "Administrativo", 25000),
    Empleado("Sara", "Secretaria", 27000),
    Empleado("Mario", "Botones", 21000)
]

salarios_altos = filter(lambda e: e.salario > 50000, lista_empleados)

[print(s.__str__()) for s in salarios_altos]
```

```bash
Juan trabaja como Director y cobra 75000 €.
Ana trabaja como Presidenta y cobra 85000 €.
```

A modo de curiosidad, ya que me he avanzado y he utilizado comprensiones de listas (ver la última línea del bloque de código anterior), resulta que mediante ellas, en este ejemplo concreto, no es necesario recurrir al uso de la función `filter()`:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 75000),
    Empleado("Ana", "Presidenta", 85000),
    Empleado("Antonio", "Administrativo", 25000),
    Empleado("Sara", "Secretaria", 27000),
    Empleado("Mario", "Botones", 21000)
]

[print(e.__str__()) for e in lista_empleados if e.salario > 50000]
```

```bash
Juan trabaja como Director y cobra 75000 €.
Ana trabaja como Presidenta y cobra 85000 €.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/67/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
