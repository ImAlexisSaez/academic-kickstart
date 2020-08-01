---
title: 40. Serialización II
linktitle: 40. Serialización II
toc: true
type: book
date: "2019-05-16T00:00:01+01:00"
lastmod: "2019-05-16T00:00:01+01:00"
draft: false
weight: 40
---

## Vídeo

{{< youtube CkfDnMC79b4 >}}

## Notas personales

En esta lección, continuaremos estudiando el tema de la serialización, analizando ahora cómo llevar a cabo el proceso cuando hay objetos implicados.

Aprovechemos la clase `Vehiculo` que generamos anteriormente y cuyo código fuente recordemos era:

```python
class Vehiculo():
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
        self.enmarcha = False
        self.acelera = False
        self.frena = False

    def arrancar(self):
        self.enmarcha = True

    def acelerar(self):
        self.acelera = True

    def frenar(self):
        self.frena = True

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena)
```

A continuación, importemos la librería `pickle` y creemos una lista con algunas instancias de la clase `Vehiculo`:

```python
import pickle

coche1 = Vehiculo("Mazda", "MX5")
coche2 = Vehiculo("Seat", "León")
coche3 = Vehiculo("Renault", "Megane")

coches = [coche1, coche2, coche3]

fichero = open("coches", "wb")

pickle.dump(coches, fichero)

fichero.close()

del fichero
```

*Notas:*

- Recordemos que estamos creando ficheros externos cuya codificación es binaria, es por ello que el valor del parámetro correspondiente de la función `open()` es `"wb"`.
- Al ejecutar el anterior bloque de código, aparecerá en la carpeta asociada del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0)) el fichero `coches`.

Para rescatar la información de este archivo que acabamos de generar, tecleamos:

```python
import pickle


class Vehiculo():
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
        self.enmarcha = False
        self.acelera = False
        self.frena = False

    def arrancar(self):
        self.enmarcha = True

    def acelerar(self):
        self.acelera = True

    def frenar(self):
        self.frena = True

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena)


fichero = open("coches", "rb")

coches = pickle.load(fichero)

print(coches)
```

```bash
[<__main__.Vehiculo object at 0x00000259428D65C0>, <__main__.Vehiculo object at 0x00000259428F7F28>, <__main__.Vehiculo object at 0x00000259428F7F98>]
```

Efectivamente, disponemos ahora de una lista con tres objetos. No obstante, recordemos que tenemos el método `estado` para acceder a información de interés sobre dichos objetos. Así, si escribimos:

```python
for coche in coches:
    print(coche.estado())
```

```bash
Marca: Mazda 
Modelo: MX5 
En marcha: False 
Acelerando: False 
Frenando: False
None
Marca: Seat 
Modelo: León 
En marcha: False 
Acelerando: False 
Frenando: False
None
Marca: Renault 
Modelo: Megane 
En marcha: False 
Acelerando: False 
Frenando: False
None
```

*Nota*: como podemos comprobar arriba, si hacemos la recuperación de la serialización en un fichero distinto, la definición de la clase `Vehiculo` es necesario que figure asimismo (en caso contrario arroja *Python* un error). El problema radica en que el nuevo archivo no tiene información sobre la clase `Vehiculo` ni, por supuesto, del método `estado()`.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/40/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
