---
title: "Buscando ceros, muchos ceros, en un factorial"
slug: "buscando-ceros-muchos-ceros-en-un-factorial"
subtitle: "Problema 33"
summary: "Problema 33: trabajando con números enormes."

date: 2018-12-12T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Fórmula de Legendre", "Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [asoggetti](https://unsplash.com/@asoggetti), disponible en [Unsplash](https://unsplash.com/photos/wH3POmZAsio)."
---

**Problema 33:** 

- (a) ¿En cuántos ceros acaba el número $1000!$?
- (b) Demuestra que $1000!$ no es divisible por $2^{995}$,

***

Para el apartado (a), nuestra labor consistiría en contar el número de dieces que podemos encontrar en la expresión de $1000! = 1\cdot2\cdot3\cdots999\cdot1000$. No estamos en condiciones de emplear directamente la *Fórmula de Legendre*, puesto que $10$ no es un número primo, pero $10=2\cdot5$, de manera que nuestra tarea se reduce a buscar el número de veces que figura $5$ en la factorización en números primos de $1000!$ (porque $2$ aparecerá con mayor frecuencia, al ser menor que $5$, por ello nos interesa solamente hallar el número de cincos). 

Así, aplicando la mencionada fórmula,

$$
\begin{aligned}
v_5(1000!) &= \left\lfloor\dfrac{1000}{5}\right\rfloor + \left\lfloor\dfrac{1000}{5^2}\right\rfloor + \left\lfloor\dfrac{1000}{5^3}\right\rfloor + \left\lfloor\dfrac{1000}{5^4}\right\rfloor\\
&= 200 + 40 + 8 + 1 = 249,
\end{aligned}
$$

es decir, $1000!$ acaba en $249$ ceros.

Para el apartado (b), quizá de forma un tanto rebuscada, simplemente nos preguntan por el número de veces que aparece $2$ en la factorización en números primos de $1000!$, puesto que tal valor nos permitirá verificar la propiedad enunciada. Aplicando, de nuevo, la *Fórmula de Legendre*, tenemos que

$$
\begin{aligned}
v_2(1000!) &= \left\lfloor\dfrac{1000}{2}\right\rfloor + \left\lfloor\dfrac{1000}{2^2}\right\rfloor + \cdots + \left\lfloor\dfrac{1000}{2^9}\right\rfloor\\
&= 500 + 250 + 125 + 62 + 31 + 15 + 7 + 3 + 1 \\
&= 994,
\end{aligned}
$$

luego $2^{994}|1000!$, pero $2^{995}\nmid 1000!$, como queríamos demostrar.
