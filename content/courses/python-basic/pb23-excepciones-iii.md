---
title: 23. Excepciones III
linktitle: 23. Excepciones III
toc: true
type: docs
date: "2019-05-07T00:00:01+01:00"
lastmod: "2019-05-07T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 23

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 23
---

## Vídeo

{{< youtube dLH-oay4Bts >}}

## Notas personales

Estudiemos cómo lanzar excepciones, de forma intencionada, a través de la instrucción `raise`. Veremos su utilidad cuando trabajemos, más adelante, con clases.

Generemos un sencillo programa cuyo objetivo sea evaluar nuestra edad:

```python
def evalua_edad(edad):
    if edad < 20:
        return "Eres muy joven."
    elif edad < 40:
        return "Eres joven."
    elif edad < 65:
        return "Eres maduro."
    elif edad < 100:
        return "Cuídate."


print(evalua_edad(18))  # Eres muy joven.
print(evalua_edad(70))  # Cuídate.
```

Sin embargo, la función así definida presenta este curioso comportamiento:

```python
print(evalua_edad(-15))  # Eres muy joven.
```

Evidentemente, podemos arreglar esta situación mediante estructuras condicionales, pero veremos a continuación cómo emplear la instrucción `raise` para abordar el presente caso.

```python
def evalua_edad(edad):
    if edad < 0:
        raise TypeError("No se permiten edades negativas.")
    if edad < 20:
        return "Eres muy joven."
    elif edad < 40:
        return "Eres joven."
    elif edad < 65:
        return "Eres maduro."
    elif edad < 100:
        return "Cuídate."


print(evalua_edad(18))
print(evalua_edad(70))
print(evalua_edad(-15))
```

Al ejecutar el anterior programa, obtenemos:

```bash
Eres muy joven.
Cuídate.
Traceback (most recent call last):
  File "prac23_excepciones3_2.py", line 16, in <module>
    print(evalua_edad(-15))
  File "prac23_excepciones3_2.py", line 3, in evalua_edad
    raise TypeError("No se permiten edades negativas.")
TypeError: No se permiten edades negativas.
```

*Nota*: hemos de usar alguno de los tipos de error disponibles en *Python*, no pdemos cualquier cadena de texto sin más ahí. No obstante, dicho esto, cuando generemos clases podremos elaborar también errores personalizados.

Pasemos a programar un algoritmo que calcule la raíz cuadrada de un número mayor o igual que cero:

```python
import math


def calcula_raiz(num):
    if num < 0:
        raise ValueError("El número no puede ser negativo.")
    else:
        return math.sqrt(num)


op = (int(input("Introduce un número mayor o igual que cero: ")))

print(calcula_raiz(op))

print("Programa terminado.")
```

Controlemos la excepción que aparece si introducimos un número negativo:

```python
import math


def calcula_raiz(num):
    if num < 0:
        raise ValueError("El número no puede ser negativo.")
    else:
        return math.sqrt(num)


op = (int(input("Introduce un número mayor o igual que cero: ")))

try:
    print(calcula_raiz(op))
except ValueError as ErrorDeNumeroNegativo:
    print(ErrorDeNumeroNegativo)

print("Programa terminado.")
```

Un par de ejecuciones del anterior programa, por ejemplo, podrían ser:

```bash
Introduce un número mayor o igual que cero: 144
12.0
Programa terminado.
```

```bash
Introduce un número mayor o igual que cero: -144
El número no puede ser negativo.
Programa terminado.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/23/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
