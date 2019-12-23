---
title: "Un primer contacto con ecuaciones diofánticas (V)"
slug: "un-primer-contacto-con-ecuaciones-diofanticas-v"
subtitle: "Problema 52"
summary: "Problema 52: ¡y subimos el número de incógnitas hasta cuatro!."

date: 2019-02-16T05:59:39+02:00
lastmod: 2019-02-16T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Brennan Burling](https://unsplash.com/@bwobble11), disponible en [Unsplash](https://unsplash.com/photos/vpaHZEYx35U)."
---

**Problema 52:** Halla las soluciones enteras de la ecuación 

$$
30x+42y+70z-105u=(-3).
$$

***

Como

$$
\begin{aligned}
30 &= 2\cdot3\cdot5,\\\\ 42 &= 2\cdot3\cdot7,\\\\ 70 &= 2\cdot5\cdot7,\\\\ 105 &= 3\cdot5\cdot7,
\end{aligned}
$$

entonces $mcd(30,42,70,105)=1$, por lo que estamos en condiciones de asegurar que la ecuación diofántica propuesta admite solución entera. A diferencia del [problema anterior](/2019/02/13/un-primer-contacto-con-ecuaciones-diofanticas-iv/), en esta ocasión ningún par de coeficientes está conformado por números primos entre sí. El procedimiento que seguiremos será entonces:

1. Escogeremos dos coeficientes cualesquiera.
2. Despejaremos para conseguir una ecuación diofántica con dos variables.
3. Dividiremos por el máximo común divisor de los mencionados coeficientes y resolveremos dicha ecuación.

De esta manera, si empezamos considerando los coeficientes asociados a las variables $x$ e $y$, como $mcd(30,42)=6$, la ecuación 

$$
30x+42y = (-3) - 70z + 105u
$$ 

la podemos simplificar por $6$, llegando así a

$$
5x+7y = \dfrac{(-3)-70z+105u}{6} = v,\quad\text{con}\quad v = \dfrac{(-3)-70z+105u}{6}.
$$

Llevando a cabo el cambio de variable $x = vx^{\prime}$ e $y = vy^{\prime}$, la ecuación queda $5x^{\prime} +7y^{\prime}=1$, y despejando la variable $x^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido,

$$
x^{\prime} = \dfrac{1-7y^{\prime}}{5},
$$

hallando que para $y^{\prime}_0 = (-2)$, entonces $x^{\prime}_0 = 3$. Deshaciendo el cambio de variable efectuado, $x_0 = 3v$ e $y_0 = -2v$ es una solución particular para la ecuación diofántica planteada unas líneas arriba, por lo que su solución general queda

$$
\begin{aligned}
x &= 3v + 7t,\\\\ y &= -2v - 5t,
\end{aligned}
$$

con $t$ número entero.

No obstante, recordemos que declaramos antes que 

$$
v = \dfrac{(-3) - 70z + 105u}{6},
$$ 

esto es $105u - 70z - 6v = 3$, que resulta ser una ecuación diofántica de tres variables del mismo tipo que aquella con la cual iniciamos este ejercicio (el máximo común divisor de sus coeficientes asciende a $1$, pero no existe algún par de ellos que sean primos entre sí), pero con una incógnita menos. Como $mcd(6,70,105) = 1$, estamos en condiciones de asegurar que esta última ecuación diofántica planteada admite solución entera. Tomando, por ejemplo, los coeficientes asociados a las variables $u$ y $z$, escribimos entonces la ecuación $105u-70z = 3+6v$, que podemos simplificar por $35$, quedando así

$$
3u-2z = \dfrac{3+6v}{35} = w,\quad\text{con}\quad w = \dfrac{3+6v}{35}.
$$

Al igual que antes, si consideramos el cambio de variable $u = wu^{\prime}$ y $z = wz^{\prime}$, la anterior ecuación se convierte en $3u^{\prime} -2z^{\prime} =1$. Despejando la variable $z^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido, 

$$
z^{\prime} = \dfrac{1-3u^{\prime}}{2}.
$$ 

Luego, para $u^{\prime}_0 =(-1)$ hallamos que $z^{\prime}_0 =(-2)$, y deshaciendo el cambio de variable efectuado, $u_0 = -w$ y $z_0 = -2w$ es una solución particular de esta ecuación diofántica, por lo que su solución general queda

$$
\begin{aligned}
u &= -w+2t^{\prime},\\\\ z &= -2w+3t^{\prime},
\end{aligned}
$$

con $t^{\prime}$ número entero.

Finalmente, como definimos antes $$w = \dfrac{3+6v}{35},$$ generamos al ecuación diofántica $35w-6v=3$, que sabemos admite solución entera pues $mcd(6,35) = 1$. Así, despejando ahora la variable $w$, $$w=\dfrac{3+6v}{35},$$ y entonces $v_0 = (-18)$ y $w_0=3$ es una solución particular para ella. De esta manera, su solución general es

$$
\begin{aligned}
v &= (-18)+35t^{\prime\prime},\\\\ w &= 3+6t^{\prime\prime}
\end{aligned}
$$

con $t^{\prime\prime}$ número entero. Únicamente nos resta reemplazar adecuadamente los resultados alcanzados para que así la solución quede expresada en función de valores enteros. Así,

$$
\begin{aligned}
x &= 3v+7t = (-54) + 7t + 105t^{\prime\prime},\\\\ y &= -2v-5t = 36 - 5t - 70t^{\prime\prime},\\\\ z &= -2w + 3t^{\prime} = (-6) + 3t^{\prime} - 12t^{\prime\prime},\\\\ u &= -w+2t^{\prime} = (-3) + 2t^{\prime} - 6t^{\prime\prime},
\end{aligned}
$$

con $t$, $t^{\prime}$ y $t^{\prime\prime}$ números enteros.
