---
title: 10. Condicionales I
linktitle: 10. Condicionales I
toc: true
type: docs
date: "2019-04-30T00:02:01+01:00"
lastmod: "2019-04-30T00:02:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 10

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 10
---

## Vídeo

{{< youtube iV-4F0jGWak >}}

## Notas personales

Las estructuras condicionales nos permiten alterar el flujo de ejecución de un programa. Por lo que respecta al condicional `if`, tiene la siguiente sintaxis:

```python
if condición:
    instrucciones
```

La anterior condición suele venir expresada a través de operadores de comparación (`<`, `>`, `<=`, `>=`, `==`, `!=`). Veamos un sencillo ejemplo de aplicación de una estructura condicional `if` en la definición de una función:

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion

print(evaluacion(6)) # Aprobado
print(evaluacion(1)) # Suspenso
print(evaluacion(2.1)) # Suspenso
```

Programemos una versión interactiva del anterior bloque de instrucciones, donde el usuario ha de introducir la nota durante la ejecución del código (a través de la función `input()`). Para ello, necesitamos activar la consola mediante el menú `Tools`, opción `SublimeREPL` y en el apartado `Python` seleccionamos `Python - RUN current file`.

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion

print("Programa de evaluación de notas de alumnos")

nota_alumno = input()

print(evaluacion(nota_alumno))
```

No obstante, si ejecutamos e insertamos una nota numérica (por ejemplo, `8`), *Python* nos arroja el siguiente error:

```python
# TypeError: '<' not supported between instances of 'str' and 'int'
```

Ello es debido a que cualquier información introducida por el usuario desde el teclado se almacena como cadena de texto (`"8"`), y el operador `<` no está preparado para comparar textos y números. Resolvemos esta situación empleando la función `int()`.

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion

print("Programa de evaluación de notas de alumnos")

nota_alumno = input()

print(evaluacion(int(nota_alumno)))
```

Siendo una iteración del programa, por ejemplo, 

```bash
Programa de evaluación de notas de alumnos
8
Aprobado
```

La función `input()` admite la posibilidad de indicar un mensaje:

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion

print("Programa de evaluación de notas de alumnos")

nota_alumno = input("Introduce la nota del alumno: ")

print(evaluacion(int(nota_alumno)))
```

Siendo ahora una iteración del programa, por ejemplo:

```bash
Programa de evaluación de notas de alumnos
Introduce la nota del alumno: 8
Aprobado
```
