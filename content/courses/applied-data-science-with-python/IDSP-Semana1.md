---
title: Semana 1
linktitle: Semana 1
toc: true
type: docs
date: "2019-05-23T00:00:01+01:00"
lastmod: "2019-05-23T00:00:01+01:00"
draft: false
menu:
  applied-data-science-with-python:
    parent: Curso 1
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## 1. ''Introduction to Specialization''

La dificultad de la presente especialización es de nivel intermedio, ya que requiere que poseamos familiaridad con ciertos conceptos de programación (en *Python* fundamentalmente) y estadística.

*Python* ha sido el lenguaje de programación escogido porque:

- es fácil de aprender, destacando por la gran legibilidad de su código;
- cuenta con cientos de librerías disponibles para desarrollar las tareas más diversas; y
- posee potentes librerías para trabajar en las tareas propias de la *Ciencia de Datos* (el ecosistema *SciPy*).

El primer curso de la especialización, **Introduction to Data Science in Python**, está compuesto por los siguientes cuatro módulos:

1. Prerrequisitos de *Python*.
2. La librería *Pandas*.
3. Consultas (''*querying*'') y manipulaciones avanzadas con *Pandas*.
4. Análisis estadísticos básicos con *NumPy* y *SciPy*.

## 2. ''Data Science''

La popularidad de la *Ciencia de Datos* ha crecido exponencialmente, hecho que podemos confirmar experimentalmente nosotros mismos si acudimos a la web de *Google Trends* y buscamos el término ''*data science*''.

Este interés queda justificado por la actual era de la información en la que vivimos, con compañías que utilizan de manera intensiva las diversas teorías de esta disciplina, como son *Google*, *Facebook*, *Netflix*...

La *Ciencia de Datos* se describe habitualmente, de manera gráfica, mediante el diagrama de *Drew Conway*:

![Diagrama de Drew Conway sobre Ciencia de Datos](week1-img01.png)

No obstante, conceptos como ''escepticismo'', ''experimentación'', ''simulación'' o ''replicación'', entre otros, también tienen cabida en esta disciplina.

Es recomendable la lectura del artículo ''*50 years of Data Science*'' ([enlace](http://courses.csail.mit.edu/18.337/2015/docs/50YearsDataScience.pdf)), de la mano de David Donoho, y en el cual figuran las siguientes seis etapas que componen un proyecto de *Ciencia de Datos*:

1. Exploración y preparación de los datos.
2. Representación y transformación de los datos.
3. Cálculos utilizando los datos.
4. Modelización de los datos.
5. Visualización y presentación de los datos.
6. ''Ciencia'' a través de la *Ciencia de Datos*.

## 3. ''The Coursera Jupyter Notebook System''

Personalmente, como la especialización la seguiré en modo ''Audit'', mi objetivo es realizar las tareas, los ejercicios e incluso los cuestionarios localmente, en lugar de a través de las herramientas que ofrece *Coursera* en la propia plataforma. Para ello, con miras a tener disponible el acceso a los distintos *notebooks* de *Jupyter*, he instalado en mi ordenador *Anaconda* ([enlace](https://www.anaconda.com/distribution/#download-section)).

## 4. ''Python functions''

Familiaricémonos un poco con los *notebooks* de *Python*.


```python
x = 1
y = 2
x + y
```




    3



Los objetos declarados en una celda, permanecen disponibles para que trabajemos con ellos posteriormente como deseemos.


```python
x
```




    1



Refactoricemos el anterior código en una función que sume dos números:


```python
def add_numbers(x, y):
    return x + y

add_numbers(1, 2)
```




    3



**Ejercicio**: modifica la anterior función para que acepte tres parámetros, en lugar de dos, y devuelva la suma de todos ellos.


```python
def add_numbers(x, y, z):
    return x + y + z

add_numbers(1, 2, 3)
```




    6



Así definida la función `add_numbers()`, pierde la funcionalidad de sumar únicamente dos números, ya que *Python* arrojaría un error si solo le pasamos el valor de dos argumentos. Podemos solventar esta situación si el tercer parámetro declarado, `z`, queda como opcional.

*Nota*: los parámetros opcionales de una función figuran los últimos en la declaración de esta.


```python
def add_numbers(x, y, z=None):
    if z == None:
        return x + y
    else:
        return x + y + z
    
add_numbers(1, 2)
```




    3




```python
add_numbers(1, 2, 3)
```




    6



Para imprimir múltiples valores como resultado de una celda en un *notebook* de *Jupyter*, podemos recurrir a la función `print()`.


```python
print(add_numbers(2, 3))
print(add_numbers(2, 3, 4))
```

    5
    9
    

Podemos asignar a variables los valores que una función devuelve.


```python
def add_numbers(x, y, z=None, flag=False):
    if flag:
        print("El valor de flag es verdadero.")
    if z == None:
        return x + y
    else:
        return x + y + z
```


```python
a = add_numbers(1, 2)
print(a)
```

    3
    


```python
b = add_numbers(1, 2, 3, True)
print(b)
```

    El valor de flag es verdadero.
    6
    

En ocasiones, puede resultarnos útil que en la llamada a la función aparezca el nombre de algunos (o todos) de sus parámetros juntos con el valor asignado, puesto que aporta bastante legibilidad.


```python
c = add_numbers(x=1, y=2, z=3, flag=True)
print(c)
```

    El valor de flag es verdadero.
    6
    

**Ejercicio**: reescribe la siguiente función para que funcione de manera correcta. Esta función debería sumar dos números si el valor del parámetro `kind` es `"add"` o si este no se le suministra. En caso contrario, debe restar al primer número el segundo.

```python
def do_math(?, ?, ?):
  if (kind=='add'):
    return a+b
  else:
    return a-b

do_math(1, 2)
```


```python
def do_math(a, b, kind="add"):
    if kind == "add":
        return a + b
    else:
        return a - b

do_math(1, 2)
```




    3



## 5. Python Types and Sequences


```python

```
