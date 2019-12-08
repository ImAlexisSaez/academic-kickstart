---
title: "Un curioso múltiplo que todo número posee"
slug: "un-curioso-multiplo-que-todo-numero-posee"
subtitle: "Problema 64"
summary: "Problema 64: una aplicación del principio del palomar."

date: 2019-03-30T05:59:39+02:00
lastmod: 2019-08-04T00:00:01+01:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Principio del palomar", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Annie Spratt](https://unsplash.com/@anniespratt), disponible en [Unsplash](https://unsplash.com/photos/vEbdiy3vDPk)."
---

**Problema 64:** 

- (a) Demuestra que escogidos siete números enteros al azar, la diferencia entre dos de ellos es múltiplo de seis.
- (b) Demuestra que todo número entero $n$ tiene un múltiplo cuya expresión decimal está compuesta por ceros y unos.

***

Para el apartado (a), empecemos considerando un ejemplo concreto: sean los números enteros, escogidos al azar, $53$, $75$, $32$, $7$, $83$, $1$ y $10$. Si obtenemos el valor de la congruencia de cada uno de ellos módulo seis, es cierto que

$$
\begin{aligned}
53&\equiv 5\pmod{6},\\
75&\equiv 3\pmod{6},\\
32&\equiv 2\pmod{6},\\
 7&\equiv 1\pmod{6},\\ 
83&\equiv 5\pmod{6},\\
 1&\equiv 1\pmod{6},\\
10&\equiv 4\pmod{6}.
\end{aligned}
$$

Basta ahora tomar dos cuyo valor de la congruencia módulo seis coincida para encontrar un múltiplo de seis. Efectivamente, por ejemplo, 

$$
83-53=30 = 6\cdot5.
$$

En general, como el *menor sistema completo de restos módulo* $6$ está conformado por seis valores, $\\{0,1,2,3,4,5\\}$, dados siete números escogidos al azar sabemos, por el *Principio del palomar*, que al menos dos de ellos poseerán el mismo valor de la congruencia módulo seis. Esto es, existen al menos $x, y\in\mathbb{Z}$ tal que $x\equiv a\pmod{6}$ e $y\equiv a\pmod{6}$, con $a\in\\{0,1,2,3,4,5\\}$. Por consiguiente,

$$
(x-y)\equiv (a-a)\pmod{6}\equiv 0\pmod{6},
$$

es decir, la diferencia es múltiplo de seis.

Para el apartado (b) utilizaremos la misma estrategia, pero escogiendo los números con cautela, ya que buscamos que el múltiplo que nos interesa únicamente posea en su expresión decimal ceros y unos. Como antes, empecemos considerando un ejemplo concreto: sea $n=6$. Trabajemos pues con el conjunto de siete números 

$$
\{1,11,111,1111,11111,111111,1111111\},
$$ 

para el que, por el *Principio del palomar*, sabemos que al menos dos de ellos poseerán el mismo valor de su congruencia módulo seis. Efectivamente,

$$
1\equiv 1\pmod{6}\qquad\text{y}\qquad 1111\equiv 1\pmod{6}.
$$

Así, $(1111 - 1)\equiv 0\pmod{6}$, esto es, $1110 = 6\cdot185$ es múltiplo de $6$ y en su expresión decimal únicamente aparecen ceros y unos.

En general, dado un número natural $n$, consideramos el conjunto 

$$
\{1,11,111,1111,\ldots\}
$$ 

de $n+1$ elementos. Por el *Principio del palomar*, al menos dos de dichos elementos poseerán el mismo valor de su congruencia módulo $n$. Designemos por $a$ y $b$ a tales elementos que verifican $a\equiv x\pmod{n}$ y $b\equiv x\pmod{n}$, entonces $(a-b)\equiv 0\pmod{n}$, esto es, la diferencia entre ellos es múltiplo de $n$, y, por tal y como hemos construido el anterior conjunto, su expresión únicamente poseerá ceros y unos.

A modo anecdótico, si en el problema nos hubiesen solicitado demostrar que todo número entero $n$ tiene un múltiplo cuya expresión decimal está compuesta por ceros y doses, habría bastado considerar un conjunto del tipo 

$$
\{2,22,222,2222,\ldots\}.
$$

Variantes similares del problema únicamente exigen encontrar un conjunto adecuado al que aplicar la estrategia esbozada en párrafos anteriores.
