---
title: 11. Condicionales II
linktitle: 11. Condicionales II
toc: false
type: docs
date: "2019-04-30T00:03:01+01:00"
lastmod: "2019-04-30T00:03:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 11

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 11
---

## Vídeo

{{< youtube cf7o4s9nFu8 >}}

## Notas personales

En este vídeo ampliaremos las posibilidades de la estructura condicional `if` mediante `else` y `elif`, quedando entonces su sintaxis como

```python
if condicion:
    instrucciones
elif condicion:
    instrucciones
else:
    instrucciones
```

Empecemos creando un programa de control de acceso:

```python
print("Verificación de acceso")

edad_usuario = int(input("Introduce tu edad: "))

if edad_usuario < 18:
    print("No puedes pasar.")
else:
    print("Puedes pasar.")
```

Veamos el resultado de algunas ejecuciones de este programa:

```bash
Verificación de acceso
Introduce tu edad: 19
Puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 15
No puedes pasar.
```

Añadamos al programa la posibilidad de mostrar un mensaje de error si el usuario introduce un dato excesivamente elevado:

```python
print("Verificación de acceso")

edad_usuario = int(input("Introduce tu edad: "))

if edad_usuario < 18:
    print("No puedes pasar.")
elif edad_usuario > 100:
    print("Edad incorrecta.")
else:
    print("Puedes pasar.")
```

Veamos el resultado de ejecutar el anterior programa con distintos valores de edad:

```bash
Verificación de acceso
Introduce tu edad: 25
Puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 15
No puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 124
Edad incorrecta.
```

Para reforzar el uso de esta estructura condicional, elaboremos un programa que asigna a cada calificación numérica su correspondiente etiqueta:

```python
print("Control de calificaciones")

nota_alumno = int(input("Introduce la nota: "))

if nota_alumno < 0:
    print("Nota incorrecta.")
elif nota_alumno < 5:
    print("Insuficiente.")
elif nota_alumno < 6:
    print("Suficiente.")
elif nota_alumno < 7:
    print("Bien.")
elif nota_alumno < 9:
    print("Notable.")
elif nota_alumno <= 10:
    print("Sobresaliente.")
else:
    print("Nota incorrecta.")
```

Veamos el resultado de ejecutar el anterior programa con distintas calificaciones:

```bash
Control de calificaciones
Introduce la nota: -6
Nota incorrecta.
```

```bash
Control de calificaciones
Introduce la nota: 4
Insuficiente.
```

```bash
Control de calificaciones
Introduce la nota: 6
Bien.
```

```bash
Control de calificaciones
Introduce la nota: 7
Notable.
```

```bash
Control de calificaciones
Introduce la nota: 10
Sobresaliente.
```

```bash
Control de calificaciones
Introduce la nota: 12
Nota incorrecta.
```

**Ejercicio 1**: crea un programa que pida dos números *enteros* por teclado. El programa tendrá una función llamada `devuelve_max` encargada de devolver el número más alto de los dos introducidos.

```python
def devuelve_max(n1, n2):
    if n1 < n2:
        return n2
    else:
        return n1

num1 = int(input("Introduce el primer número: "))
num2 = int(input("Introduce el segundo número: "))

print("El máximo es: " + str(devuelve_max(num1, num2)))
```

**Ejercicio 2**: crea un programa que pida por teclado ''Nombre'', ''Apellido'' y ''Tfno''. Esos tres datos deberán ser almacenados en una lista y mostrar en consola el mensaje: ''Los datos personales son: nombre apellido teléfono'' (Se mostrarán los datos introducidos por teclado).

```python
nombre = input("Nombre: ")
apell = input("Apellido: ")
tfno = input("Teléfono: ")

datos = [nombre, apell, tfno]

print("Los datos personales son: " + 
      datos[0] + " " + datos[1] + " " + datos[2])
```

**Ejercicio 3**: crea un programa que pida tres números por teclado. El programa imprime en consola la media aritmética de los números introducidos.

```python
num1 = float(input("Introduce el primer número: "))
num2 = float(input("Introduce el segundo número: "))
num3 = float(input("Introduce el tercer número: "))

media = (num1 + num2 + num3) / 3

print("La media aritmética es: " + str(media))
```
