---
title: 32. Programación orientada a objetos IX
linktitle: 32. POO IX
toc: true
type: book
date: "2019-05-10T00:00:02+01:00"
lastmod: "2019-05-10T00:00:02+01:00"
draft: false
weight: 32
---

## Vídeo

{{< youtube kV1cN_bqcSw >}}

## Notas personales

En esta lección, abordaremos el concepto de **polimorfismo**. Un objeto puede cambiar de forma dependiendo del contexto en el que se utilice y, por tanto, modificar tanto sus propiedades como sus comportamientos asociados.

Como *Python* es un lenguaje de tipado dinámico, esta característica es sencilla de utilizar.

Veamos un ejemplo:

```python
class Coche():
    def desplazamiento(self):
        print("Me desplazo utilizando cuatro ruedas.")


class Moto():
    def desplazamiento(self):
        print("Me desplazo utilizando dos ruedas.")


class Camion():
    def desplazamiento(self):
        print("Me desplazo utilizando seis ruedas.")
```

Así, si ahora tecleamos:

```python
mi_vehiculo = Moto()

mi_vehiculo.desplazamiento()

mi_vehiculo2 = Coche()

mi_vehiculo2.desplazamiento()

mi_vehiculo3 = Camion()

mi_vehiculo3.desplazamiento()
```

```bash
Me desplazo utilizando dos ruedas.
Me desplazo utilizando cuatro ruedas.
Me desplazo utilizando seis ruedas.
```

Si tuviésemos cientos de vehículos y quisiéramos utilizar sus comportamientos, habríamos de seguir el patrón esbozado arriba.

No obstante, nos podemos aprovechar de la magia del polimorfismo creando una función como se muestra a continuación:

```python
def desplazamiento_vehiculo(vehiculo):
    vehiculo.desplazamiento()
```

Y como el objeto `vehiculo` posee la capacidad de adquirir el rol de cualquiera de los vehículos programados arriba (coche, moto o camión), *Python* en todo momento sabrá a qué método `desplazamiento()` acudir en cada instante.

Así, si escribimos:

```python
mi_vehiculo = Camion()

desplazamiento_vehiculo(mi_vehiculo)

mi_vehiculo = Coche()

desplazamiento_vehiculo(mi_vehiculo)

mi_vehiculo = Moto()

desplazamiento_vehiculo(mi_vehiculo)
```

```bash
Me desplazo utilizando seis ruedas.
Me desplazo utilizando cuatro ruedas.
Me desplazo utilizando dos ruedas.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/32/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).





