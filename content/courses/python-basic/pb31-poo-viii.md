---
title: 31. Programación orientada a objetos VIII
linktitle: 31. POO VIII
toc: true
type: docs
date: "2019-05-10T00:00:01+01:00"
lastmod: "2019-05-10T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 31

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 31
---

## Vídeo

{{< youtube oe04X1B14YY >}}

## Notas personales

En esta lección estudiaremos el uso de las funciones

- `super()` e
- `isinstance()`.

Partimos del último ejemplo de la lección anterior:

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


class VehiculoElec():
    def __init__(self):
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True


class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Si queremos crear un objeto de la clase `BicicletaElec` que posea una marca y un modelo, tenemos dos opciones disponibles:

- Acudir al método `__init__()` de la clase `VehiculoElec` y copiar las líneas que nos interesen del método homónimo de la clase `Vehiculo`. No obstante, este enfoque es, cuanto menos, poco elegante.
- Utilizar la función `super()`, cuya utilidad reside en que procede a llamar al método de la clase padre.

Veamos esta segunda aproximación con un ejemplo un tanto más sencillo:

```python
class Persona():
    def __init__(self, nombre, edad, residencia):
        self.nombre = nombre
        self.edad = edad
        self.residencia = residencia

    def describir(self):
        print("Nombre:", self.nombre, "\nEdad:", self.edad, "\nResidencia:",
              self.residencia)


class Empleado(Persona):
    def __init__(self, salario, antiguedad):
        self.salario = salario
        self.antiguedad = antiguedad
```

Ahora podríamos comenzar a construir objetos de ambas clases:

```python
antonio = Persona("Antonio", 55, "España")

antonio.describir()
```

```bash
Nombre: Antonio 
Edad: 55 
Residencia: España
```

Para constuir un objeto de la clase `Empleado`, hemos de tener en cuenta que tomará como argumentos los parámetros declarados en dicha clase, y no los de `Persona`. No obstante, a la hora de emplear el método `describir()` encontraremos problemas tal y como están programadas ambas clases:

```python
juan = Empleado(1500, 15)

juan.describir()
```

```bash
Traceback (most recent call last):
  File "prac31_poo8_2.py", line 24, in <module>
    juan.describir()
  File "prac31_poo8_2.py", line 8, in describir
    print("Nombre:", self.nombre, "\nEdad:", self.edad, "\nResidencia:",
AttributeError: 'Empleado' object has no attribute 'nombre'
```

Podemos reescribir el constructor de la clase `Empleado`, haciendo uso de la función `super()`, como sigue:

```python
class Empleado(Persona):
    def __init__(self, salario, antiguedad):
        super().__init__("Juan", 33, "Italia")
        self.salario = salario
        self.antiguedad = antiguedad
```

De manera que ahora el código no arrojará error alguno:

```python
juan = Empleado(1500, 15)

juan.describir()
```

```bash
Nombre: Juan 
Edad: 33 
Residencia: Italia
```

No obstante, programado así, todos nuestros empleados se llamarían Juan, tendrían 33 años y serían italianos. Veamos cómo generalizar el funcionamiento de la anterior clase:

```python
class Empleado(Persona):
    def __init__(self, salario, antiguedad, nombre_empleado, edad_empleado,
                 residencia_empleado):
        super().__init__(nombre_empleado, edad_empleado, residencia_empleado)
        self.salario = salario
        self.antiguedad = antiguedad

    def describir(self):
        super().describir()
        print("Salario:", self.salario, "\nAntigüedad:", self.antiguedad)
```

De paso, hemos mejorado también el método `describir()`, que procede a llamar al de la clase padre y, además, añade la información correspondiente al salario y a la antigüedad. De este modo,

```python
juan = Empleado(1500, 15, "Juan", 33, "Italia")

juan.describir()
```

```bash
Nombre: Juan 
Edad: 33 
Residencia: Italia
Salario: 1500 
Antigüedad: 15
```

La función `isinstance()` nos informa si un objeto es instancia de una clase determinada:

```python
juan = Empleado(1500, 15, "Juan", 33, "Italia")

juan.describir()

print(isinstance(juan, Persona))  # True
print(isinstance(juan, Empleado))  # True

marco = Persona("Marco", 51, "Francia")

print(isinstance(marco, Persona))  # True
print(isinstance(marco, Empleado))  # False
```

Con todo, modifiquemos el ejemplo inicial para permitir que una bicicleta eléctrica admita marca y modelo.

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


class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Notemos que:

- Hemos utilizado la función `super()` en el método `__init__()` de `VehiculoElec`.
- Hemos declarado que la clase `VehiculoElec` hereda de `Vehiculo`.

Así,

```python
mi_bici = BicicletaElec("Orbea", "HCI30")

mi_bici.estado()
```

```bash
Marca: Orbea 
Modelo: HCI30 
En marcha: False 
Acelerando: False 
Frenando: False
```

