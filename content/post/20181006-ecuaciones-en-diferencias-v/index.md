---
title: "Repasando ecuaciones en diferencias lineales (V)"
slug: "repasando-ecuaciones-en-diferencias-lineales-v"
subtitle: "Problema 16"
summary: "Problema 16: volvemos a trabajar con números complejos."

date: 2018-10-06T05:59:39+02:00
lastmod: 2019-07-27T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Ecuaciones en diferencias", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Oliver Plattner](https://unsplash.com/@oplattner), disponible en [Unsplash](https://unsplash.com/photos/Plt0vHDRb9U)."
---

**Problema 16:** Resuelve

- (a) $a_{n+2}+a_n = \sin{(\pi n)}$.
- (b) $a_{n+2}+a_n = \sin{\left(\dfrac{\pi}{2}n\right)}$.

<!--more-->

***

El apartado (a) nos plantea la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}+a_n = \sin{(\pi n)}.
$$

Esta tiene como ecuación en diferencias lineal homogénea asociada 

$$
a_{n+2}+a_n = 0,
$$

cuya ecuación característica correspondiente es 

$$
\lambda^2+1=0.
$$ 

Como $\lambda^2+1 = (\lambda - i)(\lambda + i)$, estamos en el caso de raíces complejas conjugadas simples, para las que $\varrho = 1$ y $\theta = \pi/2$, de manera que la solución para la ecuación anterior queda

$$
\begin{aligned}
a_h(n) &= 1^n\left(A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}\right)\\
&= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B\in\mathbb{R}$. 

Ahora, para hallar una solución particular, $a_p(n)$, como $b(n) = \sin{(\pi n)}$ y $\lambda = \cos{(\pi)} + i\sin{(\pi)} = -1$ no es raíz de la ecuación característica, proponemos $a_p(n) = a\cos{(\pi n)} + b\sin{(\pi n)}$, de manera que, sustituyendo en la ecuación inicial

$$
\begin{aligned}
a\cos{(\pi(n+2))} + b\sin{(\pi(n+2))} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},\\
a\cos{(\pi n+2\pi)} + b\sin{(\pi n+2\pi)} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},
\end{aligned}
$$

y recordando que

$$
\begin{aligned}
\cos{(k_1+k_2)} &= \cos{(k_1)}\cos{(k_2)}-\sin{(k_1)}\sin{(k_2)},\\
\sin{(k_1+k_2)} &= \sin{(k_1)}\cos{(k_2)}+\cos{(k_1)}\sin{(k_2)},
\end{aligned}
$$

entonces $\cos{(\pi n+2\pi)} = \cos{(\pi n)}$ y $\sin{(\pi n+2\pi)} = \sin{(\pi n)}$, con lo que la ecuación anterior queda

$$
\begin{aligned}
a\cos{(\pi n)} + b\sin{(\pi n)} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},\\
2a\cos{(\pi n)} + 2b\sin{(\pi n)} &= \sin{(\pi n)},
\end{aligned}
$$

e, igualando coeficientes, llegamos a que $2a=0$, de donde $a=0$, y $2b=1$, con lo que $b=1 / 2$, de forma que 

$$
a_p(n) = \dfrac{1}{2}\sin{(\pi n)}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)} + \dfrac{1}{2}\sin{(\pi n)},
$$ 

con $A,B\in\mathbb{R}$.

En el apartado (b), tenemos la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}+a_n = \sin{\left(\dfrac{\pi}{2}n\right)},
$$

cuya correspondiente ecuación lineal homogénea es 

$$
a_{n+2}+a_n = 0,
$$

con ecuación característica asociada 

$$
\lambda^2 + 1=0.
$$ 

Como $\lambda^2+1 = (\lambda - i)(\lambda + i)$, estamos en el caso de raíces complejas conjugadas simples, para las que $\varrho = 1$ y $\theta = \pi/2$, de manera que la solución para la ecuación anterior queda 

$$
\begin{aligned}
a_h(n) &= 1^n\left(
A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}
\right)\\
&= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$ 

con $A,B\in\mathbb{R}$. 

Ahora, para hallar una solución particular, $a_p(n)$, como 

$$
b(n) = \sin{\left(\dfrac{\pi}{2}n\right)}
$$ 

y 

$$
\lambda = \cos{\left(\dfrac{\pi}{2}\right)} + i\sin{\left(\dfrac{\pi}{2}\right)} = i
$$

es raíz simple ($m=1$) de la ecuación característica, proponemos

$$
\begin{aligned}
a_p(n) &= n^1\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right)\\
&= n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right),
\end{aligned} 
$$

de manera que, sustituyendo en la ecuación inicial,

$$
(n+2)\left(a\cos{\left(\dfrac{\pi}{2}(n+2)\right)} + b\sin{\left(\dfrac{\pi}{2}(n+2)\right)}\right)+n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right) = \sin{\left(\dfrac{\pi}{2}n\right)}
$$

y recordando que

$$
\begin{aligned}
\cos{(k_1+k_2)} &= \cos{(k_1)}\cos{(k_2)}-\sin{(k_1)}\sin{(k_2)},\\
\sin{(k_1+k_2)} &= \sin{(k_1)}\cos{(k_2)}+\cos{(k_1)}\sin{(k_2)},
\end{aligned}
$$

entonces 

$$
\begin{aligned}
\cos{\left(\dfrac{\pi}{2}(n+2)\right)} &= \cos{\left(\dfrac{\pi}{2}n+\pi\right)} = -\cos{\left(\dfrac{\pi}{2}n\right)},\\
\sin{\left(\dfrac{\pi}{2}(n+2)\right)} &= \sin{\left(\dfrac{\pi}{2}n+\pi\right)} = -\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con lo que la ecuación anterior queda

$$
(n+2)\left(-a\cos{\left(\dfrac{\pi}{2}n\right)} - b\sin{\left(\dfrac{\pi}{2}n\right)}\right)+ n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right) = \sin{\left(\dfrac{\pi}{2}n\right)}
$$

e, igualando coeficientes, llegamos a que $-2a=0$, de donde $a=0$, y $-2b=1$, por lo que $b = -1 / 2$, de forma que 

$$
a_p(n) = -\dfrac{1}{2}\sin{\left(\dfrac{\pi}{2}n\right)}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
\begin{aligned}
a(n) = a_h(n) + a_p(n) &= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)} -\dfrac{1}{2}\sin{\left(\dfrac{\pi}{2}n\right)}\\
&=A\cos{\left(\dfrac{\pi}{2}n\right)} + \left(B-\dfrac{1}2{}\right)\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B\in\mathbb{R}$.
