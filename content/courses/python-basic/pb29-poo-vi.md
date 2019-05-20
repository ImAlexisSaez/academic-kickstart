---
title: 29. Programación orientada a objetos VI
linktitle: 29. POO VI
toc: true
type: docs
date: "2019-05-09T00:00:03+01:00"
lastmod: "2019-05-09T00:00:03+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 29

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 29
---

## Vídeo

{{< youtube u_VbLsIyzRk >}}

## Notas personales

En programación orientada a objetos, el concepto de **herencia** intenta dar una réplica aproximada de su contrapartida en la vida real. De una clase, denominada en ocasiones **clase padre** o **superclase**, heredarán otras clases atributos, métodos... Se conocen estas últimas como **subclases** de la anterior (y también como **superclases** si de ellas también heredan otras).

La principal utilidad de la herencia es la reutilización de código cuando se generan clases ''similares''. Hemos de estudiar las características y comportamientos que poseen en común todos los objetos con los que deseamos trabajar. Todo ello lo englobaremos en una **superclase**, de la cual luego heredarán otras clases, que aun teniendo características en común, también es cierto que existen otras peculiaridades que las diferencian.

Veamos un ejemplo práctico:

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


mi_moto = Moto("Honda", "CBR")

mi_moto.estado()
```

```bash
Marca: Honda 
Modelo: CBR 
En marcha: False 
Acelerando: False 
Frenando: False
```

Estamos utilizando métodos de la clase `Vehiculo` a través de la clase `Moto` gracias a la herencia.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/29/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
