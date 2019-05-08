---
title: 8. Tuplas
linktitle: 8. Tuplas
toc: true
type: docs
date: "2019-04-30T00:01:00+01:00"
lastmod: "2019-04-30T00:01:00+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 8

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 8
---

## Vídeo

{{< youtube Ufqh8aoR9hE >}}

## Notas personales

Una **tupla** es una lista inmutable que

- no permite añadir, eliminar, mover elementos...
- permite la extracción de porciones, que continuan siendo tuplas, y
- posibilita búsquedas de índice (`.index()`) y comprobaciones de si un elemento pertenece o no a ella (`in`).

Son útiles porque

- son más rápidas en cuanto a ejecución se refiere,
- requieren menos espacio (mayor optimización),
- formatean cadenas de texto, y
- pueden utilizarse como claves en un diccionario, a diferencia de las listas.

Su sintaxis es `nombre = (elem1, elem2, elem3...)`, siendo el uso de los paréntesis opcional aunque recomendable. El acceso a los elementos funciona como en las listas.

```python
mi_tupla = ("Alexis", 10, 1, 1995)

print(mi_tupla) # ("Alexis", 10, 1, 1995)
print(mi_tupla[1]) # 10
print(mi_tupla[-1]) # 1995
```

Existen funciones que nos permiten convertir tuplas en listas (`list()`) y viceversa (`tuple()`):

```python
mi_lista = list(mi_tupla)
print(mi_lista) # ["Alexis", 10, 1, 1995]

mi_tupla = tuple(mi_lista)
print(mi_tupla) # ("Alexis", 10, 1, 1995)
```

Comprobamos la pertenencia de un elemento a la tupla mediante `in`:

```python
print("Alexis" in mi_tupla) # True
print(3.14 in mi_tupla) # False
```

Con `.count()` obtenemos el número de elementos que se encuentran dentro de una tupla:

```python
mi_tupla = ("Alexis", 1, 2, 2, True, 2, "Alexis")

print(mi_tupla.count("Alexis")) # 2
print(mi_tupla.count(1)) # 2 (True cuenta como 1)
print(mi_tupla.count(2)) # 3
```

El método `len` nos permite hallar la longitud de una tupla, siendo el índice del último elemento igual a `len - 1`:

```python
print(len(mi_tupla)) # 7
print(mi_tupla[len(mi_tupla) - 1]) # "Alexis"
```

Podemos crear tuplas unitarias siguiendo el patrón `nombre = (elem,)`:

```python
mi_tupla = ("Alexis",)

print(type(mi_tupla)) # <class 'tuple'>
print(len(mi_tupla)) # 1
```

Como mencionamos, los paréntesis son opcionales:

```python
mi_tupla = "Alexis", 3.14, True, 10

print(type(mi_tupla)) # <class 'tuple'>
print(mi_tupla) # ("Alexis", 3.14, True, 10)
```

Esta sintaxis se conoce como **empaquetado de tupla** y hemos de ser cautos, pues en un futuro, al combinarla con el uso de funciones, puede dar lugar a confusiones.

El proceso inverso, **desempaquetado de tuplas**, nos permite asignar los elementos de una tupla a diferentes variables:

```python
mi_tupla = ("Alexis", 3.14, True, 10)

nombre, pi, alto, mes = mi_tupla

print(nombre) # Alexis
print(pi) # 3.14
print(alto) # True
print(mes) # 10
```
