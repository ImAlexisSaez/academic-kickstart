---
title: "Un primer contacto con ecuaciones diofánticas (II)"
slug: "un-primer-contacto-con-ecuaciones-diofanticas-ii"
subtitle: "Problema 46"
summary: "Problema 46: decidiendo cuándo existe solución y calculándola."

date: 2019-01-26T05:59:39+02:00
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
  caption: "Fotografía de [Kevin Bosc](https://unsplash.com/@kevinbosc), disponible en [Unsplash](https://unsplash.com/photos/4e9eeHdiBi0)."
---

**Problema 46:** Estudia cuáles de estas ecuaciones diofánticas tiene solución entera y, en su caso, calcúlala:

- (a) $25x+36y=10$. 
- (b) $200x+1768y=8$.
- (c\) $40x+50y=3$.
- (d) $213x+1123y=18$.
- (e) $14x+165y=1$.


***

Para el apartado (a), como $25=5^2$ y $36 = 2^2 \cdot3^2$, entonces $mcd(25,36)=1$, y, dado que $1|10$, estamos en condiciones de asegurar que la ecuación diofántica propuesta admite solución entera. Empecemos despejando la variable $x$, por ser aquella cuyo coeficiente asociado es más reducido. Así,

$$
x = \dfrac{10-36y}{25} = -y + \dfrac{10-11y}{25} = -y+x^{\prime},
$$

con

$$
x^{\prime}=\dfrac{10-11y}{25},
$$

esto es, $25x^{\prime} + 11y = 10$, luego

$$
y = \dfrac{10-25x^{\prime}}{11} = -2x^{\prime} + \dfrac{10-3x^{\prime}}{11} = -2x^{\prime}+y^{\prime},
$$

con

$$
y^{\prime}=\dfrac{10-3x^{\prime}}{11},
$$

es decir, $3x^{\prime} +11y^{\prime} =10$. Finalmente,

$$
x^{\prime} = \dfrac{10-11y^{\prime}}{3},
$$

por lo que basta probar para $y^{\prime}$ valores pertenecientes al *menor sistema completo de restos módulo* $3$. Para $y^{\prime} =2$, tenemos que $x^{\prime} = (-4)$, y deshaciendo ahora los cambios de variable llevados a cabo anteriormente,

$$
\begin{aligned}
y &= -2x^{\prime} + y^{\prime} = 8+2=10,\\
x &= -y + x^{\prime} = (-10) - 4 = -14,
\end{aligned}
$$

esto es, una solución particular para la ecuación diofántica planteada es $(x_0,y_0) = ((-14), 10)$, mientras que su solución general queda

$$
\begin{aligned}
x &= (-14) + 36t,\\
y &= 10 - 25t,
\end{aligned}
$$

con $t$ número entero.

De cara al apartado (b), comencemos calculando el máximo común divisor de $200$ y $1768$ por el *Algoritmo de Euclides*. Tenemos que,

$$
\begin{aligned}
1768 &= 200\cdot8 + 168,\\
200 &= 168\cdot1 +  32,\\
168 &=  32\cdot5 +   8,\\
32 &=   8\cdot4,
\end{aligned}
$$

por lo que $mcd(200,1768) = 8$ y, evidentemente, $8|8$, por lo que estamos en condiciones de asegurar que la ecuación diofántica propuesta en este apartado admite solución entera. Simplificando dicha ecuación por $8$ queda $25x + 221y = 1$. Despejemos la variable $x$, por ser aquella cuyo coeficiente es más reducido,

$$
x = \dfrac{1-221y}{25} = -8y + \dfrac{1-21y}{25} = -8y + x^{\prime},\quad\text{con}\quad x^{\prime} = \dfrac{1-21y}{25},
$$

esto es, $25x^{\prime} +21y = 1$, luego

$$
\begin{aligned}
y = \dfrac{1-25x^{\prime}}{21} = -x^{\prime} + \dfrac{1-4x^{\prime}}{21} = -x^{\prime} +y^{\prime},\quad\text{con}\quad y^{\prime} = \dfrac{1-4x^{\prime}}{21},
\end{aligned}
$$

es decir, $4x^{\prime} + 21y^{\prime} = 1$, por lo que

$$
\begin{aligned}
x^{\prime} = \dfrac{1-21y^{\prime}}{4},
\end{aligned}
$$

y ya únicamente basta probar valores para $y^{\prime}$ que pertenezcan al *menor sistema completo de restos módulo* $4$. Así, para $y^{\prime} = 1$, tenemos que $x^{\prime} = (-5)$, y deshaciendo los cambios de variable llevados a cabo arriba,

$$
\begin{aligned}
y &= -x^{\prime}+y^{\prime} = 5+1=6,\\
x &= -8y+x^{\prime} = (-48)-5 = (-53).
\end{aligned}
$$

Una solución para la ecuación diofántica planteada es $(x_0,y_0) = ((-53), 6)$, y su solución general queda

$$
\begin{aligned}
x &= (-53) + 1768t,\\
y &= 6-200t,
\end{aligned}
$$

con $t$ número entero.

A continuación, en el apartado (c\), como $40 = 2^3 \cdot5$ y $50 = 2\cdot5^2$, resulta que $mcd(40,50) = 10$, y dado que $10\nmid 3$, estamos en condiciones de asegurar que la ecuación diofántica propuesta no admite solución entera.

Para el apartado (d), empecemos calculando el máximo común divisor de $213$ y $1123$ utilizando el *Algoritmo de Euclides*,

