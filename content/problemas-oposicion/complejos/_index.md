---
# Book
title: Números complejos
linktitle: Números complejos
summary: Problemas matemáticos de números complejos para la preparación de oposiciones al cuerpo de profesores de Enseñanza Secundaria, en la especialidad de matemáticas.

date: "2021-06-20T00:00:01+01:00"
lastmod: "2021-06-20T00:00:01+01:00"
draft: false # Is this a draft? true/false
toc: true # Show table of contents? true/false
type: book # Do not modify.
math: true
weight: 90
---

## Problemas resueltos

### Problema 1

Dada una constante real positiva, $a$, y el conjunto 

$$
M\_a = \left\\{z\in\mathbb{C}^* : \left|z+\dfrac{1}{z}\right|=a \right\\},
$$ 

donde $\mathbb{C}^* = \mathbb{C}\backslash\{(0,0)\}$, encuentre los valores mínimo y máximo de $|z|$ cuando $z\in M_a$. 

{{< hl >}}Solución:{{< /hl >}} hemos de ser capaces de extraer información sobre el módulo de $z$, $|z|$, a partir de la expresión de la ecuación que define al conjunto $M_a$. Por las propiedades de la conjugación, sabemos que $z\overline{z} = |z|^2$, de manera que una posible estrategia a seguir sería elevar al cuadrado ambos miembros de la ecuación que define a $M_a$ y desarrollar la expresión resultante mediante las propiedades de la conjugación. Así,

$$
\begin{aligned}
a^2 &= \left|z+\dfrac{1}{z}\right|^2 = \left(z+\dfrac{1}{z}\right)\overline{\left(z+\dfrac{1}{z}\right)} = \left(z+\dfrac{1}{z}\right)\left(\overline{z}+\dfrac{1}{\overline{z}}\right)\\\\ &= z\overline{z} + \dfrac{z}{\overline{z}} + \dfrac{\overline{z}}{z} + \dfrac{1}{z\overline{z}} = z\overline{z} + \dfrac{z^2 + \overline{z}^2}{\overline{z}z} + \dfrac{1}{z\overline{z}},
\end{aligned}
$$

pero recordemos que $z\overline{z} = |z|^2$, por lo que la anterior ecuación quedaría

$$
a^2 = |z|^2 + \dfrac{z^2+\overline{z}^2}{|z|^2}+\dfrac{1}{|z|^2},
$$

y multiplicando ambos miembros por $|z|^2$, número que sabemos es distinto de cero porque $z\in\mathbb{C}^*$, tenemos

$$
a^2|z|^2 = |z|^4 + z^2 + \overline{z}^2 + 1.
$$

Ahora bien, a primera vista, la anterior expresión parece que quiere conducirnos hacia alguna especie de ecuación bicuadrada en $|z|$. Efectivamente, si reordenamos los términos de manera adecuada, llegamos a

$$
|z|^4 - a^2|z|^2 + 1 = - (z^2 + \overline{z}^2)
$$

y si completamos el cuadrado del miembro derecho,

$$
\begin{aligned}
|z|^4 - a^2|z|^2 + 1 &= - (z^2 + \overline{z}^2 + 2z\overline{z} - 2z\overline{z})\\\\ &= - (z + \overline{z})^2 + 2z\overline{z}\\\\ &= - (z + \overline{z})^2 + 2|z|^2, 
\end{aligned}
$$

es decir,

$$
|z|^4 - (a^2+2)|z|^2 + 1 = - (z+\overline{z})^2 \leq 0.
$$

Por lo tanto, tras realizar operaciones algebraicas sobre la ecuación que define al conjunto $M_a$, hemos llegado a que la expresión de cierta ecuación bicuadrada en $|z|$ debe ser menor o igual que cero. Investiguemos si de ella podemos extraer alguna condición sobre el módulo de $z$ que nos permita dar respuesta al problema planteado.

Resolviendo $|z|^4 - (a^2 + 2)|z|^2 + 1 = 0$ y teniendo en cuenta que es positivo el coeficiente asociado a $|z|^4$, tenemos que $|z|^4 - (a^2 + 2)|z|^2 + 1 \leq 0$  si, y solo si,

$$
|z|^2\in \left[
\dfrac{2+a^2 - \sqrt{a^4+4a^2}}{2}, \dfrac{2+a^2 + \sqrt{a^4+4a^2}}{2}
\right],
$$

que es equivalente a decir que

$$
|z|\in \left[
\dfrac{-a + \sqrt{a^2+4}}{2}, \dfrac{a + \sqrt{a^2+4}}{2}
\right].
$$

Veamos esta última equivalencia en detalle, pues puede no resultarnos trivial a primera vista. La idea aquí es representar ambos extremos del intervalo que hemos obtenido para $|z|^2$ como cuadrados de ciertas expresiones. Si somos capaces de llevar a cabo tal tarea, únicamente bastará aplicar la raíz cuadrada (que, recordemos, es una transformación monótona creciente) para, de esta manera, llegar a la conclusión obtenida para $|z|$.

Centrémonos en la expresión del extremo inferior del intervalo definido para $|z|^2$ (el razonamiento a seguir sería análogo para el superior). Por un lado,

$$
2+a^2 - \sqrt{a^4 + 4a^2} = 2+a^2 - a\sqrt{a^2 + 4},
$$ 

expresión que nos invita a experimentar con el desarrollo de $(-a + \sqrt{a^2 + 4})^2$. Así,

$$
\begin{aligned}
(-a + \sqrt{a^2+4})^2 &= a^2 + a^2 + 4 - 2a\sqrt{a^2+4}\\\\ &= 2a^2+4 - 2a\sqrt{a^2+4}\\\\ &= 2(a^2+2-a\sqrt{a^2+4})\\\\ &= 2(a^2+2-\sqrt{a^4+4a^2}),
\end{aligned}
$$

de forma que

$$
\dfrac{2+a^2 - \sqrt{a^4+4a^2}}{2} = \dfrac{(-a + \sqrt{a^2+4})^2}{2\cdot 2} = \left(\dfrac{-a + \sqrt{a^2+4}}{2}\right)^2.
$$

Por tanto, hemos llegado a que

$$
\begin{aligned}
\min{|z|} &= \dfrac{-a+\sqrt{a^2+4}}{2},\\\\ \max{|z|} &= \dfrac{a+\sqrt{a^2+4}}{2},
\end{aligned}
$$

y los valores extremos se alcanzarán cuando se dé la igualdad en la inecuación considerada, es decir, cuando $-(z+\overline{z})^2 = 0$, que equivale a la condición $z=-\overline{z}$. Así pues, los valores extremos se alcanzarán para los números complejos $z\in M_a$ tales que $z=-\overline{z}$.

## Problemas propuestos

{{% callout note %}}
Pendiente de recopilación.
{{% /callout %}}