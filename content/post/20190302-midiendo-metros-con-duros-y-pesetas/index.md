---
title: "Midiendo metros con duros y pesetas"
slug: "midiendo-metros-con-duros-y-pesetas"
subtitle: "Problema 56"
summary: "Problema 56: un curioso juego de monedas."

date: 2019-03-02T05:59:39+02:00
lastmod: 2019-08-04T00:00:01+02:00

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
  caption: "Fotografía de [Kurt Cotoaga](https://unsplash.com/@kydroon), disponible en [Unsplash](https://unsplash.com/photos/cqbLg3lZEpk)."
---

**Problema 56:** El diámetro de una moneda de $5$ pesetas es de $37$ mm y el de una peseta es de $23$ mm, ¿de cuántas maneras puede obtenerse la longitud de un metro alineando monedas de $5$ pesetas y de pesetas?

***

Sea $x$ el número de monedas de $5$ pesetas e $y$ la cifra total de monedas de $1$ peseta. Expresando todas las cantidades involucradas en el enunciado del ejercicio en milímetros, para así trabajar con números enteros, hemos de resolver la ecuación diofántica 

$$
37x+23y=1000,
$$ 

para encontrar el número de maneras en las que puede obtenerse un metro alineando monedas de los dos tipos indicados. 

Como $23$ y $37$ son números primos, tenemos que $mcd(23,37)=1$, y dado que, trivialmente, $1|1000$, estamos en condiciones de asegurar que la anterior ecuación diofántica planteada admite solución entera. De cara a su resolución, para empezar, llevemos a cabo el cambio de variable

$$
\begin{aligned}
x &= 1000x^{\prime},\\
y &= 1000y^{\prime}
\end{aligned}
$$

de manera que la ecuación diofántica se transforma en $37x^{\prime} + 23y^{\prime} = 1$. Utilizando el *Algoritmo de Euclides*, como

$$
\begin{aligned}
37 &= 23\cdot1 + 14,\\
23 &= 14\cdot1 +  9,\\
14 &=  9\cdot1 +  5,\\
 9 &=  5\cdot1 +  4,\\
 5 &=  4\cdot1 +  1,\\
 4 &=  1\cdot4,
\end{aligned}
$$

además de haber comprobado que $mcd(23,37)=1$, podemos encontrar una solución particular a la ecuación diofántica sin más que expresar dicho máximo común divisor como combinación lineal de $23$ y $37$. Para ello,

$$
\begin{aligned}
1 &= 5 - 4\cdot1\\
&= 5 - 1\cdot(9\cdot1 - 5) \\
&= (-9) + 2\cdot5 = (-9) + 2(14\cdot1 - 9) \\
&= 2\cdot14 - 3\cdot9 \\
&= 2\cdot14 - 3(23\cdot1 - 14) \\
&= (-3)\cdot23 + 5\cdot14 \\
&= (-3)\cdot23 + 5(37 - 23\cdot1) \\
&= 5\cdot37 - 8\cdot23,
\end{aligned}
$$

y dado que, recordemos, la ecuación diofántica es $37x^{\prime} +23y^{\prime} =1$, igualando, arribamos a que $x^{\prime}_0=5$ e $y^{\prime}_0=(-8)$. Deshaciendo ahora el cambio de variable realizado,

$$
\begin{aligned}
x_0 &= 1000x^{\prime}_0 = 5000,\\
y_0 &= 1000y^{\prime}_0 = (-8000),
\end{aligned}
$$

es una solución particular para la ecuación diofántica $37x+23y=1000$. Por tanto, su solución general queda

$$
\begin{aligned}
x &= 5000 + 23t,\\
y &= (-8000) - 37t,
\end{aligned}
$$

con $t$ número entero. Dado que el número de monedas que alineamos ha de ser mayor o igual que cero, planteamos las inecuaciones,

$$
5000 + 23t\geq 0\qquad\text{y}\qquad (-8000) - 37t\geq 0,
$$

esto es,

$$
-\dfrac{5000}{23}\leq t\leq -\dfrac{8000}{37},
$$

es decir, $(-217.4)\leq t\leq (-216.2)$ y como $t$ ha de ser un número entero, únicamente deja como solución $t=(-217)$. Por tanto,

$$
\begin{aligned}
x &= 5000 + 23\cdot(-217) = 9,\\ 
y &= (-8000) - 37\cdot(-217) = 29,
\end{aligned}
$$

esto es, solamente podemos obtener un metro alineando las monedas indicadas de una manera y es utilizando $9$ monedas de $5$ pesetas y $29$ monedas de $1$ peseta.
