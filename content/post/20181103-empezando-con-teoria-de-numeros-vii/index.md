---
title: "Empezando con teoría de números (VII)"
slug: "empezando-con-teoria-de-numeros-vii"
subtitle: "Problema 23"
summary: "Problema 23: seguimos trabajando con múltiplos y criterios de divisibilidad."

date: 2018-11-03T05:59:39+02:00
lastmod: 2019-07-28T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Criterios de divisibilidad", "Problemas", "Teorema Fundamental de la Numeración", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Finding Dan | Dan Grinwis](https://unsplash.com/@finding_dan), disponible en [Unsplash](https://unsplash.com/photos/bTFNVc4pWvY)."
---

**Problema 23:** Sea $n$ un número natural. Sea $A_n = 2^n + 2^{2n} + 2^{3n}$.

- a) Demuestra que para todo $n$, $A_{n+3}\equiv A_n\pmod{7}$.
- b) ¿Para qué valores de $n$, $A_n$ es múltiplo de $7$?
- c) Los números en base $2$, $1110$, $1010100$ y $1001001000$, ¿son divisibles por $7$?

***

Para el apartado a),

$$
A_{n+3} = 2^{n+3} + 2^{2(n+3)} + 2^{3(n+3)} = 2^{n+3} + 2^{2n+6} + 2^{3n+9}.
$$

Ahora bien, aprovechando que $2^3=8\equiv 1\pmod{7}$, tenemos que

$$
A_{n+3} = 2^3\cdot2^n + (2^3)^2\cdot2^{2n} + (2^3)^3\cdot 2^{3n} \equiv (2^n + 2^{2n} + 2^{3n})\pmod{7},
$$

es decir, $A_{n+3}\equiv A_n\pmod{7}$, como queríamos demostrar.

En cuanto al apartado b), teniendo presente el resultado alcanzado en el apartado anterior, estudiemos qué sucede para tres números consecutivos. Por comodidad de cara a los cálculos, tomaremos $1$, $2$ y $3$ como valores para $n$, y así,

$$
\begin{aligned}
A_1 &= 2^1+2^2+2^3 = 14\equiv 0\pmod{7},\\
A_2 &= 2^2+2^4+2^6 = 84\equiv 0\pmod{7},\\
A_3 &= 2^3+2^6+2^9 = 584\equiv 3\pmod{7},
\end{aligned}
$$

es decir, como $A_{1}$ es múltiplo de $7$ y se satisface la propiedad dada en a), que podemos escribir como $( A_{n + 3} - A_{n} ) \equiv 0 \pmod{7}$, concluimos que $A_{4}$ será múltiplo de $7$ también, así como $A_{7}, A_{10}, A_{13}$ y, en general, los números de la forma $n=3k+1$, con $k\in\mathbb{Z}$, sin más que aplicar reiteradamente la citada propiedad. Un argumento similar se podría esgrimir para los números de la forma $n=3k+2$, con $k\in\mathbb{Z}$, a la vista del resultado alcanzado para $A_2$. De igual manera, este cauce de pensamiento nos llevaría a descartar que cualquier número de la forma $n=3k$, con $k\in\mathbb{Z}$, vaya a ser múltiplo de $7$, ya que $A_3$ no lo es. En conclusión, $A_n$ será múltiplo de $7$ para todos aquellos valores de $n$ que no sean múltiplo de $3$.

Finalmente, en el apartado c), por el *Teorema Fundamental de la Numeración*, sabemos que podemos escribir

$$
\begin{aligned}
1110_{(2} &= 2^1+2^2+2^3 = A_1,\\
1010100_{(2} &= 2^2+2^4+2^6 = A_2,\\ 
1001001000_{(2} &= 2^3+2^6+2^9 = A_3,
\end{aligned}
$$

y por lo establecido para el apartado anterior, $A_{1}$ y $A_{2}$ son divisibles por $7$, mientras que $A_{3}$ no lo es. De esta manera, los números $1110_{(2}$ y $1010100_{(2}$ son divisibles por $7$, mientras que $1001001000_{(2}$ no lo es.
