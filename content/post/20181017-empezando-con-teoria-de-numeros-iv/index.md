+++
title = "Empezando con teoría de números (IV)"
slug  = "empezando-con-teoria-de-numeros-iv"
subtitle = "Problema 20"
summary  = "Problema 20: descifrando algunos criterios de divisibilidad."

date     = 2018-10-17T05:59:39+02:00
#lastmod = 2019-04-01T21:52:10+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Criterios de divisibilidad", "Problemas", "Teorema Fundamental de la Numeración", "Teoría de números"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Chris Lawton](https://unsplash.com/@chrislawton), disponible en [Unsplash](https://unsplash.com/photos/t-EYluv7mW0)."
+++

**Problema 20:** Calcula las reglas de divisibilidad para $3$ y para $9$.

***

Consideremos el número de $n$ cifras $a\_{n-1}a\_{n-2}\cdots a_2a_1a_0$ en base $10$. Sabemos, por el *Teorema Fundamental de la Numeración*, que podemos expresarlo como

$$
a\_{n-1}a\_{n-2}\cdots a\_1a\_0 = a\_0+a\_110+\cdots+a\_{n-2}10^{n-2}+a\_{n-1}10^{n-1}.
$$

Para encontrar el criterio de divisibilidad del $3$ utilizaremos las propiedades de las congruencias sobre las potencias de $10$, buscando una condición sobre los dígitos del número $a\_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que 

$$
a\_0+a\_110+a\_210^2+\cdots+a\_{n-2}10^{n-2}+a\_{n-1}10^{n-1}\equiv 0\pmod{3},
$$ 

esto es, dicho número sea múltiplo de $3$.

Así, como $10\equiv 1\pmod{3}$, fácilmente apreciamos que $10^2\equiv 1^2\pmod{3}\equiv 1\pmod{3}$ y, en general, $10^i\equiv 1\pmod{3}$, para cada $i\in\mathbb{N}$, por lo que

$$
a\_0+a\_110+\cdots+a\_{n-1}10^{n-1}\equiv (a\_0+a\_1+\cdots+a\_{n-1})\pmod{3},
$$

es decir, el número $a\_{n-1}a_{n-2}\cdots a_2a_1a_0$ es divisible por $3$ siempre y cuando la suma de sus dígitos sea múltiplo de $3$.

Por lo que respecta al criterio de divisibilidad del $9$, el modo de proceder es muy similar al mostrado arriba. Volvemos a buscar una condición sobre los dígitos del número $a\_{n-1}a\_{n-2}\cdots a\_2a\_1a\_0$ de manera que 

$$
a\_0+a\_110+a\_210^2+\cdots+a\_{n-2}10^{n-2}+a\_{n-1}10^{n-1}\equiv 0\pmod{9},
$$ 

esto es, dicho número sea múltiplo de $9$. Al igual que antes, como $10\equiv 1\pmod{9}$, se sigue que $10^2\equiv 1^2\pmod{9}\equiv 1\pmod{9}$ y, en general, $10^i\equiv 1\pmod{9}$, para cada $i\in\mathbb{N}$, por lo que

$$
a\_0+a\_110+\cdots+a\_{n-1}10^{n-1}\equiv (a\_0+a\_1+\cdots+a\_{n-1})\pmod{9},
$$

es decir, el número $a\_{n-1}a_{n-2}\cdots a_2a_1a_0$ es divisible por $9$ siempre y cuando la suma de sus dígitos sea múltiplo de $9$. Expresado de otra manera, todo número es congruente con la suma de sus cifras módulo $9$. Por ejemplo, $162\equiv 0\pmod{9}$, ya que $1+6+2=9$ y $9\equiv 0\pmod{9}$; mientras que $172\equiv 1\pmod{9}$, puesto que $1+7+2=10$ y $10\equiv 1\pmod{9}$. 

*Nota*: es más, el último criterio de divisibilidad hallado se puede generalizar como sigue: ''*dado un sistema de numeración cuya base $b$ es mayor que $2$, un número es divisible por $b-1$ siempre que la suma de sus dígitos sea congruente con $0$ módulo $b-1$*''.