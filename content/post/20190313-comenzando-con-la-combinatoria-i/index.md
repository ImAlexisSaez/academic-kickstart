+++
title = "Comenzando con la combinatoria (I)"
slug  = "comenzando-con-la-combinatoria-i"
subtitle = "Problema 59"
summary  = "Problema 59: primeros pasos."

date     = 2019-03-13T05:59:39+02:00
#lastmod = 2019-04-08T10:40:36+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Matteo Marinelli](https://unsplash.com/@rtearth), disponible en [Unsplash](https://unsplash.com/photos/P6uF0I_okfk)."
+++

**Problema 59:** 

- (a) ¿De cuántas formas se pueden sentar ocho personas en una fila de ocho asientos?
- (b) ¿Cuántas palabras distintas de diez letras se pueden formar con las letras $A$, $B$, $C$ y $D$?
- (c\) ¿De cuántas formas pueden huir diez niños de la policía en un cruce de calles?
- (d) ¿Cuántas distribuciones se pueden conseguir lanzando diez monedas?
- (e) ¿De cuántas formas se pueden obtener cinco caras y cinco cruces en el apartado anterior?
- (f) ¿Cuántos números de $4$ cifras se pueden formar con los dígitos $1,2,3,\ldots, 9$?
- (g) ¿Cuántas distribuciones de cumpleaños pueden darse entre diez amigos?

***

Para el apartado (a), dado que el orden importa y utilizamos todos los elementos, sin que ninguno de ellos se repita, buscamos la cantidad de permutaciones de ocho elementos. Así, $P_8 = 8! = 40320$ es el número de formas en que se pueden sentar ocho personas en una fila de ocho asientos.

En el apartado (b), el orden vuelve a importar y, obviamente, hemos de permitir la repetición de las letras para conformar las palabras, por lo que ahora la herramienta adecuada para contar será el total de variaciones de cuatro elementos tomadas de diez en diez. Por tanto, hay $VR_{4,10} = 4^{10} = 1048576$ palabras distintas de diez letras conformadas a partir de las letras $A$, $B$, $C$ y $D$.

En cuanto al apartado (c\), hemos de ser cautos a la hora de escoger quién juega el papel de los ''elementos'' para contabilizar el total de maneras en que realizar la acción. En esta ocasión, son las calles. Si consideramos un cruce estándar de cuatro de ellas (y las denotamos por $a$, $b$, $c$ y $d$), una posible forma de escapar de la policía consistiría en que todos los niños optasen por la calle $a$, generando así el valor $(a,a,\ldots,a)$. Si el primer niño escogiese la calle $b$ y el resto la $a$, tendríamos el valor $(b,a,a,\ldots,a)$, y así sucesivamente. Por tanto, como importa el orden y alguna de las calles estará repetida dentro de las opciones de la huida, buscamos el número de variaciones con repetición de cuatro elementos tomados de diez en diez. Como antes, $VR_{4,10} = 4^{10}$ es el número de formas en que pueden huir diez niños de la policía en un cruce de calles.

Para el apartado (d), un tanto ambiguo, asumiremos que están interesados en conocer el número de secuencias de caras y cruces que se pueden encontrar lanzando diez monedas. Con esta reformulación, es claro que son dos los elementos protagonistas, cara y cruz, y consideraremos que el orden importa porque, suponemos, las monedas son distinguibles. Por tanto, buscamos el número de variaciones con repetición de dos elementos tomados de diez en diez, esto es, hay $VR_{2,10} = 2^{10} = 1024$ posibles secuencias de caras y cruces cuando se lanzan diez monedas.

A continuación, en el apartado (e), como el orden continúa siendo importante y cada elemento se repite un número fijo de veces, estamos interesados en la cantidad de permutaciones con repetición de diez elementos, donde tanto un elemento, como el otro, se repite en cinco ocasiones. Es decir, hay

$$
P(10;5,5) = PR_{10}^{5,5} = \dfrac{10!}{5!\cdot 5!} = \dfrac{10\cdot9\cdot8\cdot7\cdot6}{5!} = 252
$$

formas de obtener cinco caras y cinco cruces al lanzar diez monedas.

En el apartado (f) hemos de considerar dos opciones posibles, en función de si admitimos o no repetición de los números. En caso afirmativo, al importar el orden y permitir repetición de los números, estamos interesados en el número de variaciones con repetición de nueve elementos tomados de cuatro en cuatro, esto es, hay $VR\_{9,4} = 9^4 = 6561$ números de cuatro cifras conformados a partir de los dígitos $1,2,3,\ldots,9$ que pueden poseer, además, dígitos repetidos. En caso negativo, el orden continúa siendo importante, pero ahora no permitimos la repetición de cifras, por lo que estamos interesados en hallar el número de variaciones de nueve elementos tomados de cuatro en cuatro, es decir, $V_{9,4} = 9\cdot8\cdot7\cdot6 = 3024$ posibilidades.

Finalmente, en el apartado (g), si todos los amigos celebrasen su cumpleaños el primer día del año, se generaría el valor $(1,1,\ldots,1)$. Si el primer amigo lo celebrase el quinto día del año y el resto el tercer día, se conformaría el valor $(5,3,3\ldots,3)$. Así, vemos que los elementos son los días del año, $365$, que los vamos a tomar de diez en diez. Como admitimos la posibilidad de que dos amigos cumplan año el mismo día, esto es, de repetir elemento, e importa el orden, estamos interesados en hallar el número de variaciones con repetición de $365$ elementos tomados de diez en diez. Así, hay $VR_{365,10} = 365^{10}$ distribuciones de cumpleaños posibles entre los diez amigos.