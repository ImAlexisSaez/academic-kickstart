---
title: 25. Programación orientada a objetos II
linktitle: 25. POO II
toc: true
type: book
date: "2019-05-08T00:00:02+01:00"
lastmod: "2019-05-08T00:00:02+01:00"
draft: false
weight: 25
---

## Vídeo

{{< youtube 2UNrSiKEI8w >}}

## Notas personales

Una **clase** es un modelo donde se redactan las características comunes de un grupo de objetos.

Una **instancia** (o **ejemplar** u **objeto**) es un miembro concreto de una clase.

La **modularización** surge cuando un programa está compuesto de diversas clases. Cada una de ellas funciona de manera independiente (facilitando así enormemente su mantenimiento y control de excepciones) y es posible su reutilización en otros programas.

La **encapsulación** nos permite proteger el funcionamiento interno de cierto bloque de código, para que no pueda accederse o alterarse desde el exterior de manera inadecuada. No obstante, todas las clases de un programa estarán ''conectadas'' entre sí de cierta manera (mediante **métodos de acceso** a ciertas características de cada una de las clases).

El mencionado acceso se llevará a cabo empleando la **nomenclatura del punto**. Por ejemplo, supongamos que hemos creado un objeto, de la clase `coche`, llamado `miCoche`. Para acceder a sus propiedades, utilizaremos la sintaxis:

- `miCoche.color = ''rojo''`
- `miCoche.peso = 1500`
- `miCoche.ancho = 2000`
- `miCoche.alto = 900`

De forma similar, el acceso al comportamiento de este objeto se realizará mediante la mencionada nomenclatura:

- `miCoche.arranca()`
- `miCoche.frena()`
- `miCoche.gira()`
- `miCoche.acelera()`
