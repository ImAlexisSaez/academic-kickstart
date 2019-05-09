---
title: 30. Programación orientada a objetos VII
linktitle: 30. POO VII
toc: true
type: docs
date: "2019-05-09T00:00:04+01:00"
lastmod: "2019-05-09T00:00:04+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 30

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 30
---

## Vídeo

{{< youtube jMQQN9OxwVc >}}

## Notas personales

Continuemos con el ejemplo de la lección anterior:

```python
# Clase Padre
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


# Clase hija
class Moto(Vehiculo):
    pass
```

Construyamos la clase `Moto`, añadiendo un comportamiento nuevo, `caballito`, que se va a sumar a los cuatro heredados de la clase `Vehiculo`:

```python
class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        hcaballito = "Voy haciendo el caballito."
```

Ahora podríamos teclear:

```python
mi_moto = Moto("Honda", "CBR")

mi_moto.caballito()

mi_moto.estado()
```

```bash
Marca: Honda 
Modelo: CBR 
En marcha: False 
Acelerando: False 
Frenando: False
```

El programa ''funciona'' (al menos no arroja errores), pero no nos está informando si estamos haciendo el caballito o no.

Abordemos esta situación sobreescribiendo el método `estado` heredado de la clase `Vehiculo`, para así incorporar la información sobre el nuevo comportamiento de la clase `Moto`.

Para sobreescribir un método de la clase padre definimos uno en la clase hija que se caracterice por tener el mismo nombre y número de parámetros:

```python
class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        self.hcaballito = "Voy haciendo el caballito."

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena, "\n", self.hcaballito)
```

De esta manera, la ejecución del siguiente bloque de código:

```python
mi_moto = Moto("Honda", "CBR")

mi_moto.caballito()

mi_moto.estado()
```

Produce como resultado ahora:

```bash
Marca: Honda 
Modelo: CBR 
En marcha: False 
Acelerando: False 
Frenando: False 
 Voy haciendo el caballito.
```

Modifiquemos el código para albergar la posibilidad de trabajar con furgonetas:

```python
class Furgoneta(Vehiculo):
    def carga(self, cargar):
        self.cargado = cargar
        if self.cargado:
            return "La furgoneta está cargada."
        else:
            return "La furgoneta no está cargada."
```

Así,

```python
mi_furgo = Furgoneta("Renault", "Kangoo")

mi_furgo.arrancar()

mi_furgo.estado()

mi_furgo.carga(True)
```

```bash
Marca: Renault 
Modelo: Kangoo 
En marcha: True 
Acelerando: False 
Frenando: False
```

Todo funciona de manera adecuada, con la salvedad de que no estamos viendo que la furgoneta está cargada. Como el método `carga()` devuelve una cadena de texto, añadiendo una función `print()` solucionamos el entuerto:

```python
mi_furgo = Furgoneta("Renault", "Kangoo")

mi_furgo.arrancar()

mi_furgo.estado()

print(mi_furgo.carga(True))
```

```bash
Marca: Renault 
Modelo: Kangoo 
En marcha: True 
Acelerando: False 
Frenando: False
La furgoneta está cargada.
```

Obviamente, una instrucción del tipo `mi_moto.carga()` arroja un error, ya que no hereda de `Furgoneta` la clase `Moto`, sino de `Vehiculo`.

Añademos soporte para vehículos electrónicos:

```python
class VehiculoElec():
    def __init__(self):
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True
```

Y, a continuación, generemos una clase para trabajar con biciletas eléctricas. Estas tienen marca, modelo, pueden arrancar, frenar... y a la vez también poseen autonomia y la posibilidad de cargar energía. *Python* nos permite heredar de dos o más clases, que se conoce como **herencia múltiple**:

```python
class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Hemos de tener en cuenta que cuando se da herencia múltiple, a la hora de tomar el constructor o los diferentes métodos, se da la preferencia según hayamos ordenado las clases padres de las que hereda. En este caso, no podemos iniciar una bicicleta eléctrica con marca y modelo, aprovechando así el constructor de la clase `Vehiculo`, ya que la clase `VehiculoElec` posee su propio constructor y este último tiene preferencia por haber colocado esta clase primero en la definición de `BicicletaElec`.

```python
mi_bici = BicicletaElec("Orbea", "HCI30")
```

```bash
Traceback (most recent call last):
  File "prac30_poo7_3.py", line 58, in <module>
    mi_bici = BicicletaElec("Orbea", "HCI30")
TypeError: __init__() takes 1 positional argument but 3 were given
```

No obstante, si intercambiamos el orden de las clases padre en la definición de `BicicletaElec`:

```python
class BicicletaElec(Vehiculo, VehiculoElec):
    pass


mi_bici = BicicletaElec("Orbea", "HCI30")

mi_bici.estado()
```

La ejecución ya no arroja errores, mostrando el siguiente resultado:

```bash
Marca: Orbea 
Modelo: HCI30 
En marcha: False 
Acelerando: False 
Frenando: False
```
