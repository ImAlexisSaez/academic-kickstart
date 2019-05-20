---
title: 35. Paquetes I
linktitle: 35. Paquetes I
toc: true
type: docs
date: "2019-05-12T00:00:02+01:00"
lastmod: "2019-05-12T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 35

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 35
---

## Vídeo

{{< youtube nRieWujis4s >}}

## Notas personales

Los **paquetes** son directorios donde se almacenarán módulos relacionados entre sí. Sirven para organizar el código de una aplicación y reutilizar los mencionados módulos.

Un paquete se crea generando un directorio en cuyo interior haya presente un archivo denominado `__init__.py`.

Imaginemos que nuestro objetivo es elaborar un programa que realice diversos cálculos matemáticos y estadísticos. Vamos a empezar creando un directorio denominado `calculos`, en consonancia con la nomenclatura que estamos siguiendo para los ficheros del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

En su interior creamos el mencionado archivo `__init__.py` (sin contenido alguno), acción que le transmite a *Python* la información de que la carpeta `calculos` funcionará como un paquete.

Añadimos ahora a la carpeta el módulo `calculos_generales.py`, cuyo contenido es el siguiente:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)


def dividir(dividendo, divisor):
    print("El resultado de la división es:", dividendo / divisor)


def potenciar(base, exponente):
    print("El resultado de la potenciación es:", base**exponente)


def redondear(numero):
    print("El resultado del redondeo es:", round(numero))
```

Ahora, desde la raíz del directorio, veamos cómo podemos utilizar nuestro paquete recién creado:

```python
from calculos.calculos_generales import dividir

dividir(10, 3)
```

```bash
El resultado de la división es: 3.3333333333333335
```

Recordemos que podemos importar todo el contenido del módulo utilizando el carácter `*`:

```python
from calculos.calculos_generales import *

dividir(10, 3)

redondear(4.6)

potenciar(2, 10)
```

```bash
El resultado de la división es: 3.3333333333333335
El resultado del redondeo es: 5
El resultado de la potenciación es: 1024
```

Podemos crear **subpaquetes**, esto es, un paquete dentro de otro, siguiendo de manera recursiva el procedimiento explicado.

Por ejemplo, para afinar un poco más, creemos dos directorios dentro de la carpeta del paquete, denominados `basicos` (para suma, resta, multiplicación y división) y `redondeo-potencia` (para redondear y calcular potencias). Cada una de ellas ha de llevar en su interior su correspondiente fichero `__init__.py`.

En la carpeta `basicos` incluimos el módulo `operaciones_basicas.py`, cuyo contenido será:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)


def dividir(dividendo, divisor):
    print("El resultado de la división es:", dividendo / divisor)
```

Mientras que en la carpeta `redondeo_potencia` generamos el módulo `redondea_y_potencia`, compuesto por el siguiente bloque de código:

```python
def potenciar(base, exponente):
    print("El resultado de la potenciación es:", base**exponente)


def redondear(numero):
    print("El resultado del redondeo es:", round(numero))
```

Para utilizar estos últimos módulos creados, tecleamos:

```python
from calculos.basicos.operaciones_basicas import sumar
from calculos.redondeo_potencia.redondea_y_potencia import potenciar

sumar(5, 7)
potenciar(2, 10)
```

```bash
El resultado de la suma es: 12
El resultado de la potenciación es: 1024
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/35/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

