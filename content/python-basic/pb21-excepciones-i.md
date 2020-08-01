---
title: 21. Excepciones I
linktitle: 21. Excepciones I
toc: true
type: book
date: "2019-05-06T00:01:01+01:00"
lastmod: "2019-05-06T00:01:01+01:00"
draft: false
weight: 21
---

## Vídeo

{{< youtube 2MaAs7XU2T0 >}}

## Notas personales

Una **excepción** es un error que acontece durante la ejecución de un programa. La sintaxis del código es correcta, pero, en el momento de ejecutarse el algoritmo, sucede ''algo inesperado''.

Para ilustrar la aparición de excepciones, trabajemos con el siguiente código:

```python
def suma(num1, num2):
    return num1 + num2


def resta(num1, num2):
    return num1 - num2


def multiplica(num1, num2):
    return num1 * num2


def divide(num1, num2):
    return num1 / num2


op1 = (int(input("Introduce el primer número: ")))
op2 = (int(input("Introduce el segundo número: ")))

print("Operaciones disponibles: ")
print("- Suma")
print("- Resta")
print("- Multiplica")
print("- Divide")

operacion = input("Introduce la operación a realizar: ")

if operacion == "Suma":
    print(suma(op1, op2))
elif operacion == "Resta":
    print(resta(op1, op2))
elif operacion == "Multiplica":
    print(multiplica(op1, op2))
elif operacion == "Divide":
    print(divide(op1, op2))
else:
    print("Operación no contemplada.")

print("Operación ejecutada. Continuación de ejecución del programa ")
```

Un posible ejemplo de ejecución sería:

```bash
Introduce el primer número: 16
Introduce el segundo número: 4
Operaciones disponibles: 
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Multiplica
64
Operación ejecutada. Continuación de ejecución del programa
```

Sin embargo, si por accidente intentamos realizar una división entre 0:

```bash
Introduce el primer número: 2
Introduce el segundo número: 0
Operaciones disponibles: 
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Divide
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 35, in <module>
    print(divide(op1, op2))
  File "prac21_excepciones1_1.py", line 14, in divide
    return num1 / num2
ZeroDivisionError: division by zero
```

De forma que el código se detiene en el preciso instante de la llamada a la función `divide()` y deja de ejecutar las restantes líneas (la instrucción `print()` final en esta ocasión), cuya importancia puede ser vital para nosotros.

Este tipo de situaciones se aborda mediante una **captura** o **control de excepción**. La idea es intentar realizar un bloque de código y, en el caso de no poderse llevar a cabo dicha acción, que al menos el resto de programa siga adelante.

Si nos fijamos en la **pila de llamadas** que nos muestran antes de arrojar el error:

```bash
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 35, in <module>
    print(divide(op1, op2))
  File "prac21_excepciones1_1.py", line 14, in divide
    return num1 / num2
ZeroDivisionError: division by zero
```

Leyendo de abajo hacia arriba, la instrucción `return num1 / num2`, ubicada en la línea 14 del código, arroja un error de división por cero (`ZeroDivisionError`). Para controlar esta circunstancia, usaremos un bloque de tipo:

```python
try:
    instrucciones
except error:
    instrucciones
```

Así, nuestra función `divide()` la podríamos reescribir como sigue:

```python
def divide(num1, num2):
    try:
        return num1 / num2
    except ZeroDivisionError:
        print("No se puede dividir entre 0.")
        return "Operación errónea."
```

De manera que, replicando el anterior conflictivo ejemplo:

```bash
Introduce el primer número: 2
Introduce el segundo número: 0
Operaciones disponibles: 
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Divide
No se puede dividir entre 0.
Operación errónea.
Operación ejecutada. Continuación de ejecución del programa 
```

Apreciamos que la última línea de código, aquel `print()` final, ahora efectivamente sí llega a ejecutarse.

Por desgracia, no es el único punto conflictivo que presenta el código mostrado. Por ejemplo, ¿qué sucede si introducimos una cadena de texto en lugar de un número?

```bash
Introduce el primer número: 3
Introduce el segundo número: a
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 22, in <module>
    op2 = (int(input("Introduce el segundo número: ")))
ValueError: invalid literal for int() with base 10: 'a'
```

*Python* arroja un error de tipo `ValueError` que también habríamos de controlar a través de un bloque `try` - `except`.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/21/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
