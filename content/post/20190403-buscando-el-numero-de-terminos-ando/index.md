+++
title = "Buscando el número de términos ando"
slug  = "buscando-el-numero-de-terminos-ando"
subtitle = "Problema 65"
summary  = "Problema 65: trabajando con desarrollos de polinomios."

date     = 2019-04-03T05:59:39+02:00
#lastmod = 2019-04-03T07:15:55+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Estrategia de barras y estrellas", "Problemas", "Teorema del binomio"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Maksym Ivashchenko](https://unsplash.com/@maksymiv), disponible en [Unsplash](https://unsplash.com/photos/roKIwcialYo)."
+++

**Problema 65:** ¿Cuántos términos tiene la expansión de $(x\_1+x\_2+\cdots+x\_s)^n$?

***

Empecemos estudiando algunos casos sencillos para comprobar si podemos inferir algún patrón de comportamiento. Por ejemplo, sabemos que

$$
(x+y)^2 = x^2 + y^2 + xy,
$$

es decir, la expansión de $(x+y)^2$ posee tres términos. Análogamente,

$$
(x+y)^3 = x^3 + 3x^2y + 3xy^2 + y^3,
$$

esto es, la expansión de $(x+y)^3$ posee cuatro términos. En general, por el *Teorema del binomio*,

$$
(x+y)^n = \dbinom{n}{0}x^ny^0 + \dbinom{n}{1}x^{n-1}y^1+\cdots+\dbinom{n}{n}x^0y^n.
$$

Rápidamente observamos que cada uno de los sumandos del anterior desarrollo posee una peculiar característica: la suma de las potencias de $x$ e $y$ asciende a $n$, el grado del binomio. Esto es cierto asimismo para los dos primeros ejemplos que consideramos arriba, sin más que escribirlos de la siguiente manera para que quede patente,

$$
\begin{aligned}
(x+y)^2 &= x^2y^0 + y^2x^0 + x^1y^1,\\\\ (x+y)^3 &= x^3y^0 + 3x^2y^1 + 3x^1y^2 + y^3x^0.
\end{aligned}
$$

Así pues, estamos interesados en saber de cuántas maneras podemos repartir el grado entre las variables involucradas en el desarrollo. En los ejemplos anteriores, $x$ e $y$ jugarían el papel de dos urnas indistinguibles, mientras que el grado $n$ adoptaría el rol de las $n$ bolas idénticas. Utilizando la estrategia de *barras y estrellas*, necesitamos una *barra* para representar sobre la recta real las dos urnas y buscamos ubicar luego $n$ *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de términos en la expansión de un binomio de grado $n$, equivale a la cantidad de permutaciones con repetición de $n+1$ elementos, donde uno de ellos se repite una vez, mientras que el otro lo hace en $n$ ocasiones. Así, hay

$$
PR\_{n+1}^{1,n} = \dfrac{(n+1)!}{1!\cdot n!} = n+1
$$

términos en el desarrollo de un binomio de grado $n$.

Por otro lado, 

$$
(x+y+z)^2 = x^2+y^2+z^2+2xy+2xz+2yz,
$$

esto es, el desarrollo de $(x+y+z)^2$ posee seis términos. Si lo escribimos como

$$
(x+y+z)^2 = x^2y^0z^0 + x^0y^2z^0 + x^0y^0z^2 + 2x^1y^1z^0 + 2x^1y^0z^1 + 2x^0y^1z^1,
$$

rápidamente apreciamos que estamos repartiendo el grado, $2$, en tres urnas indistinguibles, $x$, $y$ y $z$. Aplicando, como antes, la estrategia de *barras y estrellas*, dicha acción la podemos llevar a cabo de

$$
PR\_{2+2}^{2,2} = PR_{4}^{2,2} = \dfrac{4!}{2!\cdot 2!} = 6
$$

formas posibles.

En general, para la expresión $(x\_1+x\_2+\cdots+x\_s)^n$ vamos a considerar que disponemos de $s$ urnas indistinguibles, las respectivas variables $x\_1,x\_2,\ldots,x\_s$. En ellas buscamos repartir $n$ bolas idénticas, el grado $n$. Utilizando la estrategia de *barras y estrellas*, necesitamos $s-1$ *barras* para representar sobre la recta real las $s$ urnas y buscamos ubicar luego $n$ *estrellas* en los huecos que dicha configuración produce. Por tanto, el número de términos del desarrollo de $(x\_1+x\_2+\cdots+x\_s)^n$, equivale a la cantidad de permutaciones con repetición de $s-1+n$ elementos, donde uno de ellos se repite $s-1$ veces, mientras que el otro hace en $n$ ocasiones. Así, hay

$$
PR\_{s-1+n}^{s-1,n} = \dfrac{(n+s-1)!}{n!(s-1)!}
$$

términos en el desarrollo de $(x\_1+x\_2+\cdots+x\_s)^n$.
