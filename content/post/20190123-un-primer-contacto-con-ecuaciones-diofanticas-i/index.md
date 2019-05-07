+++
title = "Un primer contacto con ecuaciones diofánticas (I)"
slug  = "un-primer-contacto-con-ecuaciones-diofanticas-i"
subtitle = "Problema 45"
summary  = "Problema 45: matemáticas de caballos y vacas."

date     = 2019-01-23T05:59:39+02:00
#lastmod = 2019-04-06T17:47:40+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Ecuaciones diofánticas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [John Westrock](https://unsplash.com/@johnwestrock), disponible en [Unsplash](https://unsplash.com/photos/ZA2vDly2om0)."
+++

**Problema 45:** 

- (a) Sea $c$ un número entero positivo tal que $10\leq c\leq 100$. ¿Cuál es el valor mínimo de $c$ para el cual la ecuación $84x+990y=c$ admite  solución entera?
- (b) Un hombre compra caballos y vacas, pagando $1770$ euros. Una vaca cuesta $21$ euros y un caballo $31$ euros. ¿Cuántos caballos y vacas ha comprado?

***

Para el apartado (a), como

$$
\begin{aligned}
 84 &= 2^2\cdot3\cdot7,\\\\ 990 &= 2\cdot3^2\cdot5\cdot11,
\end{aligned}
$$

entonces $mcd(84, 990) = 6$. Para que la ecuación diofántica planteada admita soluciones enteras, $6$ ha de dividir a $c$ y, dado que buscamos el valor mínimo de $c$, nuestra tarea se reduce pues a encontrar el primer múltiplo de $6$ que pertenezca al intervalo $[10,100]$. La solución será, por tanto, $c=12$.

En cuanto al apartado (b), consideremos $x$ el número de vacas compradas e $y$ el total de caballos adquiridos. Dados sus respectivos precios y el importe total desembolsado, planteamos la ecuación diofántica 

$$
21x + 31y = 1770.
$$ 

Como $mcd(21,31) = 1$ y $1|1770$, estamos en condiciones de asegurar que la anterior ecuación diofántica admite solución entera. Para aliviar cálculos, empecemos llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 1770x^{\prime},\\\\ y &= 1770y^{\prime},
\end{aligned}
$$

con lo cual queda $21x^{\prime} + 31y^{\prime} = 1$. Despejando ahora la variable $x^{\prime}$,

$$
\begin{aligned}
x^{\prime} = \dfrac{1-31y^{\prime}}{21} = -y^{\prime} + \dfrac{1 - 10y^{\prime}}{21} = -y^{\prime} + x^{\prime\prime},
\end{aligned}
$$

con

$$
x^{\prime\prime} = \dfrac{1-10y^{\prime}}{21},
$$

es decir, $21x^{\prime\prime} = 1-10y^{\prime}$, y despejando ahora la variable $y^{\prime}$,

$$
\begin{aligned}
y^{\prime} = \dfrac{1-21x^{\prime\prime}}{10},
\end{aligned}
$$

ecuación para la que, por tanteo, rápidamente observamos que si $x^{\prime\prime} = 1$, entonces $y^{\prime} = (-2)$. Deshaciendo ahora los cambios de variable realizados,

$$
\begin{aligned}
x^{\prime} &= -y^{\prime} + x^{\prime\prime} = 2 + 1 = 3,\\\\ x  &= 1770x^{\prime} = 1770\cdot3 = 5310,\\\\ y  &= 1770y^{\prime} = 1770\cdot(-2) = -3540,
\end{aligned}
$$

llegamos a una solución particular de la ecuación diofántica propuesta. Así, su solución general queda

$$
\begin{aligned}
x &= 5310 + 31t,\\\\ y &= (-3540) - 21t,
\end{aligned}
$$

con $t$ número entero. El número de animales que ha comprado de cada clase ha de ser, necesariamente, mayor o igual que cero, por lo que planteamos las inecuaciones,

$$
\begin{aligned}
5310 + 31t &\geq 0\Rightarrow t\geq -\dfrac{5310}{31} = -171.29,\\\\ -3540-21t  &\geq 0\Rightarrow t\leq -\dfrac{3540}{21} = -168.57.
\end{aligned}
$$
Como $t$ ha de ser entero, concluimos que $-171\leq t\leq -169$. Por tanto,

| $t$ | $x$ (vacas) | $y$ (caballos) |
| --- | ----------- | -------------- |
| $-171$ | $9$ | $51$ |
| $-170$ | $40$ | $30$ |
| $-169$ | $71$ | $9$ |

Siendo así la posible respuesta, al interrogante planteado en el enunciado del ejercicio, cualquiera de las anteriores tres posibilidades.
