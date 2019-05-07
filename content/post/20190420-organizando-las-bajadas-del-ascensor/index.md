+++
title = "Organizando las bajadas del ascensor"
slug  = "organizando-las-bajadas-del-ascensor"
subtitle = "Problema 70"
summary  = "Problema 70: de barras, estrellas y... ¿ascensores?"

date     = 2019-04-20T05:59:39+02:00
#lastmod = 2019-04-20T10:58:50+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Elina Bernpaintner](https://unsplash.com/@elinajosefin), disponible en [Unsplash](https://unsplash.com/photos/LWio98k7C4s)."
+++

**Problema 70:** Suben dos mujeres y tres hombres a un ascensor en la planta baja de un edificio de seis pisos. Averigua de cuántas maneras se pueden bajar del ascensor, sabiendo que en un mismo piso no pueden bajar personas de distinto sexo.

***

En adelante, vamos a considerar que un edificio de seis pisos posee cinco plantas a las que subir en ascensor, esto es, contaremos la planta baja como un piso más y, obviamente, para acceder a ella no necesitamos utilizar el ascensor.

En primer lugar, asumamos que las mujeres son indistinguibles, así como los hombres, pues parece la interpretación más natural tras una primera lectura del enunciado. Empezaremos organizando la bajada de ellas, pues son menos personas a considerar y únicamente encontramos dos opciones posibles: que bajen juntas o por separado.

Si ambas bajan juntas en un mismo piso, son cinco las opciones que se les presentan disponibles, desde la planta primera hasta la quinta. A continuación, por lo que respecta a los hombres, cuatro son las plantas que les quedan para bajar los tres. Pueden hacerlo los tres juntos en una misma planta, cada uno por separado en plantas distintas, dos en una misma planta y el tercero en otra diferente, y así sucesivamente. Enseguida apreciamos que el problema es equivalente a uno de los tratados anteriormente: disponer sobre urnas indistinguibles cierto número de bolas idénticas. 

En esta ocasión, las cuatro plantas restantes harían el papel de urnas, mientras que los tres hombres adoptarían el rol de bolas. Utilizando la estrategia de *barras y estrellas*, necesitamos tres *barras* para representar sobre la recta real las cuatro urnas y buscamos ubicar luego tres *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de formas en que pueden bajar los tres hombres del ascensor, en las cuatro plantas restantes, equivale a la cantidad de permutaciones con repetición de seis elementos, donde cada uno de ellos se repite en tres ocasiones, esto es,

$$
PR\_{6}^{3,3} = CR\_{4,3} = \dbinom{4+3-1}{3} = \dbinom{6}{3} = 20.
$$

Así, aplicando la *regla del producto*, cuando las dos mujeres bajan juntas, las cinco personas pueden bajar del ascensor de $5\cdot20=100$ maneras posibles.

A continuación, asumamos que las mujeres bajan cada una en una planta diferente. Como hemos supuesto que ambas son indistinguibles, esta acción la pueden realizar de tantas formas como número de combinaciones de cinco elementos tomados de dos en dos hay (puesto que el orden no importa, es indiferente que una baje en el primero y otra en el tercero o en el orden contrario), es decir,

$$
C\_{5,2} = \dbinom{5}{2} = 10.
$$

Así, ahora quedan tres pisos disponibles para que bajen los tres hombres. Por un razonamiento similar al llevado a cabo arriba, el problema sería equivalente al de almacenar tres bolas idénticas en tres urnas indistinguibles. Utilizando la estrategia de *barras y estrellas*, necesitamos dos *barras* para representar sobre la recta real las tres urnas y buscamos ubicar luego tres *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de formas en que pueden bajar del ascensor los tres hombres, en las tres plantas restantes, equivale a la cantidad de permutaciones con repetición de cinco elementos, donde uno de ellos se repite en tres ocasiones, mientras que el otro lo hace dos veces, esto es,

$$
PR\_{5}^{3,2} = CR\_{3,3} = \dbinom{3+3-1}{3} = \dbinom{5}{3} = 10.
$$

Así, aplicando la *regla del producto*, cuando las dos mujeres bajan por separado, las cinco personas pueden bajar del ascensor de $10\cdot10=100$ maneras posibles.

Finalmente, por el *principio de adición*, son $100+100=200$ las maneras en que dos mujeres y tres hombres pueden bajar del ascensor, en un edificio de seis pisos, sabiendo que en un mismo piso no pueden bajar personas de distinto sexo.

En segundo lugar, consideremos que las cinco personas son distinguibles (que sería el caso, por ejemplo, de que nos las hubiesen presentado cada una por su nombre). Actuaremos de forma similar a como hicimos en los párrafos anteriores, empezando por estudiar las formas en las que pueden bajar las mujeres: juntas o separadas.

Si bajan juntas, como antes, son cinco las opciones que se les presentan disponibles, una por cada una de las cinco plantas. Ahora, por lo que respecta a los hombres, les quedan cuatro plantas donde poder bajar del ascensor. Como el orden en esta ocasión sí es importante y en una misma planta pueden bajar varios de ellos, el número de maneras en que pueden bajar equivale a la cantidad de variaciones con repetición de cuatro elementos tomados de tres en tres, esto es, $VR\_{4,3} = 4^3 = 256$. Aplicando la *regla del producto*, cuando las dos mujeres bajan juntas, las cinco personas pueden bajar del ascensor de $5\cdot256 = 1280$ maneras posibles.

Si las mujeres bajan por separado, dado que importa el orden en el que lo hagan, la cantidad de formas en que pueden hacerlo asciende al total de variaciones de cinco elementos tomadas de dos en dos, es decir, $V\_{5,2} = 5\cdot4 = 20$. Ahora, por lo que respecta a los hombres, les quedan tres plantas donde poder bajar del ascensor. Como el orden en esta ocasión sí es importante y en una misma planta pueden bajar varios de ellos, el número de maneras en que pueden bajar equivale a la cantidad de variaciones con repetición de tres elementos tomados de tres en tres, esto es, $VR\_{3,3} = 3^3 = 27$. Aplicando la *regla del producto*, cuando las dos mujeres bajan juntas, las cinco personas pueden bajar del ascensor de $20\cdot27 = 540$ maneras posibles.

Finalmente, por el *principio de adición*, son $1280+540=1820$ las maneras en que dos mujeres y tres hombres (todos ellos distinguibles) pueden bajar del ascensor, en un edificio de seis pisos, sabiendo que en un mismo piso no pueden bajar personas de distinto sexo.

*Nota*: si interpretamos el enunciado asignando seis plantas al edificio, habremos de llevar a cabo las oportunas correcciones en el argumento expuesto.
