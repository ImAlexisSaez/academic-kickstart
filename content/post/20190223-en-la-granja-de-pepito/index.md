---
title: "En la granja de Pepito"
slug: "en-la-granja-de-pepito"
subtitle: "Problema 54"
summary: "Problema 54: de vacas, cerdos y pollos."

date: 2019-02-23T05:59:39+02:00
lastmod: 2019-08-02T00:00:01+02:00

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
  caption: "Fotografía de [Maksym Ivashchenko](https://unsplash.com/@maksymiv), disponible en [Unsplash](https://unsplash.com/photos/q3-ugNWsBfg)."
---

**Problema 54:** Un granjero compró vacas, cerdos y pollos. En total $100$ animales por $100$ euros. Hay al menos uno de cada. Si una vaca cuesta $10$ euros, un cerdo $3$ euros y un pollo $0.50$ euros, ¿cuántos animales de cada clase compró?

***

Sea $x$ el número de vacas, $y$ el total de cerdos y $z$ la cantidad de pollos adquiridos. Como se compran $100$ animales, tenemos la ecuación lineal $x+y+z=100$, con la restricción de que $x\geq1$, $y\geq1$ y $z\geq1$ ya que nos indican que, al menos, se compra un animal de cada tipo. Finalmente, dados los precios suministrados y el desembolso llevado a cabo, encontramos la ecuación $10x+3y + 0.5z = 100$. Así pues, hemos de resolver el sistema de ecuaciones

$$
\begin{aligned}
10x+3y+0.5z &= 100,\\ 
x+y+z &= 100,
\end{aligned}
$$

con la restricción adicional indicada arriba. Despejando la variable $z$ de la segunda ecuación, $z = 100-x-y$, y sustituyéndola en la primera ecuación del sistema,

$$
10x + 3y + 50 - 0.5x - 0.5y = 100,
$$

esto es, $10x+3y-0.5x-0.5y=50$, o bien $19x+5y=100$, ecuación diofántica que sabemos admite solución entera, puesto que $mcd(5,19)=1$ y, obviamente, $1|100$. Así, despejando la variable $y$, por ser aquella cuyo coeficiente asociado es más reducido, 

$$
y = \dfrac{100 - 19x}{5},
$$

por lo que basta probar, para $x$, valores pertenecientes al *menor sistema completo de restos módulo* $5$. Para $x_0=0$, hallamos que $y_0 = 20$, siendo esta una solución particular de la ecuación diofántica propuesta. Su solución general, por tanto, queda

$$
\begin{aligned}
x &= 5t,\\
y &= 20-19t,
\end{aligned}
$$

con $t$ número entero. Como hemos de comprar, al menos, un animal de cada tipo, tanto $x$ como $y$ han de ser positivas. De $5t>0$ concluimos que $t>0$; mientras que de $20-19t>0$ deducimos que $t\leq 1$. Así, como $t$ es un número entero, únicamente puede tomar el valor $t=1$, dejando así $x=5$, $y=1$ y $z = 100-x-y = 100-5-1=94$. Es decir, el granjero compró $5$ vacas, un cerdo y $94$ pollos.
