---
title: "Una historia de cheques de viaje"
slug: "una-historia-de-cheques-de-viaje"
subtitle: "Problema 11"
summary: "Problema 11: el relato de un... ¿error?"

date: 2018-09-22T05:59:39+02:00
lastmod: 2018-09-22T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Aviv Ben Or](https://unsplash.com/@vivanebro), disponible en [Unsplash](https://unsplash.com/photos/g_Abgn1slAM)."
---

En el presente artículo abordaremos con sumo detalle un problema propuesto en la convocatoria de oposiciones de Extremadura, de este mismo año 2018, para la especialidad de matemáticas.

***

**Problema 11:** En su último viaje a Estados Unidos, el señor Martínez cambió un cheque de viaje. El cajero, al pagarle, confundió el número de dólares con los centavos y viceversa. El señor Martínez gastó 68 centavos en sellos y comprobó que el dinero que le quedaba era el doble del importe del cheque de viaje que había cambiado. ¿Qué valor mínimo tenía el cheque de viaje?

***

Al leer el enunciado, enseguida apreciamos dos partes que nos sirven de pista hacia el tipo de problema que tenemos entre manos. Para empezar, cuando aparece ''el dinero que le quedaba era el doble del importe del cheque de viaje que había cambiado'', debemos sospechar que, en algún momento de la resolución del ejercicio, plantearemos una ecuación algebraica, posiblemente lineal. Esta poseerá múltiples soluciones, quizá incluso infinitas, ya que en la cuestión se interesan por el ''valor mínimo''. Al estar trabajando con dólares y centavos, cantidades monetarias que usualmente se representan utilizando números enteros, todo ello nos va a hacer pensar rápidamente en ecuaciones diofánticas.

Así pues, una de las claves de este ejercicio reside en trabajar en centavos, para evitar así operar con decimales. De esta manera, si el señor Martínez viajó a Estados con un cheque de viaje cuyo valor ascendía a $a$ dólares y $b$ centavos, con $a$ y $b$ números enteros mayores o iguales de cero, en total el valor de dicho cheque era de $100a + b$ centavos.

Ahora, en el banco se equivocaron al cambiarle el cheque de viaje, intercambiando los papeles de dólares y centavos, de forma que, al final, el señor Martínez recibió $100b + a$ centavos. De estos, gastó 68 centavos en sellos, quedándole entonces disponible $100b + a - 68$ centavos.

La anterior cantidad nos dicen que equivalía al doble del importe del cheque de viaje que había cambiado ($2(100a + b)$), es decir, tenemos la ecuación diofántica 

$$
100b + a - 68 = 200a + 2b,
$$ 

que queda, operando, 

$$
199a-98b=-68.
$$

Obtengamos el $mcd(199,98)$ utilizando el *Algoritmo de Euclides*:

$$
\begin{aligned}
199 &= 98\cdot 2 + 3,\\\\ 98 &= 3\cdot 32 + 2,\\\\ 3 &= 2\cdot 1 + 1,\\\\ 2 &= 1\cdot 2,
\end{aligned}
$$

luego $mcd(199, 98) = 1$ y como $1|68$ sabemos que la ecuación diofántica admite solución entera. 

Despejamos entonces $b$, por ser la variable cuyo coeficiente asociado es más pequeño, quedando así 

$$
b = \dfrac{199a + 68}{98}.
$$

Ahora, como el valor que figura en el denominador de la igualdad anterior es $98$, a continuación, tendríamos que darle a $a$, de manera ordenada, valores del *menor sistema completo de restos módulo* $98$ hasta hallar una solución particular.

No obstante, en lugar de llevar a cabo tan titánica labor, aprovecharemos las operaciones realizadas durante el *Algoritmo de Euclides* para descomponer la anterior fracción como sigue: 

$$
b = 2a + \dfrac{3a+68}{98} = 2a + b^{\prime},
$$

con

$$
b^{\prime} = \dfrac{3a+68}{98},
$$

que equivale a $98b^{\prime} = 3a + 68$, ecuación en la que ahora despejaremos $a$, teniendo que 

$$
a = \dfrac{98b^{\prime} - 68}{3}.
$$ 

Podemos así dar valores a $b^{\prime}$, ya que únicamente tendríamos que probar $b^{\prime}=0$, $b^{\prime}=1$ y $b^{\prime}=2$ (que conforma el *menor sistema completo de restos módulo* $3$). Para $b^{\prime}=0$, $a\notin\mathbb{Z}$, pero si $b^{\prime}=1$, entonces $a=10$ y, por tanto, $b = 2a+b^{\prime} = 21$, quedando así la solución particular como sigue:

$$
\begin{aligned}
a_0 &= 10,\\\\ b_0 &= 21,
\end{aligned}
$$

mientras que la solución general es

$$
\begin{aligned}
a &= 10 - 98t,\\\\ b &= 21 - 199t,
\end{aligned}
$$

con $t\in\mathbb{Z}$. 

Una vez resuelta la ecuación diofántica, centrémonos de nuevo en aquello que nos pedían en el enunciado: ''¿Qué valor mínimo tenía el cheque de viaje?''. Como hablamos de cantidades monetarias, tanto $a$, como $b$, han de ser mayores o iguales que cero, es decir,

$$
\begin{aligned}
a &= 10 -98t \geq0 \Rightarrow t\leq\dfrac{10}{98},\\\\ b &= 21 - 199t \geq0 \Rightarrow t\leq\dfrac{21}{199},
\end{aligned}
$$

y $t\in\mathbb{Z}$. Por consiguiente, el valor mínimo se alcanza cuando $t=0$, donde $a=10$ y $b=21$. Así, el señor Martínez viajó a Estados Unidos con un cheque de viaje cuyo valor ascendía a 10 dólares y 21 centavos.
