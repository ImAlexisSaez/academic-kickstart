---
title: "Juegos de lógica e ingenio en LaTeX"
slug: "juegos-de-logica-e-ingenio-en-latex"
subtitle: "Generando material para los talleres de matemáticas..."
summary: "¿Buscas cómo desarrollar el pensamiento lógico-deductivo en tu alumnado? ¿Qué te parecería conseguirlo a través de clásicos pasatiempos? ¿Y si, además, puedes hacerlo fácilmente empleando LaTeX?"

date: 2021-09-18T00:00:01+02:00
lastmod: 2023-04-29T00:00:01+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["LaTeX"]
categories: ["Recursos"]
# projects: []

image:
   focal_point: "Smart"
   caption: "Fotografía de [Jakub Chlouba](https://unsplash.com/@jakub_chlouba), disponible en [Unsplash](https://unsplash.com/photos/8REfDmu_bFE)."
---

El curso académico pasado tuve, entre mis materias a impartir, un taller de profundización de matemáticas en 4º de ESO. Una vez finalizado, he estado pensando durante este verano qué actividades incluir de cara a futuras iteraciones de esta asignatura (sea o no yo el responsable de impartir dicho taller). Una de las primeras ideas que acudió a mi mente fue explorar la posibilidad del uso de juegos de lógica e ingenio para desarrollar el pensamiento lógico-deductivo.

Afortunadamente, en *Internet* existe una variedad impresionante de generadores de juegos de lógica e ingenio. Por ejemplo, destacaría la familia de juegos a los que podemos acceder desde [esta web](https://es.puzzle-bridges.com/). 

El siguiente paso por dar consistía en explorar las posibilidades que ofrece *LaTeX* de cara a generar, con el menor esfuerzo posible, fichas de este tipo de pasatiempos para ofrecérselas a los alumnos. A este respecto, existe un paquete de *LaTeX* que incorpora plantillas predeterminadas para una cantidad numerosa de juegos de lógica e ingenio y, además, permite la opción de extender, de manera relativamente sencilla, el paquete para que incluya otros juegos no contemplados. Se trata de [logicpuzzle](https://www.ctan.org/pkg/logicpuzzle), cuya [documentación](https://osl.ugr.es/CTAN/graphics/pgf/contrib/logicpuzzle/logicpuzzle.pdf) es simplemente maravillosa. Para cada juego de lógica e ingenio que incorpora, lista los comandos particulares que lo genera y ofrece un ejemplo completo de código, tanto para el enunciado, como para la solución de dicho juego.

Personalmente, me he aventurado con algunos, como *2D-Sudoku*, *Battleship*, *Bokkusu*, *Bridges*, *Hitori*, *Kendoku* o *Killer Sudoku*. He organizado los documentos a doble columna, dejando una de ellas de ancho reducido para incluir las instrucciones del juego y las de entrega de la ficha y otra columna más extensa que recoge los enunciados de los juegos en sí. El aspecto final de algunas de ellas se muestra a continuación:

{{< figure src="Screenshot_1.png" title="Ejemplo de ficha para el juego *Hashiwokakero*." numbered="true" >}}

{{< figure src="Screenshot_2.png" title="Ejemplo de ficha para el juego *Shikaku*." numbered="true" >}}

{{< figure src="Screenshot_3.png" title="Ejemplo de ficha para el juego *Kakurasu*." numbered="true" >}}

{{< figure src="Screenshot_4.png" title="Ejemplo de ficha para el juego *Hitori*." numbered="true" >}}

{{< figure src="Screenshot_5.png" title="Ejemplo de ficha para el juego *Killer Sudoku*." numbered="true" >}}

{{< figure src="Screenshot_6.png" title="Ejemplo de ficha para el juego *Kenken*." numbered="true" >}}

{{< figure src="Screenshot_7.png" title="Ejemplo de ficha para el juego *Sudoku*." numbered="true" >}}

{{< figure src="Screenshot_1.png" title="Ejemplo de ficha para el juego *Bimaru*." numbered="true" >}}

Si bien es cierto que unos juegos son algo más tediosos de escribir en *LaTeX* que otros, una vez te familiarizas con las instrucciones, las fichas se generan relativamente rápido. Así, nos queda un excelente recurso para materias de tipo taller o para esos días previos a cualquier periodo vacacional.

Finalmente, mi intención es compartir todas las fichas en formato *PDF* (hasta la fecha, tengo doce generadas) en un proyecto cuando la disponibilidad de tiempo me lo permita.