$$
\begin{aligned}
1123 &= 213\cdot5 + 58,\\
213 &=  58\cdot3 + 39,\\
58 &=  39\cdot1 + 19,\\
39 &=  19\cdot2 +  1,\\
19 &=   1\cdot19,
\end{aligned}
$$

por lo que $mcd(213, 1123)=1$, esto es, la ecuación diofántica admite solución entera, ya que, obviamente, $1|18$. Por comodidad en los cálculos, empecemos llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 18x^{\prime},\\
y &= 18y^{\prime},
\end{aligned}
$$

y así queda, $213x^{\prime} + 1123y^{\prime}=1$. Despejando la variable $x^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido, llegamos a que

$$
x^{\prime} = \dfrac{1-1123y^{\prime}}{213} = -5y^{\prime} + \dfrac{1-58y^{\prime}}{213} = -5y^{\prime}+x^{\prime\prime},
$$

con

$$
x^{\prime\prime} = \dfrac{1-58y^{\prime}}{213},
$$

esto es, $213x^{\prime\prime} + 58y^{\prime} = 1$. Ahora,

$$
y^{\prime} = \dfrac{1-213x^{\prime\prime}}{58} = -3x^{\prime\prime} + \dfrac{1-39x^{\prime\prime}}{58} = -3x^{\prime\prime} + y^{\prime\prime},
$$

con

$$
y^{\prime\prime} = \dfrac{1-39x^{\prime\prime}}{58},
$$

es decir, $39x^{\prime\prime} + 58y^{\prime\prime} = 1$. A continuación,

$$
x^{\prime\prime} = \dfrac{1-58y^{\prime\prime}}{39} = -y^{\prime\prime} + \dfrac{1-19y^{\prime\prime}}{39} = -y^{\prime\prime} + x^{\prime\prime\prime},
$$

con

$$
x^{\prime\prime\prime} = \dfrac{1-19y^{\prime\prime}}{39},
$$

esto es, $39x^{\prime\prime\prime} + 19y^{\prime\prime}=1$. Acto seguido,

$$
y^{\prime\prime} = \dfrac{1-39x^{\prime\prime\prime}}{19} = -2x^{\prime\prime\prime} + \dfrac{1-x^{\prime\prime\prime}}{19} = -2x^{\prime\prime\prime} + y^{\prime\prime\prime},
$$

con

$$
y^{\prime\prime\prime} = \dfrac{1-x^{\prime\prime\prime}}{19},
$$

es decir, $x^{\prime\prime\prime} +19y^{\prime\prime\prime} = 1$, luego $x^{\prime\prime\prime} = 1-19y^{\prime\prime\prime}$. Una solución particular para esta última es $(x^{\prime\prime\prime}_0, y^{\prime\prime\prime}_0) = (1,0)$, y así, deshaciendo los cambios de variable realizados, arribamos a

$$
\begin{aligned}
y^{\prime\prime}_0 &= -2x^{\prime\prime\prime}_0 + y^{\prime\prime\prime}_0 = (-2)+0 = (-2),\\
x^{\prime\prime}_0 &= -y^{\prime\prime}_0 + x^{\prime\prime\prime}_0 = 2+1 = 3,\\
y^{\prime}_0  &= -3x^{\prime\prime}_0 + y^{\prime\prime}_0 = (-9) - 2 = (-11),\\
x^{\prime}_0  &= -5y^{\prime}_0 + x^{\prime\prime}_0 = 55 + 3 = 58,\\
y_0   &= 18y^{\prime}_0 = (-198),\\
x_0   &= 18x^{\prime}_0 = 1044,
\end{aligned}
$$

por lo que la solución general a la ecuación diofántica planteada es

$$
\begin{aligned}
x &= 1044 + 1123t,\\
y &= (-198) - 213t,
\end{aligned}
$$

con $t$ número entero.

Finalmente, en el apartado (e), como

$$
\begin{aligned}
14 &= 2\cdot7,\\
165 &= 3\cdot5\cdot11,
\end{aligned}
$$

entonces $mcd(14,165)=1$, por lo que la ecuación diofántica propuesta admite solución entera. Despejando la variable $x$, por ser aquella cuyo coeficiente asociado es más reducido, tenemos que

$$
x=\dfrac{1-165y}{14}=-11y+\dfrac{1-11y}{14}=-11y+x^{\prime},
$$

con

$$
x^{\prime}=\dfrac{1-11y}{14},
$$

esto es, $14x^{\prime}+11y=1$. Ahora,

$$
y=\dfrac{1-14x^{\prime}}{11}=-x^{\prime}+\dfrac{1-3x^{\prime}}{11}=-x^{\prime}+y^{\prime},
$$

con

$$
y^{\prime}=\dfrac{1-3x^{\prime}}{11},
$$

es decir, $3x^{\prime} +11y^{\prime}=1$. A continuación,

$$
\begin{aligned}
x^{\prime} =\dfrac{1-11y^{\prime}}{3},
\end{aligned}
$$

por lo que basta probar, para $y^{\prime}$, valores pertenecientes al *menor sistema completo de restos módulo* $3$. Para $y^{\prime}_0=2$, es cierto que $x^{\prime}_0 = (-7)$, y deshaciendo los cambios de variable llevados a cabo,

$$
\begin{aligned}
y_0 &= -x^{\prime}_0 + y^{\prime}_0 = 7+2=9,\\
x_0 &= -11y_0 + x^{\prime}_0 = (-99)-7 = (-106),
\end{aligned}
$$

llegamos a una solución particular para la ecuación diofántica planteada. Así, su solución general queda

$$
\begin{aligned}
x &= (-106) + 165t,\\
y &= 9-14t,
\end{aligned}
$$

con $t$ número entero.
