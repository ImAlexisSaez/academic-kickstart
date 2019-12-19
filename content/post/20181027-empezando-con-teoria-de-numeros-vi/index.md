---
title: "Empezando con teoría de números (VI)"
slug: "empezando-con-teoria-de-numeros-vi"
subtitle: "Problema 22"
summary: "Problema 22: trabajando con distintos sistemas de numeración."

date: 2018-10-27T05:59:39+02:00
lastmod: 2018-10-27T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Criterios de divisibilidad", "Problemas", "Teorema Fundamental de la Numeración", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Denys Nevozhai](https://unsplash.com/@dnevozhai), disponible en [Unsplash](https://unsplash.com/photos/P1Irb5y18-A)."
---

**Problema 22 (Comunidad Valenciana, 2006):** 

- a) Halla la base en que $$3753_{(x} - 3586_{(x} = 189_{(x}.$$
- b) Una vez hallado el valor de $x$, deduce el criterio de divisibilidad entre $x-1$ de dicha base.
- c) Después, justifica si alguno de los números dados es divisible por $x-1$ en dicha base.
- d) Por último, pasa el primero de los números dados a base $9$. 

***

Para el apartado a), por el *Teorema Fundamental de la Numeración*, sabemos que

$$
\begin{aligned}
3753_{(x} &= 3x^0 + 5x^1 + 7x^2 + 3x^3 = 3+5x+7x^2+3x^3,\\\\ 3586_{(x} &= 6x^0 + 8x^1 + 5x^2 + 3x^3 = 6+8x+5x^2+3x^3,\\\\ 189_{(x} &= 9x^0 + 8x^1 + 1x^2 = 9+8x+x^2,
\end{aligned}
$$

por lo que la igualdad planteada en el enunciado es equivalente a:

$$
3+5x+7x^2 + 3x^3 - (6+8x+5x^2 + 3x^3) = 9+8x+x^2.
$$

Operando, esta se convierte en $x^2 - 11x-12=0$, y como 

$$
x^2 - 11x-12 = (x-12)(x+1),
$$ 

concluimos que la base del sistema de numeración en la que se satisface la anterior igualdad es $x=12$ ($x=-1$ queda descartada automáticamente pues toda base ha de ser un número natural estrictamente mayor que $1$. Es más, a modo anecdótico, si las soluciones hubiesen sido $x=7$ y $x=12$, también habríamos descartado de forma automática la primera, pues en la expresión de los números implicados en la igualdad hay dígitos mayores o iguales que $7$).

Para el apartado b), consideremos el número de $n$ cifras $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ en base $12$. Utilizando el mismo resultado anterior, sabemos que podemos expresarlo como

$$
a_{n-1}a_{n-2}\cdots a_1a_0 = a_0+a_112+\cdots+a_{n-2}12^{n-1}+a_{n-1}12^{n-1}.
$$

De cara a encontrar el criterio de divisibilidad del $11$ emplearemos las propiedades de las congruencias sobre las potencias de $12$, buscando una condición sobre los dígitos del número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que

$$
a_0+a_112+a_212^2+\cdots+a_{n-1}12^{n-1}\equiv 0\pmod{11}.
$$

Ahora, como $12\equiv 1\pmod{11}$, fácilmente apreciamos que 

$$
12^2\equiv 1^2\pmod{11}\equiv 1\pmod{11}
$$ 

y, en general, $12^i\equiv 1\pmod{11}$, para cada $i\in\mathbb{N}$, por lo que

$$
a_0+a_112+\cdots+a_{n-1}12^{n-1}\equiv (a_0+a_1+\cdots+a_{n-1})\pmod{11},
$$

es decir, el número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$, en base $12$, es divisible por $11$ siempre y cuando la suma de sus dígitos sea múltiplo de $11$.

En el apartado c), a partir de la condición obtenida arriba, podemos concluir que

- $3+7+5+3 = 18\equiv 7\pmod{11}$,
- $3+5+8+6 = 22\equiv 0\pmod{11}$,
- $1+8+9 = 18\equiv 7\pmod{11}$,

esto es, $3586_{(12}$ es el único número, de entre los tres propuestos, divisible por $11$.

Finalmente, en el apartado d) tenemos que

$$
\begin{aligned}
3753_{(12} &= 3\cdot12^0 + 5\cdot12^1 + 7\cdot12^2 + 3\cdot12^3 \\\\ &= 5184+1008+60+3 \\\\ &= 6255_{(10},
\end{aligned}
$$

y dividiendo ahora sucesivamente por $9$,

$$
\begin{aligned}
6255 &= 9\cdot 695 + 0,\\\\ 695 &= 9\cdot 77 + 2,\\\\ 77 &= 9\cdot 8 + 5,
\end{aligned}
$$

arribamos a que $6255_{(10} = 8520_{(9}$, de manera que $3753_{(12} = 8520_{(9}$ por la unicidad que nos concede el *Teorema Fundamental de la Numeración*.
