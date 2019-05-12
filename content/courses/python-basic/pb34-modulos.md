---
title: 34. Módulos
linktitle: 34. Módulos
toc: true
type: docs
date: "2019-05-12T00:00:01+01:00"
lastmod: "2019-05-12T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 34

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 34
---

## Vídeo

{{< youtube t93x-vnFvP4 >}}

## Notas personales

Un **módulo** es un archivo con extensión `.py`, `.pyc` (Python compilado) o fichero escrito en *C* para *CPython*, que posee su propio espacio de nombres y que puede contener variables, funciones, clases e incluso otros módulos.

Sirve para organizar y reutilizar el código (**modularización** y **reutilización**). Se genera uno creando un archivo con extensión `.py` (o `.pyc` o archivo en C) y guardándolo donde nos interese.

Vamos a crear un módulo que, siguiendo la organización del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) de código, se llamará `prac34_modulo_matematicas.py`. En su interior tecleamos las siguientes líneas:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)
```

Ahora, generamos otro archivo, `prac34_script1.py`, e importamos el anterior módulo, utilizando para ello la instrucción `import`:

```python
import prac34_modulo_matematicas as modulo

modulo.sumar(5, 7)

modulo.restar(9, 5)

modulo.multiplicar(4, 9)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 4
El resultado de la multiplicación es: 36
```

Como el nombre del módulo generado es un tanto extenso, he utilizado la instrucción `as`, que permite reescribir dicho nombre y, en mi caso, abreviarlo para que su uso sea más cómodo.

Una alternativa a esta estrategia la encontramos en el fichero `prac34_script2.py`, donde se utiliza `from ... import ...`:

```python
from prac34_modulo_matematicas import sumar

sumar(5, 7)
```

```bash
El resultado de la suma es: 12
```

En el bloque de código anterior, únicamente hemos importado la función `sumar()` de nuestro módulo. Podemos añadir más funciones separándolas mediante comas o importar todo el contenido del módulo utilizando el carácter `*`:

```python
from prac34_modulo_matematicas import sumar, restar

sumar(5, 7)

restar(12, 6)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 6
```

```python
from prac34_modulo_matematicas import *

sumar(5, 7)

restar(12, 6)

multiplicar(12, 12)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 6
El resultado de la multiplicación es: 144
```

No obstante, es peligroso actuar así, pues, en ocasiones, podemos reescribir métodos de manera accidental y arribar a resultados no deseados. Además, en aplicaciones complejas, por motivos de optimización, utilizar el carácter `*` provoca que se reserve demasiado espacio en memoria al tener que almacenar todo el contenido del módulo importado.

Creemos un módulo, `prac34_modulo_vehiculos.py` con las clases utilizadas en la lección de herencia asociada al apartado de programación orientada a objetos:

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


class Furgoneta(Vehiculo):
    def carga(self, cargar):
        self.cargado = cargar
        if self.cargado:
            return "La furgoneta está cargada."
        else:
            return "La furgoneta no está cargada."


class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        self.hcaballito = "Voy haciendo el caballito."

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena, "\n", self.hcaballito)


class VehiculoElec(Vehiculo):
    def __init__(self, marca, modelo):
        super().__init__(marca, modelo)
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True
```

Y ahora, en el fichero `prac34_script5.py` tecleamos:

```python
from prac34_modulo_vehiculos import *

mi_coche = Vehiculo("Mazda", "MX5")
mi_coche.estado()
```

```bash
Marca: Mazda 
Modelo: MX5 
En marcha: False 
Acelerando: False 
Frenando: False
```

*Python* busca los módulos en el mismo directorio donde está guardado el fichero desde el cual se realiza la llamada de importación. En caso de no hallarlo ahí, pasa a revisar el `syspath` (es un conjunto de directorios entre los que está, por ejemplo, el de instalación de *Python*).

Si no tenemos los módulos en ninguna de ambas ubicaciones, *Python* arrojará un error al ejecutar el programa. Para solucionar esta situación estudiaremos el uso de **paquetes** en la próxima lección.
