---
title: "De astas, banderas y un poco de combinatoria"
slug: "de-astas-banderas-y-un-poco-de-combinatoria"
subtitle: "Problema 68"
summary: "Problema 68: una curiosa manera de transmitir señales."

date: 2019-04-13T05:59:39+02:00
lastmod: 2019-08-05T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Combinatoria", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Angel Santos](https://unsplash.com/@afs_snapshots), disponible en [Unsplash](https://unsplash.com/photos/LcCpvQhjJSM)."
---

**Problema 68:** En un puesto de mando, para transmitir señales, hay en línea recta cuatro astas. En cada asta solamente se puede colocar una bandera. Las señales consisten en colocar banderas de distintos colores en dichas astas. Según el número de banderas colocadas, colores de las mismas y lugar que ocupen, la señal será distinta. Halla el número de señales que se pueden transmitir si se posee un juego de siete banderas con los colores del arco iris.

***

Una de las claves de este ejercicio pasa por darse cuenta de que en cada asta se ''puede'' colocar (o no) una bandera para transmitir una determinada señal. Así pues, hemos de discutir las opciones posibles, para las señales disponibles, en función del número de astas empleadas:

- Si emplean las cuatro astas, dado que el orden en el que coloquen las banderas importa y no es posible repetir bandera alguna, la cantidad de señales que pueden transmitir en este caso equivale al número de variaciones de siete elementos tomados de cuatro en cuatro, esto es, 
 
$$
V_{7,4} = 7\cdot6\cdot5\cdot4 = 840.
$$

- Si utilizan tres astas, ello implica que de las cuatro disponibles han de escoger tres, acción que pueden llevar a cabo de $C_{4,3}$ maneras posibles. Una vez escogidas las astas, como el orden en el que coloquen las banderas importa y no pueden repetir bandera alguna, podrían transmitir, para una elección de astas particular, un total de señales que asciende al número de variaciones de siete elementos tomados de tres en tres, es decir, $V_{7,3}$. Ahora, aplicando la *regla del producto*, utilizando tres astas pueden transmitir un número de señales que asciende a 
 
$$
C_{4,3}\cdot V_{7,3} = \dbinom{4}{3}\cdot7\cdot6\cdot5 = 840.
$$

- Si utilizan dos astas, ello implica que de las cuatro disponibles han de escoger dos, acción que pueden llevar a cabo de $C_{4,2}$ maneras posibles (aquí, como antes, no importa el orden, pues es igual escoger las astas primera y segunda, que las astas segunda y primera, lo importante ahora es seleccionar dos astas). Una vez escogidas las astas, como el orden en el que coloquen las banderas importa y no pueden repetir bandera alguna, podrían transmitir, para una elección de astas particular, un total de señales que asciende al número de variaciones de siete elementos tomados de dos en dos, es decir, $V_{7,2}$. Ahora, aplicando la *regla del producto*, utilizando dos astas pueden transmitir un número de señales que asciende a 
 
$$
C_{4,2}\cdot V_{7,2} = \dbinom{4}{2}\cdot7\cdot6 = 252.
$$

- Si utilizan una asta, ello implica que de las cuatro disponibles han de escoger una, acción que pueden llevar a cabo de cuatro maneras posibles. Una vez escogida, tienen siete opciones de cara a escoger la bandera que emplearán para transmitir la señal. Ahora, aplicando la *regla del producto*, utilizando una asta pueden transmitir un número de señales que asciende a 
 
$$
C_{4,1}\cdot V_{7,1} = 4\cdot7 = 28.
$$

- Finalmente, existe una posibilidad adicional que hemos de considerar y consiste en que no utilicen bandera alguna para transmitir una determinada señal (esto es, que no hagan uso de ninguna asta).

Recapitulando, si se posee un juego de siete banderas con los colores del arco iris y cuatro astas donde colocarlas, podrán transmitir un total de

$$
840+840+252+28+1 = 1961
$$

señales.
