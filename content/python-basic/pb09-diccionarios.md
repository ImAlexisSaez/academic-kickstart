---
title: 9. Diccionarios
linktitle: 9. Diccionarios
toc: true
type: book
date: "2019-04-30T00:01:01+01:00"
lastmod: "2019-04-30T00:01:01+01:00"
draft: false
weight: 9
---

## Vídeo

{{< youtube 2OmgHl8lp0I >}}

## Notas personales

Un **diccionario** es una estructura de datos que nos permite almacenar valores de diferentes tipos (enteros, cadenas de texto, decimales...) e incluso listas, tuplas y otros diccionarios.

Su principal característica reside en que cada dato se almacena asociado a una clave única, de tal forma que se crea una relación de tipo `clave:valor` para cada elemento guardado. Además, los mencionados elementos no están ordenados, es decir, el orden es indiferente (por la presencia las referidas claves únicas) a la hora de guardar información en un diccionario.

Su sintaxis es `nombre = {clave:valor}`. 

Creemos un diccionario que almacene países (clave) y capitales (valor), y veamos cómo se accede a cada uno de sus elementos:

```python
mi_dicc = {"Alemania": "Berlin",
           "Francia": "París",
           "Reino Unido": "Londres",
           "España": "Madrid"}

print(mi_dicc["Francia"])  # París
print(mi_dicc["España"])  # Madrid

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid'}
```

Agregamos nuevos elementos al diccionario con el patrón `nombre[clave] = valor`:

```python
mi_dicc["Italia"] = "Lisboa"

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid', 'Italia': 'Lisboa'}
```

Modificamos un valor asignado a una clave simplemente sobreescribiéndolo:

```python
mi_dicc["Italia"] = "Roma"

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid', 'Italia': 'Roma'}
```

Suprimimos elementos con `del`:

```python
del mi_dicc["Reino Unido"]

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'España': 'Madrid', 'Italia': 'Roma'}
```

Generemos un diccionario que presente diferentes tipos de datos:

```python
mi_dicc = {"Alemania": "Berlín",
           23: "Jordan",
           "Mosqueteros": 3}

print(mi_dicc)  # {'Alemania': 'Berlín', 23: 'Jordan', 'Mosqueteros': 3}
```

Empleemos una tupla (el procedimiento sería similar si optamos por una lista) para asignar la clave a cada uno de los valores:

```python
mi_tupla = ("España", "Francia", "Reino Unido", "Alemania")
mi_dicc = {mi_tupla[0]: "Madrid",
           mi_tupla[1]: "París",
           mi_tupla[2]: "Londres",
           mi_tupla[3]: "Berlín"}

print(mi_dicc)  # {'España': 'Madrid', 'Francia': 'París', 'Reino Unido': 'Londres', 'Alemania': 'Berlín'}

print(mi_dicc["España"])  # Madrid
print(mi_dicc[mi_tupla[0]])  # Madrid
```

También podemos almacenar tuplas (o listas...) como valores:

```python
mi_dicc = {23: "Jordan",
           "Nombre": "Michael",
           "Equipo": "Chicago",
           "Anillos": (1991, 1992, 1993, 1996, 1997, 1998)}

print(mi_dicc)  # {23: 'Jordan', 'Nombre': 'Michael', 'Equipo': 'Chicago', 'Anillos': (1991, 1992, 1993, 1996, 1997, 1998)}
print(mi_dicc["Equipo"])  # Chicago
print(mi_dicc["Anillos"])  # (1991, 1992, 1993, 1996, 1997, 1998)
```

Asimismo, guardemos un diccionario dentro de otro:

```python
mi_dicc = {23: "Jordan",
           "Nombre": "Michael",
           "Equipo": "Chicago",
           "Anillos": {"Temporadas": (1991, 1992, 1993, 1996, 1997, 1998)}}

print(mi_dicc)  # {23: 'Jordan', 'Nombre': 'Michael', 'Equipo': 'Chicago', 'Anillos': {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}}
print(mi_dicc["Anillos"])  # {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}
```

Algunos métodos interesantes a conocer son:

- `.keys()`, para acceder a las claves de un diccionario; 
- `.values()`, para conocer los valores de un diccionario; y 
- `len()`, para averiguar la longitud de un diccionario:

```python
print(mi_dicc.keys())  # dict_keys([23, 'Nombre', 'Equipo', 'Anillos'])
print(mi_dicc.values())  # dict_values(['Jordan', 'Michael', 'Chicago', {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}])
print(len(mi_dicc))  # 4
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/09/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
