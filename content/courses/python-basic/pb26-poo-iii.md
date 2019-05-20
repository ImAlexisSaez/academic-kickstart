---
title: 26. Programación orientada a objetos III
linktitle: 26. POO III
toc: true
type: docs
date: "2019-05-08T00:00:03+01:00"
lastmod: "2019-05-08T00:00:03+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 26

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 26
---

## Vídeo

{{< youtube Y_SiIgxc-xI >}}

## Notas personales

Traslademos a código fuente algunos de los conceptos examinados en las dos lecciones anteriores. La sintaxis para crear la clase `Coche` sería:

```python
class Coche():
    instrucciones
```

Empecemos declarando las **propiedades** de la clase `Coche`:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False
```

Definamos **comportamientos** para los futuros objetos que pertenezcan a esta clase, que vienen determinados por distintos métodos:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def function(self):
        pass
```

En *Sublime Text 3* cuando empezamos a escribir `def` nos ofrece dos opciones, crear una **función** o un **método**. La principal diferencia radica en que la primera no pertenece a ninguna clase, al contrario que la segunda. Podemos, a través de los cursores, escoger en el editor la opción que apunta a un método y se nos proporciona la sintaxis de uno por defecto, como el que se muestra arriba.

Una vez editado, el código queda:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        pass
```

*Nota*: `self` hace referencia al propio objeto perteneciente a la clase, es decir, a la instancia perteneciente a la clase.

Construyamos un objeto de la clase `Coche` y veamos cómo acceder a sus propiedades:

```python
mi_coche = Coche()  # Instanciación de una clase

print("Largo del coche: ", mi_coche.largo_chasis)  # Largo del coche:  250
print("Número de ruedas: ", mi_coche.ruedas)  # Número de ruedas:  4
```

Trabajemos en el método declarado, para ello, escribimos:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        self.en_marcha = True
```

Así, ahora:

```python
print("En marcha: ", mi_coche.en_marcha)  # En marcha:  False
mi_coche.arrancar()
print("En marcha: ", mi_coche.en_marcha)  # En marcha:  True
```

Esta última acción la podríamos haber llevado a cabo a través de otro comportamiento, `estado`:

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


print(mi_coche.estado())  # El coche está parado.
mi_coche.arrancar()
print(mi_coche.estado())  # El coche está en marcha.
```

En resumen, hemos creado la clase `Coche`, que se caracteriza por poseer cuatro propiedades y dos comportamientos.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/26/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
