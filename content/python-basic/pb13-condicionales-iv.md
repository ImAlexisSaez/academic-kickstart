---
title: 13. Condicionales IV
linktitle: 13. Condicionales IV
toc: true
type: book
date: "2019-05-01T00:02:01+01:00"
lastmod: "2019-05-01T00:02:01+01:00"
draft: false
weight: 13
---

## Vídeo

{{< youtube rDGsWYnQEJY >}}

## Notas personales

A continuación, veremos el uso de los operadores lógicos `and` y `or`, y del operador `in`. Para ello, crearemos un programa que evalúe si un alumno tiene o no derecho a beca, dependiendo de

- la distancia a la que vive del centro,
- el número de hermanos, y
- el salario familiar.

```python
print("Programa de evaluación de becas - Curso 2018/19")

dist_escuela = int(input("Introduce la distancia a la escuela (en km): "))
print("Distancia a la escuela: " + str(dist_escuela))

num_hermanos = int(input("Introduce el número de hermanos en el centro: "))
print("Número de hermanos: " + str(num_hermanos))

sal_familiar = int(input("Introduce el salario anual bruto: "))
print("Salario anual bruto: " + str(sal_familiar))

if dist_escuela > 40 and num_hermanos > 2 and sal_familiar <= 20000:
    print("Tienes derecho a beca")
else:
    print("No tienes derecho a beca")
```

Revisemos la estrutura condicional para que no sea tan complicado tener derecho a una beca:

```python
print("Programa de evaluación de becas - Curso 2018/19")

distancia_escuela = int(input("Introduce la distancia a la escuela (en km): "))
print("Distancia a la escuela: " + str(distancia_escuela))

numero_hermanos = int(input("Introduce el número de hermanos en el centro: "))
print("Número de hermanos: " + str(numero_hermanos))

salario_familiar = int(input("Introduce el salario anual bruto: "))
print("Salario anual bruto: " + str(salario_familiar))

if distancia_escuela > 40 or numero_hermanos > 2 or salario_familiar <= 20000:
    print("Tienes derecho a beca")
else:
    print("No tienes derecho a beca")
```

Estudiemos ahora el uso del operador `in`. Crearemos un programa donde un alumno debe escoger una asignatura opcional de entre un listado predeterminado:

```python
print("Asignaturas optativas - Curso 2018/19")

print("- Informática gráfica")
print("- Pruebas de software")
print("- Usabilidad y accesibilidad")

asignatura = input("Escoge la asignatura optativa: ")

if asignatura in ("Informática gráfica", "Pruebas de software",
                  "Usabilidad y accesibilidad"):
    print("Asignatura elegida: " + asignatura)
else:
    print("La asignatura escogida no está contemplada.")
```

*Python* es **case sensitive** (distingue entre mayúsculas y minúsculas). Para solucionar esta situación, utilizamos las funciones `lower()` y `upper()`, funciones que escriben, respectivamente, una cadena de caracteres toda en minúsculas o mayúsculas.

```python
print("Asignaturas optativas - Curso 2018/19")

print("- Informática gráfica")
print("- Pruebas de software")
print("- Usabilidad y accesibilidad")

opcion = input("Escoge la asignatura optativa: ")

asignatura = opcion.lower()

if asignatura in ("informática gráfica", "pruebas de software",
                  "usabilidad y accesibilidad"):
    print("Asignatura elegida: " + asignatura)
else:
    print("La asignatura escogida no está contemplada.")
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/13/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

