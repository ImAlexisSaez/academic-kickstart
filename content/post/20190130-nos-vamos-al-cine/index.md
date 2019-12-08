---
title: "¡Nos vamos al cine!"
slug: "nos-vamos-al-cine"
subtitle: "Problema 47"
summary: "Problema 47: ¡qué complicado es salir en familia!."

date: 2019-01-30T05:59:39+02:00
lastmod: 2019-08-01T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeff Golenski](https://unsplash.com/@jeffgolenski), disponible en [Unsplash](https://unsplash.com/photos/GA8KMclGoNw)."
---

**Problema 47:** Una persona ha comprado entradas para el cine para personas adultas por un precio de $640$ unidades monetarias (*um*) cada una y para menores de edad a $330$ *um*. Sabiendo que invirtió $7140$ *um* y que compró menos entradas de adultos que de menores, hallar el número de entradas que adquirió.

***

Sean $x$ el número de entradas para personas adultas compradas e $y$ el número de entradas para menores de edad compradas, con $x,y\in\mathbb{N}$. Dados los precios del enunciado y la cantidad total invertida, planteamos la siguiente ecuación diofántica: 

$$
640x + 330y = 7140,
$$ 

que es equivalente, simplificando por $10$, a 

$$
64x + 33y = 714.
$$

Utilicemos el *Algoritmo de Euclides* para hallar el $mcd(64,33)$ y decidir así si la ecuación admite o no solución entera. Tenemos que:

$$
\begin{aligned}
64 &= 33\cdot 1 + 31,\\
33 &= 31\cdot 1 + 2,\\
31 &= 2\cdot 15 + 1,\\
2 &= 1\cdot 2,
\end{aligned}
$$

luego $mcd(64,33) = 1$, y como $1|714$, estamos en condiciones de asegurar que la ecuación diofántica admite solución entera. Como $714$ es un número ciertamente elevado, comencemos llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 714x^{\prime},\\
y &= 714y^{\prime},
\end{aligned}
$$

de manera que la ecuación diofántica queda $64x^{\prime} + 33y^{\prime} = 1$ y nos invita a despejar $y^{\prime}$, por ser la variable cuyo coeficiente asociado es más reducido, de forma que 

$$
y^{\prime} = \dfrac{1-64x^{\prime}}{33}.
$$ 

Ahora, como el valor que figura en el denominador de la igualdad anterior es $33$, a continuación, tendríamos que darle a $x^{\prime}$, de manera ordenada, valores del *menor sistema completo de restos módulo* $33$ hasta hallar una solución particular.

No obstante, en lugar de llevar a cabo tan titánica labor, aprovecharemos las operaciones realizadas durante el *Algoritmo de Euclides* para descomponer la anterior fracción como sigue: 

$$
y^{\prime} = -x^{\prime} + \dfrac{1 - 31x^{\prime}}{33} = -x^{\prime} + y^{\prime\prime},
$$ 

con 

$$
y^{\prime\prime} = \dfrac{1 - 31x^{\prime}}{33},
$$ 

que equivale a $33y^{\prime\prime} = 1 - 31x^{\prime}$, de manera que ahora tendríamos que despejar $x^{\prime}$, quedando: 

$$
x^{\prime} = \dfrac{1-33y^{\prime\prime}}{31} = -y^{\prime\prime} + \dfrac{1-2y^{\prime\prime}}{31}=-y^{\prime\prime} + x^{\prime\prime},
$$ 

con 

$$
x^{\prime\prime} = \dfrac{1-2y^{\prime\prime}}{31},
$$ 

que equivale a $31x^{\prime\prime} = 1-2y^{\prime\prime}$, y despejando $y^{\prime\prime}$ tenemos que 

$$
y^{\prime\prime} = \dfrac{1-31x^{\prime\prime}}{2}.
$$ 

Tras aplicar en retiradas ocasiones la misma estrategia de descomposición, hemos alcanzado un valor razonable para el denominador de la anterior ecuación. Podemos así dar valores a $x^{\prime\prime}$, ya que únicamente tendríamos que probar $x^{\prime\prime} =0$, y $x^{\prime\prime} =1$ (que conforma el *menor sistema completo de restos módulo* $2$). Para $x^{\prime\prime} =0$, $y^{\prime\prime} \notin\mathbb{Z}$, pero para $x^{\prime\prime} =1$, $y^{\prime\prime} = -15$. Ahora,

$$
\begin{aligned}
x^{\prime} &= -y^{\prime\prime} + x^{\prime\prime} = 15+1 = 16,\\
y^{\prime} &= -x^{\prime} + y^{\prime\prime} = -16 -15 = -31,\\
x  &= 714x^{\prime} = 714\cdot 16 = 11424,\\
y  &= 714y^{\prime} = 714\cdot(-31) = -22134, 
\end{aligned}
$$

por lo que la solución particular queda

$$
\begin{aligned}
x_0 &= 11424,\\
y_0 &= -22134,
\end{aligned}
$$

mientras que la solución general es

$$
\begin{aligned}
x  &= 11424 + 33t,\\
y  &= -22134 - 64t,
\end{aligned}
$$

con $t\in\mathbb{Z}$. 

Ahora que hemos resuelto la ecuación diofántica, centrémonos en sacar el número de entradas. Por un lado, en ambos casos debe tratarse de un número mayor o igual que cero, es decir, tanto $x\geq0$, como $y\geq0$. Además, nos dicen que compró menos entradas de adultos que de menores, es decir, que $x<y$. Todo esto da lugar a las siguientes condiciones:

$$
\begin{aligned}
x  = 11424 + 33t&\geq0,\\
y  = -22134 - 64t&\geq0,\\
11424 + 33t &< -22134 - 64t,
\end{aligned}
$$

con $t\in\mathbb{Z}$. De la primera inecuación, se llega a que 

$$
t\geq -\dfrac{11424}{33},
$$ 

luego $t\geq -346$. De la segunda inecuación, se llega a que 

$$
t\leq -\dfrac{22134}{64},
$$ 

luego $t\leq -346$, con lo cual $t=346$, cantidad que, efectivamente, también verifica la tercera inecuación. Así,

$$
\begin{aligned}
x &= 11424 + 33\cdot(-346) = 6,\\
y &= -22134 - 64\cdot(-346) = 10,
\end{aligned}
$$

es decir, compró $6$ entradas para adultos y $10$ entradas para menores de edad.
