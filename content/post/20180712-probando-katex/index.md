---
title: "Probando KaTeX con un problema de inducción clásico"
slug: "probando-katex-con-un-problema-de-induccion-clasico"
subtitle: "Problema 1"
summary: "Problema 1: sumando números naturales."

date: 2018-07-12T05:59:39+02:00
lastmod: 2019-07-22T00:00:01+01:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Inducción", "KaTeX", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Antoine Dautry](https://unsplash.com/@antoine1003), disponible en [Unsplash](https://unsplash.com/photos/05A-kdOH6Hw)."
---

**Problema 1:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,  

$$
1 + 2 + \cdots + n = \dfrac{n(n+1)}{2}.
$$ 

***

Generalmente, cuando abordamos problemas en los que tenemos que demostrar que cierta fórmula o afirmación se satisface, para un conjunto de índices de cardinal infinito (en esta ocasión hablaríamos del conjunto $n\geq1$, con $n\in\mathbb{N}$), es recomendable que llevemos a cabo una primera aproximación a su resolución empleando el *principio de inducción matemática*.

Así pues, vamos a considerar la propiedad, que denotaremos por $P(n)$, dada en el enunciado del problema, 

$$
1+2+\cdots+n = \dfrac{n(n+1)}{2}.
$$ 

Por lo que respecta al *caso base*, $P(1)$, rápidamente comprobamos que se verifica de manera trivial, ya que 

$$
1 = \dfrac{1\cdot2}{2} = 1.
$$

Abordemos ahora el *paso inductivo*, para lo cual hemos de mostrar que si $P(n)$ se cumple, para un $n\geq1$, entonces asimismo se satisface $P(n+1)$, cuya expresión es 

$$
1+2+\cdots+n+(n+1)=\dfrac{(n+1)(n+2)}{2}.
$$ 

La clave en este tipo de situaciones consiste en encontrar una manera acertada de manipular la conocida como *hipótesis de inducción*, $P(n)$, que nos ayude a verificar el resultado que estamos buscando comprobar.

Por fortuna para nosotros, si nos fijamos en el miembro izquierdo de la ecuación de $P(n+1)$, apreciamos que directamente aparece la suma de los $n$ primeros números naturales, cuyo valor, por la *hipótesis de inducción*, es 

$$
\dfrac{n(n+1)}{2}.
$$ 

Este hecho nos permite afirmar que 

$$
1+2+\cdots+n+(n+1) = \dfrac{n(n+1)}{2} + (n+1).
$$ 

Ahora, sumando algebraicamente ambos términos, 

$$
\dfrac{n(n+1)}{2} + (n+1)= \dfrac{n(n+1) + 2(n+1)}{2}= \dfrac{(n+1)(n+2)}{2},
$$ 

es decir, hemos llegado a mostrar que 

$$
1+2+\cdots+n+(n+1)=\dfrac{(n+1)(n+2)}{2},
$$ 

completando así el *paso inductivo*.

Así pues, por el *principio de inducción matemática*, podemos concluir que $P(n)$ se verifica para cada $n\in\mathbb{N}$, con $n\geq 1$.

***

Podría decir que la experiencia de usar *KaTeX* ha sido un tanto agridulce. La mayor parte del artículo procede de código fuente escrito en *TeX* y apenas he tenido que llevar cambio alguno en el código para que fuera interpretado correctamente por *KaTeX*, hecho ciertamente positivo. No obstante, no he sido capaz de trabajar con los entornos que, según la [web oficial](https://khan.github.io/KaTeX/function-support.html), están disponibles, como por ejemplo `aligned` o `pmatrix`. Esto, en ocasiones, temo que vaya a dificultar la narrativa o incluso a impedir la publicación de ejemplos que requieran estructuras matriciales.

Seguiré investigando, ya que me gustaría ir publicando habitualmente problemas matemáticos sin tener que recurrir a la clásica solución de compartirlos en formato `PDF` vía algún servicio de alojamiento de ficheros.

*Actualización:* tras un descanso para aclarar ideas, ¡por fin he dado con la solución al problema de los entornos! Si escribimos

```tex
$$
x = 
\begin{cases}
  a &\text{if } b\\
  c &\text{if } d
\end{cases}
$$
```

el resultado no se visualiza correctamente, y así sucede para cualquier entorno que requiera cambios de línea, como `aligned`, `pmatrix`, etc. La clave reside en el tratamiento que recibe en *Markdown* el carácter `\`, que interfiere con el funcionamiento adecuado de *KaTeX*.

La solución pasa por "escapar" el mencionado carácter, de manera que, si habitualmente necesitamos dos para comenzar una nueva línea, ahora tendríamos que teclear cuatro. Además, en ocasiones, según el entorno que vayamos a emplear, es posible que debamos sacrificar las sangrías y escribir todo medianamente seguido.

Es decir, el siguiente bloque de código

```tex
$$
x = 
\begin{cases}
  a &\text{if } b\\\\ c &\text{if } d
\end{cases}
$$
```

funciona a la perfección, como podemos comprobar a continuación

$$
x = 
\begin{cases}
  a &\text{if } b\\
  c &\text{if } d
\end{cases}
$$

Esto va a requerir cierto tiempo adicional para que edite algunas de las expresiones escritas con *TeX*, pero me alegro de poder tener a mi disposición la posibilidad de utilizar algunos entornos matemáticos básicos.
