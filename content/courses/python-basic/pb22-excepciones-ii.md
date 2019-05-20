---
title: 22. Excepciones II
linktitle: 22. Excepciones II
toc: true
type: docs
date: "2019-05-06T00:02:01+01:00"
lastmod: "2019-05-06T00:02:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 22

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 22
---

## Vídeo

{{< youtube HH3c6ZBvSx8 >}}

## Notas personales

Recordemos el código final de la lección anterior:

```python
def suma(num1, num2):
    return num1 + num2


def resta(num1, num2):
    return num1 - num2


def multiplica(num1, num2):
    return num1 * num2


def divide(num1, num2):
    try:
        return num1 / num2
    except ZeroDivisionError:
        print("No se puede dividir entre 0.")
        return "Operación errónea."


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

print("Operación ejecutada. Continuación de ejecución del programa.")
```

No obstante, este código es susceptible de presentar más errores. Por ejemplo, introduciendo una cadena de texto en lugar de un número cuando nos solicitan los datos.

Para solucionar ese detalle, podemos reescribir el correspondiente bloque de código como sigue:

```python
try:
    op1 = (int(input("Introduce el primer número: ")))
    op2 = (int(input("Introduce el segundo número: ")))
except ValueError:
    print("Los valores introducidos no son correctos.")
```

El programa así modificado, presenta errores de lógica ahora, ya que si introducimos una cadena de texto como dato, *Python* no arroja error, pero continua la ejecución del programa y al intentar llevar a cabo cualquier operación de las disponibles, lanza un error de tipo `NameError`:

```bash
Introduce el primer número: 5
Introduce el segundo número: a
Los valores introducidos no son correctos.
Operaciones disponibles: 
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Suma
Traceback (most recent call last):
  File "prac22_excepciones2_1.py", line 36, in <module>
    print(suma(op1, op2))
NameError: name 'op2' is not defined
```

Una manera de abordar esta problemática es mediante un bucle infinito de tipo `while`, forzando que el usuario introduzca valores admisibles para continuar la ejecución del programa:

```python
while True:
    try:
        op1 = (int(input("Introduce el primer número: ")))
        op2 = (int(input("Introduce el segundo número: ")))
        break
    except ValueError:
        print("Los valores introducidos no son correctos. Inténtalo de nuevo.")
```

Siendo una posible ejecución del programa la que se muestra acto seguido:

```bash
Introduce el primer número: 5
Introduce el segundo número: a
Los valores introducidos no son correctos. Inténtalo de nuevo.
Introduce el primer número: ag
Los valores introducidos no son correctos. Inténtalo de nuevo.
Introduce el primer número: 5
Introduce el segundo número: 0
Operaciones disponibles: 
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Suma
5
Operación ejecutada. Continuación de ejecución del programa.
```

Elaboremos ahora una función `divide()` diferente a la vista en el ejemplo anterior:

```python
def divide():
    op1 = (float(input("Dividendo: ")))
    op2 = (float(input("Divisor: ")))
    print("La división resulta: " + str(op1 / op2))
    print("Cálculo finalizado.")


divide()
```

Como antes, el programa arroja excepciones si intentamos dividir por cero o introducimos cadenas de texto como datos. Capturémoslas de manera consecutiva:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    except ValueError:
        print("El valor introducido es erróneo.")
    except ZeroDivisionError:
        print("No se puede dividir entre cero.")
    print("Cálculo finalizado.")


divide()
```

Existe una alternativa genérica, aunque poco recomendable, que consiste en teclear `except:` sin más e imprimir un mensaje neutro de error. Captura una excepción de forma general, pero no informa sobre lo acontencido.

Por otro lado, cuando queremos que un código se ejecute siempre, existe la posibilidad de ubicarlo en el interior de una claúsula `finally`:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    except ValueError:
        print("El valor introducido es erróneo.")
    except ZeroDivisionError:
        print("No se puede dividir entre cero.")
    finally:
        print("Cálculo finalizado.")


divide()
```

Además, es posible también programar utilizando la combinación `try` - `finally`:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    finally:
        print("Cálculo finalizado.")


divide()
```

Veamos algunas posibles ejecuciones de este último bloque de código:

```bash
Dividendo: 4
Divisor: 2
La división resulta: 2.0
Cálculo finalizado.
```

```bash
Dividendo: aaa
Cálculo finalizado.
Traceback (most recent call last):
  File "prac22_excepciones2_3.py", line 10, in <module>
    divide()
  File "prac22_excepciones2_3.py", line 3, in divide
    op1 = (float(input("Dividendo: ")))
ValueError: could not convert string to float: 'aaa'
```

```bash
Dividendo: 5
Divisor: 0
Cálculo finalizado.
Traceback (most recent call last):
  File "prac22_excepciones2_3.py", line 10, in <module>
    divide()
  File "prac22_excepciones2_3.py", line 5, in divide
    print("La división resulta: " + str(op1 / op2))
ZeroDivisionError: float division by zero
```

La cadena de texto `"Cálculo finalizado"` se muestra por pantalla, independientemente de la presencia o no de excepciones durante la ejecución del algoritmo.

*Nota técnica*: toda instrucción `try` ha de estar acompañada bien de su correspondiente `except`, bien de `finally`, bien de ambas; pero no puede aparecer en solitario.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/22/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
