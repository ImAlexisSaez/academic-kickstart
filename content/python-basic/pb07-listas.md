---
title: 7. Listas
linktitle: 7. Listas
toc: true
type: book
date: "2019-04-29T00:01:04+01:00"
lastmod: "2019-04-29T00:01:04+01:00"
draft: false
weight: 7
---

## Vídeo

{{< youtube Q8hugySbLQQ >}}

## Notas personales

Una **lista** es una estructura de datos que nos permite almacenar gran cantidad de valores. En *Python*, estos pueden añadirse de manera dinámica y ser de diferentes tipos.

Su sintaxis es `nombre = [elem1, elem2, elem3...]` y los elementos están localizados mediante un índice, que en *Python* comienza por 0.

A continuación, creemos una lista con cuatro elementos de tipo texto y veamos cómo imprimirla y acceder a elementos concretos de ella:

```python
mi_lista = ["María", "Pepe", "Marta", "Antonio"]

print(mi_lista)  # ["María", "Pepe", "Marta", "Antonio"]
print(mi_lista[:])  # ["María", "Pepe", "Marta", "Antonio"]

print(mi_lista[2])  # Marta
print(mi_lista[0])  # María
```

Si empleamos índices que superan el rango de elementos de una lista, *Python* nos arroja un error:

```python
print(mi_lista[4])
# IndexError: list index out of range
```

No obstante, sí es posible utilizar índices con valor negativo, que nos permiten acceder (empezando por `-1`) a los elementos de una lista desde la derecha:

```python
print(mi_lista[-1]) # Antonio
print(mi_lista[-3]) # Pepe
```

Obviamente, esta estrategia también está limitada por el número de elementos de la lista y no podemos pasar índices negativos fuera de su correspondiente rango:

```python
print(mi_lista[-5])
# IndexError: list index out of range
```

Además, podemos acceder a porciones de una lista, mediante la sintaxis `nombre[a:b]`, que extrae todos los elementos comprendidos entre los índices `a` y el anterior a `b`. Por ejemplo:

```python
print(mi_lista[0:2])  # ["María", "Pepe"]
print(mi_lista[0:1])  # ["María"]
print(mi_lista[-3:-1])  # ["Pepe", "Marta"]
```

Se pueden omitir algunos de los anteriores índices indicados y *Python* sobreentiende que comienza o acaba en el extremo correspondiente:

```python
print(mi_lista[:2])  # ["María", "Pepe"]
print(mi_lista[2:])  # ["Marta", "Antonio"]
print(mi_lista[-2:])  # ["Marta", "Antonio"]
```

*Nota técnica*: cuando accedemos a una porción, se conserva el tipo lista, pero no así si se extrae un único elemento en particular.

```python
print(type(mi_lista[2]))  # <class 'str'>
print(type(mi_lista[2:3]))  # <class 'list'>
```

Agregamos elementos al final de la lista utilizando `.append()`:

```python
mi_lista.append("Sandra")
print(mi_lista)  # ["María", "Pepe", "Marta", "Antonio", "Sandra"]
```

Usaremos `.insert(posición, elemento)`, si buscamos añadir un elemento en un punto intermedio:

```python
mi_lista.insert(2, "Paco")
print(mi_lista)  # ["María", "Pepe", "Paco", "Marta", "Antonio", "Sandra"]
```

Es posible agregar varios elementos al final de una lista utilizando `.extend()` y pasando como argumento otra lista:

```python
mi_compra = ["Manzanas"]
print(mi_compra)  # ["Manzanas"]

mi_compra.extend(["Aguacates", "Sandía"])
print(mi_compra)  # ["Manzanas", "Aguacates", "Sandía"]
```

Para acceder al índice de un elemento, empleamos `.index(elemento)`:

```python
print(mi_lista.index("Antonio"))  # 4
print(mi_compra.index("Sandía"))  # 2
```

Si intentamos acceder al índice de elementos que no están incluidos en la lista, *Python* arroja un error:

```python
print(mi_compra.index("Melón"))
# ValueError: 'Melón' is not in list
```

En una lista, puede haber elementos iguales en posiciones distintas. La función `.index()` nos devolverá el valor del índice del primer elemento repetido:

```python
mi_compra.extend(mi_compra)
print(mi_compra)  # ["Manzanas", "Aguacates", "Sandía", "Manzanas", "Aguacates", "Sandía"]
print(mi_compra.index("Manzanas"))  # 0
```

Para comprobar si un elemento se encuentra o no en una lista, utilizamos `in`:

```python
print("Pepe" in mi_lista)  # True
print("Ana" in mi_lista)  # False
```

Tal y como mencionamos arriba, una lista puede almacenar sin problemas elementos de diferentes tipos:

```python
mezcla = ["Alexis", True, 10, 3.14]
print(mezcla)  # ["Alexis", True, 10, 3.14]
```

Para eliminar elementos, usamos `.remove()`:

```python
mezcla.remove(True)
print(mezcla)  # ["Alexis", 10, 3.14]
```

En particular, podemos suprimir el último elemento de una lista mediante `.pop()`:

```python
mezcla.pop()
print(mezcla)  # ["Alexis", 10]
```

El operador `+` concatena listas:

```python
lista1 = ["Ana", 5]
lista2 = [True, 2.1]
lista3 = lista1 + lista2
print(lista3)  # ["Ana", 5, True, 2.1]
```

El operador `*` repite la lista un número determinado de veces.

```python
print(lista1 * 2)  # ["Ana", 5, "Ana", 5]
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/07/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
