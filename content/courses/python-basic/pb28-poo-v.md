---
title: 28. Programación orientada a objetos V
linktitle: 28. POO V
toc: true
type: docs
date: "2019-05-09T00:00:02+01:00"
lastmod: "2019-05-09T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 28

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 28
---

## Vídeo

{{< youtube OU-e2uhoGxE >}}

## Notas personales

A continuación, abordaremos la encapsulación de métodos partiendo del último ejemplo de la lección anterior:

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos
        if self.__en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")
```

Encapsular un método es hacer que sea únicamente accesible desde la propia clase, no desde fuera.

Como aplicación práctica de este procedimiento, generemos un método que compruebe que todo está en orden antes de arrancar, `chequeo_interno(self)`, que llamaremos desde `arrancar()`.

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos

        if self.__en_marcha:
            chequeo = self.chequeo_interno()

        if self.__en_marcha and chequeo:
            return "El coche está en marcha."
        elif self.__en_marcha and not chequeo:
            return "Algo ha ido mal en el chequeo. No podemos arrancar."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")

    def chequeo_interno(self):
        print("Realizando chequeo interno.")

        self.gas = "Ok"
        self.aceite = "Ok"
        self.puertas = "Ok"

        if self.gas == "Ok" and self.aceite == "Ok" and self.puertas == "Ok":
            return True
        else:
            return False
```

Así, si ahora tecleamos:

```python
mi_coche1 = Coche()

print(mi_coche1.arrancar(True))

mi_coche1.estado()

print("---- Segundo vehículo ----")

mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.estado()
```

El resultado será:

```bash
Realizando chequeo interno.
El coche está en marcha.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
---- Segundo vehículo ----
El coche está parado.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

El método `chequeo_interno()` es accesible desde fuera de la clase (no está encapsulado), pero, ¿es lógico que podamos acceder a él en cualquier momento? ¿Incluso si está parado? Si el método está diseñado para ejecutarse únicamente en el momento previo a arrancar, hemos de ''protegerlo''.

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))
print(mi_coche2.chequeo_interno())  # Absurdo en este caso
mi_coche2.estado()
```

```bash
El coche está parado.
Realizando chequeo interno.
True
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

Para encapsular el mencionado método, utilizamos la estrategia de `__`:

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos

        if self.__en_marcha:
            chequeo = self.__chequeo_interno()

        if self.__en_marcha and chequeo:
            return "El coche está en marcha."
        elif self.__en_marcha and not chequeo:
            return "Algo ha ido mal en el chequeo. No podemos arrancar."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")

    def __chequeo_interno(self):
        print("Realizando chequeo interno.")

        self.gas = "Ok"
        self.aceite = "Ok"
        self.puertas = "Ok"

        if self.gas == "Ok" and self.aceite == "Ok" and self.puertas == "Ok":
            return True
        else:
            return False
```

De forma que si ahora escribimos:

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))
print(mi_coche2.__chequeo_interno())
mi_coche2.estado()
```

El resultado es:

```bash
El coche está parado.
Traceback (most recent call last):
  File "prac28_poo5_1.py", line 50, in <module>
    print(mi_coche2.__chequeo_interno())
AttributeError: 'Coche' object has no attribute '__chequeo_interno'
```

Es decir, *Python* arroja un error. No nos deja llamar al método `__chequeo_interno()` desde fuera de la propia clase `Coche` porque está encapsulado.

¿Cuándo encapsular una variable o un método? No existe una ''regla de oro'', esto es, habremos de hacerlo cuando la clase así lo precise, dependiendo del comportamiento que posea una clase y en función del criterio del propio programador.
