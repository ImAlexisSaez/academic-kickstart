---
title: 27. Programación orientada a objetos IV
linktitle: 27. POO IV
toc: true
type: docs
date: "2019-05-09T00:00:01+01:00"
lastmod: "2019-05-09T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 27

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 27
---

## Vídeo

{{< youtube x5CY8fVyYLo >}}

## Notas personales

Partamos del código del último ejemplo de la lección anterior:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        self.en_marcha = True

    def estado(self):
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."
```

Generemos dos objetos y comparémoslos:

```python
mi_coche1 = Coche()
mi_coche2 = Coche()

print("Largo mi_coche1: ", mi_coche1.largo_chasis)  # Largo mi_coche1:  250
print("Largo mi_coche2: ", mi_coche2.largo_chasis)  # Largo mi_coche2:  250

mi_coche1.arrancar()
print(mi_coche1.estado())  # El coche está en marcha.
print(mi_coche2.estado())  # El coche está parado.
```

Sería buena idea que el método `arrancar()`, además de arrancar el coche, nos informase de su estado (en marcha o parado). También, programaremos el método `estado()` para que nos ofrezca información del coche:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")


mi_coche1 = Coche()
mi_coche2 = Coche()

print(mi_coche1.arrancar(True))  # El coche está en marcha.
print(mi_coche2.arrancar(False))  # # El coche está parado.
mi_coche1.estado()
# El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
mi_coche2.estado()
# El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

En programación orientada a objetos, las características comunes suelen formar parte de lo que se conoce como **estado inicial**. Para especificar dicho estado utilizaremos un **constructor**, que es un método especial que le da estado a los objetos que pertenecen a una clase. Su sintaxis vendrá dada por

```python
def __init__(self):
    propiedades
```

Así, el código de la clase quedaría:

```python
class Coche():
    def __init__(self):
        self.largo_chasis = 250
        self.ancho_chasis = 120
        self.ruedas = 4
        self.en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")
```

¿Qué sucede si intentamos ahora incrementar a cinco el número de ruedas del segundo coche?

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.ruedas = 5

mi_coche2.estado()
```

```bash
El coche está parado.
El coche tiene 5 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

Esta acción, en ciertos casos, no debería estar permitida. Para ello, entra en juego el concepto de **encapsulación**, que nos permitirá proteger propiedades para que no se puedan modificar desde fuera de la propia clase. Su aplicación es tan sencilla como preceder con `__` el nombre de la propiedad a proteger y en aquellos lugares donde luego aparezca:

```python
class Coche():
    def __init__(self):
        self.largo_chasis = 250
        self.ancho_chasis = 120
        self.__ruedas = 4
        self.en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")
```

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.__ruedas = 5

mi_coche2.estado()
```

```bash
El coche está parado.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

En esta ocasión, las cuatro propiedades deberían encapsularse. Incluso `en_marcha`, ya que queremos modificarla únicamente desde el interior de la clase.

La clase entonces quedaría:

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

De la misma manera, se pueden encapsular métodos, opción que estudiaremos en futuras lecciones.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/27/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
