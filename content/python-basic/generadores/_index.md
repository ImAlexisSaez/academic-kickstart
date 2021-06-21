---
title: Generadores
linktitle: Generadores
summary: Introducción al estudio de generadores en Python.
date: "2019-05-05T00:02:01+01:00"
lastmod: "2019-05-05T00:02:01+01:00"
draft: false
toc: true
type: book
weight: 5
---

## Generadores I

### Vídeo

{{< youtube TLVnoqXGWpY >}}

### Notas personales

Un **generador** es una estructura que extrae valores de una función y los almacena, de uno en uno, en objetos iterables (que se pueden recorrer). Cada vez que un generador almacena un valor, permanece en un estado pausado hasta que se solicita el siguiente, característica que se conoce como **suspensión de estado**.

La utilidad de los generadores reside en que:

- son más eficientes que las funciones tradicionales (sobretodo en consumo de recursos y tiempo, al no tener que construir ''estructuras completas de datos'');
- resultan muy útiles con listas de valores infinitos; y
- bajo determinados escenarios, será recomendable que un generador devuelva los valores de uno en uno.

Su sintaxis es:

```python
def nombre():
    yield
```

Creemos un programa que nos genere una lista de números pares, primero a través de una función y luego utilizando generadores:

```python
def genera_pares(limite):
    num = 1
    lista_pares = []
    while num < limite:
        lista_pares.append(num * 2)
        num += 1
    return lista_pares


print(genera_pares(10))  # [2, 4, 6, 8, 10, 12, 14, 16, 18]
```

```python
def genera_pares(limite):
    num = 1
    while num < limite:
        yield num * 2
        num += 1


# Creo el objeto iterable que genera la función
devuelve_pares = genera_pares(10)

# Recorro el objeto iterable con, por ejemplo, un bucle for
for i in devuelve_pares:
    print(i)

# 2
# 4
# 6
# 8
# 10
# 12
# 14
# 16
# 18
```

Imaginemos ahora que nuestro objetivo es imprimir en la consola únicamente los tres primeros números pares. Con el método `next()` podemos solicitar valores de uno en uno al objeto iterable fruto del generador:

```python
def genera_pares(limite):
    num = 1
    while num < limite:
        yield num * 2
        num += 1


# Creo el objeto iterable que genera la función
devuelve_pares = genera_pares(10)

print(next(devuelve_pares))  # 2

print("Aquí podría ir más código.")

print(next(devuelve_pares))  # 4

print("Aquí podría ir más código.")

print(next(devuelve_pares))  # 6
```

### Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/19/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

## Generadores II

### Vídeo

{{< youtube ucaHqGII350 >}}

### Notas personales

Estudiemos el uso de la instrucción `yield from`, cuya utilidad reside en la simplificación del código de los generadores en el caso de utilizar bucles anidados.

Por ejemplo, elaboremos un generador que nos devuelva ciudades:

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        yield elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # Madrid

print(next(ciudades_devueltas))  # Barcelona
```

*Nota*: en *Python*, cuando colocamos un `*` delante de un parámetro, estamos indicando que podemos pasar un número indeterminado de argumentos, que los recibirá en forma de tupla.

Imaginemos que ahora deseamos acceder a los elementos de cada una de las ciudades (sus letras en este caso):

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        for sub_elemento in elemento:
            yield sub_elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # M

print(next(ciudades_devueltas))  # a
```

El anterior ejemplo lo podemos simplificar utilizando la instrucción `yield from`:

```python
def devuelve_ciudades(*ciudades):
    for elemento in ciudades:
        yield from elemento


# Creamos objeto generador
ciudades_devueltas = devuelve_ciudades("Madrid", "Barcelona", "Bilbao",
                                       "Valencia")

print(next(ciudades_devueltas))  # M

print(next(ciudades_devueltas))  # a
```

### Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/20/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
