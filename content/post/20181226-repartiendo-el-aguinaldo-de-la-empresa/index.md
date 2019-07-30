---
title: "Repartiendo el aguinaldo de la empresa"
slug: "repartiendo-el-aguinaldo-de-la-empresa"
subtitle: "Problema 37"
summary: "Problema 37: un enunciado muy apropiado para estas fechas."

date: 2018-12-26T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Problemas", "Teorema chino del resto", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [v2osk](https://unsplash.com/@v2osk), disponible en [Unsplash](https://unsplash.com/photos/8YfAkqH3p_Y)."
---

**Problema 37:** Un cierto número de billetes se reparten entre siete subalternos y dos jefes, teniendo en cuenta que un jefe cobra el doble que un subalterno. Tras el reparto, sobran seis billetes; pero si hubiese faltado un jefe, el reparto habría salido exacto. Por otro lado, si hubiera faltado un subalterno, serían entonces ocho los billetes que habrían sobrado. Calcular el menor número positivo de billetes que cobraron cada uno.

***

La clave para resolver este ejercicio es plantearse la cuestión: ''¿entre cuántas partes hay que repartir el total de billetes?''. Como cada jefe cobra por dos subalternos, en verdad son once las partes entre las que repartir. 

Así, si denotamos por $x$ el número de billetes, la primera ecuación de congruencia lineal es $x\equiv 6\pmod{11}$, pues se reparte entre las once partes y sobran (es decir, el resto asciende a) seis. Cuando falta un jefe, son entonces nueve las partes entre las que repartir, y al ser exacto dicho reparto se traduce entonces en la ecuación de congruencia lineal $x\equiv 0\pmod{9}$. Finalmente, cuando falta un subalterno, son diez las partes entre las que repartir, y como sobran ocho billetes, la correspondiente ecuación de congruencia lineal es $x\equiv 8\pmod{10}$. 

En resumen, hemos de resolver el sistema de congruencias lineales,

$$
\begin{aligned}
x&\equiv 6\pmod{11},\\
x&\equiv 0\pmod{9},\\
x&\equiv 8\pmod{10}.
\end{aligned}
$$

Como $mcd(9,10,11)=1$, esto es, son primos entre sí los tres números, por el *Teorema chino del resto* estamos en condiciones de asegurar que existe solución módulo $9\cdot10\cdot11 = 990$. Ahora bien,

$$
M_1=90,\qquad M_2=110,\qquad M_3=99,
$$

por lo que el siguiente paso es resolver las ecuaciones de congruencias lineales,

$$
\begin{aligned}
90x&\equiv 1\pmod{11}\Leftrightarrow 2x\equiv 1\pmod{11}\Leftrightarrow x\equiv 1\pmod{11},\\
110x&\equiv 1\pmod{9}\Leftrightarrow 2x\equiv 1\pmod{9}\Leftrightarrow x\equiv 5\pmod{11},\\
99x&\equiv 1\pmod{10}\Leftrightarrow (-x)\equiv 1\pmod{10}\Leftrightarrow x\equiv (-1)\pmod{11}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 6\pmod{11},& 90x&\equiv 1\pmod{11},& x&\equiv 6\pmod{11},\\
x&\equiv 0\pmod{9},& 110x&\equiv 1\pmod{9},& x&\equiv 5 \pmod{9},\\
x&\equiv 8\pmod{10},& 99x&\equiv 1\pmod{10},& x&\equiv (-1)\pmod{10},
\end{aligned}
$$

la solución al sistema queda

$$
\begin{aligned}
x &\equiv (6\cdot90\cdot6 + 0\cdot110\cdot5 + 8\cdot99\cdot(-1))\pmod{990}\\ 
&\equiv 2448\pmod{990}\equiv 468\pmod{990}.
\end{aligned}
$$

Nótese que podíamos habernos ahorrado los cálculos asociados a la segunda ecuación del sistema, por aquel $0$ que figura en la misma. Por tanto, el menor número positivo de billetes a repartir es $468$, y como $468 = 11\cdot42 + 6$, concluimos que los subalternos cobran $42$ billetes, mientras que los jefes $84$ billetes.
