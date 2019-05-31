+++
title = "Política, votos y un poco de combinatoria"
slug  = "politica-votos-y-un-poco-de-combinatoria"
subtitle = "Problema 81"
summary  = "Problema 81: mezclando política y matemáticas, ¿qué podría salir mal?."

date     = 2019-05-29T05:59:39+02:00
#lastmod = 2019-05-31T10:04:40+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Principio de reflexión de André", "Problemas", "Rutas equiprobables"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
   focal_point = "Smart"
   caption     = "Fotografía de [Jonathan Bean](https://unsplash.com/@jonathanbean), disponible en [Unsplash](https://unsplash.com/photos/sbZU1j31ggE)."
+++

**Problema 81:** Dos candidatos $A$ y $B$ se presentan a una elección. Si $A$ recibe $a$ votos y $B$ recibe $b$ votos, con $a>b$, ¿cuál es la probabilidad de que, en todo momento del escrutinio, $A$ vaya por delante de $B$?

***

El presente ejercicio es ciertamente similar a uno de los apartados del [anterior problema](/2019/05/25/seguimos_de_rutas/), por lo que seguiremos el procedimiento allí esbozado. Para empezar, como no tenemos mayores indicaciones sobre cómo transcurre el escrutinio, asumiremos que todos los sucesos posibles de este experimento aleatorio son equiprobables, hecho que nos permitirá calcular probabilidades haciendo uso de la *Regla de Laplace*.

Por lo que respecta al total de casos posibles, este asciende al número de trayectorias que parten desde el origen de coordenadas y arriban hasta el punto $(a,b)$, que sabemos es

$$
C\_{a+b,a} = \dbinom{a+b}{a}.
$$

A continuación, de cara a obtener el cardinal del conjunto de casos favorables, sabemos que, a la postre, $a>b$. Por otro lado, la condición de que, durante el escrutinio, el candidato $A$ se mantenga siempre por delante del $B$, se traduce en que las trayectorias que partan del origen de coordenadas y lleguen hasta el punto $(a,b)$, se mantengan siempre por debajo de la diagonal $y=x$, sin intersecarla en momento alguno. 

Para ello, las rutas favorables a la situación comentada han de comenzar, necesariamente, desde el punto $(1,0)$. Así pues, hallemos el total de trayectorias existentes entre el punto $(1,0)$ y el punto $(a,b)$ que, por traslación, sabemos es equivalente a la cantidad de rutas entre el origen de coordenadas y el punto $(a,b) - (1,0) = (a-1,b)$ y esta última cifra asciende a

$$
C\_{a+b-1,b} = \dbinom{a+b-1}{b}.
$$

No obstante, entre ellas habrá algunas que se caractericen por intersecar la recta diagonal $y=x$, que procederemos a sustraer utilizando el *Principio de reflexión de André*. Aplicado a este caso particular, dicho principio afirma que el número de trayectorias que van desde el punto $(1,0)$ hasta el punto $(a,b)$ e intersecan la recta diagonal $y=x$, equivale a la cantidad de trayectorias que van desde el punto $(0,1)$ (simétrico de $(1,0)$ respecto de la recta $y=x$) hasta el punto $(a,b)$. Por traslación, estas equivalen al total de trayectorias desde el origen de coordenadas hasta el punto $(a,b) - (0,1) = (a,b-1)$, esto es,

$$
C\_{a+b-1,a} = \dbinom{a+b-1}{a}.
$$

Por consiguiente, el número de trayectorias desde el origen de coordenadas hasta el punto $(a,b)$, que se sitúan por debajo de la recta diagonal $y=x$, son

$$
\dbinom{a+b-1}{b} - \dbinom{a+b-1}{a}.
$$

Finalmente, 

$$
P = \dfrac{C\_{a+b-1,b} - C\_{a+b-1,a}}{C\_{a+b,a}} = \dfrac{\dbinom{a+b-1}{b} - \dbinom{a+b-1}{a}}{\dbinom{a+b}{a}}
$$

es la probabilidad de que, en todo momento del escrutinio, $A$ vaya por delante de $B$. A modo anecdótico, podemos facilitar una expresión más compacta para $P$. Desarrollando,

$$
\begin{aligned}
P &= \dfrac{\dfrac{(a+b-1)!}{b!(a-1)!} - \dfrac{(a+b-1)!}{a!(b-1)!}}{\dfrac{(a+b)!}{a!b!}} = \dfrac{\dfrac{a(a+b-1)!}{a!b!} - \dfrac{b(a+b-1)!}{a!b!}}{\dfrac{(a+b)!}{a!b!}}\\\\ &= \dfrac{(a-b)(a+b-1)!}{(a+b)(a+b-1)!} = \dfrac{a-b}{a+b},
\end{aligned}
$$

llegamos a una sencilla expresión para rápidamente calcular la probabilidad de interés.
