+++
title = "Refinando el ejercicio del último día"
slug  = "refinando-el-ejercicio-del-ultimo-dia"
subtitle = "Problema 77"
summary  = "Problema 77: una vuelta de tuerca adicional."

date     = 2019-05-15T05:59:39+02:00
#lastmod = 2019-05-15T07:02:09+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Maksym Ivashchenko](https://unsplash.com/@maksymiv), disponible en [Unsplash](https://unsplash.com/photos/rcXHH30zEKg)."
+++

**Problema 77:** 

- (a) Calcula el número de soluciones enteras no negativas de $$x\_1+x\_2+x\_3+x\_4+x\_5+x\_6=10.$$
- (b) ¿Cuántas soluciones enteras no negativas posee la inecuación $$x\_1+x\_2+x\_3+x\_4+x\_5+x\_6 < 10 ?$$

***

Para el apartado (a), razonaremos, como viene siendo ya habitual, en términos de urnas indistinguibles y bolas idénticas. Consideraremos que tenemos en nuestro haber seis de dichas urnas, en las que deseamos colocar diez de las mencionadas bolas. Aplicando la técnica de *barras y estrellas* necesitamos cinco *barras* para representar sobre la recta real las seis urnas y buscamos ubicar luego diez *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de formas en que el valor de la suma de seis variables puede ascender a diez, equivale a la cantidad de permutaciones con repetición de $15$ elementos, donde uno de ellos se repite cinco veces, mientras que el otro lo hace en diez ocasiones. Así, hay

$$
PR\_{15}^{5,10} = CR\_{6,10} = \dbinom{15}{10} = \dfrac{15\cdot14\cdot13\cdot12\cdot11}{5!} = 3003
$$

soluciones enteras no negativas para la ecuación propuesta.

En cuanto al apartado (b), nos encontramos en una situación parecida a la del [ejercicio anterior](/2019/05/11/buscando-el-total-de-soluciones-de-una-inecuacion/) aunque observamos una desigualdad estricta. En primer lugar, cambiaremos adecuadamente el signo $<$ por $\leq$ y luego procederemos como en aquel problema. Así, como estamos interesados en soluciones enteras no negativas, es cierto que

$$
x\_1+x\_2+x\_3+x\_4+x\_5+x\_6 < 10 \Leftrightarrow x\_1+x\_2+x\_3+x\_4+x\_5+x\_6\leq 9.
$$

A continuación, introducimos una urna adicional, en la forma de una nueva variable, $x\_7$, para así transformar la inecuación en una ecuación. Por tanto, el problema se reduce a averiguar el número de soluciones enteras no negativas de la ecuación 

$$
x\_1+x\_2+x\_3+x\_4+x\_5+x\_6+x\_7=9.
$$

Aplicando la técnica de *barras y estrellas* necesitamos seis *barras* para representar sobre la recta real las siete urnas y buscamos ubicar luego nueve *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de formas en que el valor de la suma de siete variables puede ascender a nueve, equivale a la cantidad de permutaciones con repetición de $15$ elementos, donde uno de ellos se repite seis veces, mientras que el otro lo hace en nueve ocasiones. Así, hay

$$
PR\_{15}^{6,9} = CR\_{7,9} = \dbinom{15}{9} = \dfrac{15\cdot14\cdot13\cdot12\cdot11\cdot10}{6!} = 5005
$$

soluciones enteras no negativas para la ecuación propuesta y, por tanto, asimismo para la inecuación planteada en el segundo apartado del ejercicio.
