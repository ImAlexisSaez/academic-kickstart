---
title: 41. Guardado permanente
linktitle: 41. Guardado
toc: true
type: book
date: "2019-05-20T00:00:01+01:00"
lastmod: "2019-05-20T00:00:01+01:00"
draft: false
weight: 41
---

## Vídeo

{{< youtube J3qvf1fTCsU >}}

## Notas personales

En esta lección, continuaremos estudiando cómo guardar datos de forma permanente en ficheros externos, reforzando así los contenidos aprendidos hasta el momento.

Empecemos importando la librería `pickle` y creando una clase sencilla: `Persona`.

```python
import pickle


class Persona:
    def __init__(self, nombre, genero, edad):
        self.nombre = nombre
        self.genero = genero
        self.edad = edad
        print("Se ha creado una persona nueva con el nombre de", self.nombre)

    def __str__(self):
        return "{} {} {}".format(self.nombre, self.genero, self.edad)
```

*Nota*: el método `__str__()` convierte en cadena de texto la información de un objeto.

Así, si ahora tecleamos:

```python
sandra = Persona("Sandra", "Femenino", "29")
```

```bash
Se ha creado una persona nueva con el nombre de Sandra
```

El objetivo será crear algunos objetos de dicha clase, almacenarlos en una lista (empresa que realizaremos a través de otra clase, `ListaPersonas`) y después volcar la información en un fichero externo, al cual podamos acceder en cualquier instante.

```python
import pickle


class Persona:
    def __init__(self, nombre, genero, edad):
        self.nombre = nombre
        self.genero = genero
        self.edad = edad
        print("Se ha creado una persona nueva con el nombre de", self.nombre)

    def __str__(self):
        return "{} {} {}".format(self.nombre, self.genero, self.edad)


class ListaPersonas:
    personas = []

    def agregar_personas(self, persona):
        self.personas.append(persona)

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())


lista_personas = ListaPersonas()

sandra = Persona("Sandra", "Femenino", "29")
lista_personas.agregar_personas(sandra)

antonio = Persona("Antonio", "Masculino", "39")
lista_personas.agregar_personas(antonio)

ana = Persona("Ana", "Femenino", "20")
lista_personas.agregar_personas(ana)

lista_personas.mostrar_personas()
```

```bash
Se ha creado una persona nueva con el nombre de Sandra
Se ha creado una persona nueva con el nombre de Antonio
Se ha creado una persona nueva con el nombre de Ana
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
```

Almacenemos ahora la lista de personas que hemos generado en un fichero externo. Para ello, incluiremos los pasos necesarios del mencionado proceso en el constructor de la clase `ListaPersonas`:

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())


lista_personas = ListaPersonas()
```

```bash
El fichero está vacío.
```

*Nota*: en la función `open()`, el valor del argumento `"ab+"` nos permite agregar información a un fichero de codificación binaria.

A continuación, modifiquemos el método `agregar_personas()` para que una vez añadida a la lista la nueva información, la almacene en el fichero externo.

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)
        self.guardar_personas()

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())

    def guardar_personas(self):
        fichero = open("lista_de_personas", "wb")
        pickle.dump(self.personas, fichero)
        fichero.close()
        del fichero
```

Así, si ejecutamos ahora el siguiente bloque de código:

```python
lista_personas = ListaPersonas()

sandra = Persona("Sandra", "Femenino", "29")
lista_personas.agregar_personas(sandra)

antonio = Persona("Antonio", "Masculino", "39")
lista_personas.agregar_personas(antonio)

ana = Persona("Ana", "Femenino", "20")
lista_personas.agregar_personas(ana)
```

```bash
El fichero está vacío.
Se ha creado una persona nueva con el nombre de Sandra
Se ha creado una persona nueva con el nombre de Antonio
Se ha creado una persona nueva con el nombre de Ana
```

Recuperemos la información guardada en el fichero externo, utilizando para ello un método que añadiremos a la clase `ListaPersonas`, `mostrar_informacion`:

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)
        self.guardar_personas()

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())

    def guardar_personas(self):
        fichero = open("lista_de_personas", "wb")
        pickle.dump(self.personas, fichero)
        fichero.close()
        del fichero

    def mostrar_informacion(self):
        print("La información del fichero externo es la siguiente:")
        for persona in self.personas:
            print(persona.__str__())
```

Así, 

```python
lista_personas.mostrar_informacion()
```

```bash
La información del fichero externo es la siguiente:
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
```

Agreguemos una nueva persona. Para ello, tecleamos por ejemplo:

```python
juan = Persona("Juan", "Masculino", "47")
lista_personas.agregar_personas(juan)

lista_personas.mostrar_informacion()
```

```bash
Se ha creado una persona nueva con el nombre de Juan
La información del fichero externo es la siguiente:
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
Juan Masculino 47
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/41/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
