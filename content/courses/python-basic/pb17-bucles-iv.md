---
title: 17. Bucles IV
linktitle: 17. Bucles IV
toc: true
type: docs
date: "2019-05-03T00:01:01+01:00"
lastmod: "2019-05-03T00:01:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 17

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 17
---

## Vídeo

{{< youtube UfUM6uzl5SM >}}

## Notas personales

Estudiemos el bucle **while**, que es tipo *indeterminado* porque no sabemos a priori cuántas veces ejecutará el bloque de código contenido en su interior. Su sintaxis es:

```python
while condición:
    instrucciones
```

En el siguiente ejemplo, no obstante, vemos cómo programar un bucle `while` para que funcione como uno de tipo *determinado*:

```python
i = 1

while i <= 10:
    print(f"Iteración: {i}.")
    i += 1

print("Fin de ejecución del bucle while.")

# Iteración: 1.
# Iteración: 2.
# Iteración: 3.
# Iteración: 4.
# Iteración: 5.
# Iteración: 6.
# Iteración: 7.
# Iteración: 8.
# Iteración: 9.
# Iteración: 10.
# Fin de ejecución del bucle while.
```

Generemos ahora un programa que nos solicite la edad y, en caso de ser el dato introducido un número negativo, vuelva a preguntarnos de nuevo (siendo así un ejemplo de bucle `while` de tipo *indeterminado*):

```python
edad = int(input("Introduce tu edad: "))

while edad < 0 or edad > 110:
    print("Has introducido una edad incorrecta. Vuelve a intentarlo.")
    edad = int(input("Introduce tu edad: "))

print(f"Tienes {edad} años. Gracias por colaborar.")
```

Si un usuario se empeña en introducir datos negativos o muy elevados, puede dar lugar a la aparición de un bucle ''infinito''. Veamos una estrategia para evitar este tipo de situaciones con un programa que nos permita hallar la raíz cuadrada de un número:

```python
import math

print("Programa de cálculo de raíces cuadradas")

numero = int(input("Introduce un número: "))

intentos = 0  # Para ejecutar el bucle while un número de veces determinado

while numero < 0:
    print("No se puede hallar la raíz de un número negativo.")
    if intentos == 2:
        print("Has consumido demasiados intentos.")
        print("El programa ha finalizado")
        break
    numero = int(input("Introduce un número: "))
    if numero < 0:
        intentos += 1

if intentos < 2:
    solucion = math.sqrt(numero)
    print(f"La raíz cuadrada de {numero} es {solucion}.")
```

*Notas*:

- La instrucción `break` detiene la ejecución del bucle. Es decir, si durante el transcurso de la ejecución de un bucle llegamos a una situación donde se lee una instrucción `break`, en ese instante, el flujo del programa deja el bucle y salta a la primera línea de código que se encuentra a continuación del mencionado bucle.
- En la línea `solucion = math.sqrt(numero)` introducimos el uso de la clase `math`, que hemos importado en la primera línea de código (`import math`). Es un concepto que se estudiará posteriormente en el curso, pero dicha instrucción sirve para encontrar la raíz cuadrada de un número. La utilidad de importar clases reside en que podemos aprovechar funciones ya programadas y no hemos de ''reinventar la rueda''.

**Ejercicio 1**: crea un programa que pida números infinitamente. Los números introducidos deben ser cada vez mayores. El programa finalizará cuando se introduce un número menor que el anterior.

```python
numero = int(input("Introduce un número entero: "))

condicion = True

while condicion:
    num1 = numero
    numero = int(input("Introduce un número entero mayor que el anterior: "))
    if num1 > numero:
        print(f"Valor incorrecto: {num1} no es mayor que {numero}.")
        condicion = False
    else:
        print(f"Valor correcto: {numero} es mayor que {num1}")
```

**Ejercicio 2**: crea un programa que pida números positivos indefinidamente. El programa termina cuando se introduce un número negativo. Finalmente el programa muestras la suma de todos los números introducidos.

```python
print("Cálculo de la suma de una serie de números positivos.")
print("Instrucciones: ")
print("- Introduce tantos números positivos como desees sumar.")
print("- Introduce un número negativo para calcular la suma.")

suma = 0
num = int(input("Introduce un número positivo: "))

while num > 0:
    suma += num
    num = int(input("Introduce un número positivo: "))

print(f"La suma de los valores positivos introducios es {suma}.")
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/17/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
