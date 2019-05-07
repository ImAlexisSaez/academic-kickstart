+++
title = "Comenzando con la combinatoria (II)"
slug  = "comenzando-con-la-combinatoria-ii"
subtitle = "Problema 60"
summary  = "Problema 60: obviamente, las barajas hacen su acto de presencia aquí."

date     = 2019-03-16T05:59:39+02:00
#lastmod = 2019-04-08T10:47:00+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Keisuke Higashio](https://unsplash.com/@keisuke_h), disponible en [Unsplash](https://unsplash.com/photos/jHMiVrTl6Fs)."
+++

**Problema 60:** Considerando una baraja de póquer de $52$ cartas,

- (a) ¿cuántas manos de cinco cartas se pueden extraer?
- (b) De las manos anteriores, ¿cuántas tienen tres ases?
- (c\) De estas últimas, ¿cuántas serán *full*?
- (d) En general, ¿cuántos *full* podemos extraer de la baraja?
- (e) ¿Y cuántas manos contienen una *doble pareja*?

***

De cara al apartado (a), como no importa el orden en el que recibamos las cartas en una mano cualquiera y no existe la posibilidad de recibir cartas recibidas, estamos interesados en calcular el número de combinaciones de $52$ elementos tomados de cinco en cinco. Así, hay

$$
\dbinom{52}{5} = \dfrac{52!}{5!\cdot47!} = \dfrac{52\cdot51\cdot50\cdot49\cdot48}{5!} = 2598960
$$

manos posibles de cinco cartas que podemos extraer de una baraja de póquer de $52$ cartas.

En cuanto al apartado (b), razonaremos como sigue: de los cuatro ases que posee la baraja, tomamos tres de ellos. Como no importa el orden en el que los extraigamos y no habrá ninguno repetido, esta acción la podemos llevar a cabo de 

$$
\dbinom{4}{3} = \dfrac{4!}{3!\cdot1!} = 4
$$

formas posibles. Ahora, del resto de cartas de la baraja que no son ases, $52-4=48$, simplemente hemos de tomar dos cartas adicionales, situación que puede darse de

$$
\dbinom{48}{2} = \dfrac{48!}{2!\cdot46!} = \dfrac{48\cdot47}{2} = 1128
$$

maneras posibles. Aplicando la regla del producto, hay

$$
\dbinom{4}{3}\cdot\dbinom{48}{2} = 4\cdot1128 = 4512
$$

manos que poseen tres ases.

Siguiendo con el apartado (c\), para conformar un *full* a partir de tres ases necesitamos que las otras dos cartas (distintas ambas del as) posean idéntico número. Así, empecemos tomando nuestros tres ases, que sabemos es una acción que podemos llevar a cabo de

$$
\dbinom{4}{3} = \dfrac{4!}{3!\cdot1!} = 4
$$

formas posibles. Ahora, de los doce números distintos de cartas que restan, seleccionamos uno en particular ($C\_{12,1}$) y, de las cuatro cartas posibles asociadas a dicho número, tomamos dos ($C\_{4,2}$). Aplicando la regla del producto, existen

$$
\dbinom{12}{1}\cdot\dbinom{4}{2} = 12\cdot\dfrac{4!}{2!\cdot2!} = 72
$$

maneras de realizar la anterior elección. Finalmente, utilizando de nuevo la regla del producto, hay

$$
\dbinom{4}{3}\cdot\dbinom{12}{1}\cdot\dbinom{4}{2} = 4\cdot72 = 288
$$

manos con $3$ ases que son *full*.

Para el apartado (d), la manera de razonar es muy similar a la mostrada en el párrafo anterior. De los $13$ números posibles, seleccionamos uno de ellos ($C\_{13,1}$) y será de este del que tomaremos tres cartas iguales ($C\_{4,3}$). Ahora de los $12$ números restantes, escogemos uno ($C\_{12,1}$) y extraemos dos cartas idénticas ($C\_{4,2}$). Aplicando la regla del producto, hay

$$
\dbinom{13}{1}\cdot\dbinom{4}{3}\cdot\dbinom{12}{1}\cdot\dbinom{4}{2} = 13\cdot4\cdot12\cdot6 = 3744
$$

manos que son *full*.

Finalmente, en el apartado (e), de los $13$ números disponibles en la baraja seleccionamos dos de ellos ($C\_{13,2}$), de los cuales, de entre las cuatro cartas asociadas a cada uno de ellos, escogeremos dos idénticas ($C\_{4,2}\cdot C\_{4,2}$). Por último, de las restantes cartas, $52-4-4=44$, tomaremos una cualquiera ($C\_{44,1}$). Aplicando la regla del producto hay 

$$
\dbinom{13}{2}\cdot\dbinom{4}{2}\cdot\dbinom{4}{2}\cdot\dbinom{44}{1} = 78\cdot6\cdot6\cdot44 = 123552
$$

manos que son *doble pareja*.
