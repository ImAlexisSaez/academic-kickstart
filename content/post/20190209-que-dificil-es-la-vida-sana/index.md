---
title: "¡Qué difícil es la vida sana!"
slug: "que-dificil-es-la-vida-sana"
subtitle: "Problema 50"
summary: "Problema 50: cuando llenar la cesta de la compra se convierte en un acertijo."

date: 2019-02-09T05:59:39+02:00
lastmod: 2019-08-01T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Damian Denis](https://unsplash.com/@dwade), disponible en [Unsplash](https://unsplash.com/photos/JPibHbH9D6s)."
---

**Problema 50:** Se compran manzanas y naranjas, en total $12$ piezas de fruta y cuestan $1.32$ euros. Si una manzana vale $3$ céntimos más que una naranja y hay más manzanas que naranjas, ¿cuántas piezas de cada fruta compramos?

***

Sea $x$ el número de manzanas ($M$) compradas, de manera que el total de naranjas ($N$) adquiridas será $12-x$. Por otro lado, si denotamos por $y$ el precio de las naranjas ($P_N$), será $y+3$ el precio de las manzanas ($P_M$). Expresemos el desembolso realizado, $1.32$ euros, en céntimos, esto es, $132$ céntimos, para así trabajar con números enteros. De esta manera, multiplicando las cantidades por los precios e igualando al mencionado desembolso, podemos plantear la siguiente ecuación diofántica, 

$$
x(y+3) + (12-x)y=132,
$$ 

es decir, $xy+3x+12y-xy=132$, que, simplificando, queda la ecuación $3x+12y=132$. Como $mcd(3,12) = 3$ y $3|132$, estamos en condiciones de asegurar que la ecuación diofántica propuesta admite solución entera. Así pues, simplificando por el máximo común divisor queda 

$$
x+4y=44.
$$ 

Como, en total, se adquieren $12$ piezas de frutas y se compran más manzanas que naranjas, resulta que $7\leq x\leq 11$. Luego,

| $x$ ($M$) | $12-x$ ($N$) | $y+3$ ($P_M$) | $y$ ($P_N$) |
| --------- | ------------ | ------------- | ----------- |
| $7$       | $5$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $8$       | $4$          | $12$          | $9$         |
| $9$       | $3$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $10$      | $2$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $11$      | $1$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |

Por tanto, compramos $8$ manzanas, a $12$ céntimos cada una, y $4$ naranjas, a $9$ céntimos la unidad. A modo anecdótico, es cierto que para $x=12$ también encontraríamos solución entera al problema. No obstante, si interpretamos el enunciado de manera que al menos ha comprado una unidad de cada tipo de fruta, esta solución quedaría descartada automáticamente, pues impide la adquisición de naranjas.
