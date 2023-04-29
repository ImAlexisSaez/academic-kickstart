---
title: "Los 34 grados de libertad de un estudio"
slug: "los-34-grados-de-libertad-de-un-estudio"
subtitle: "Tentaciones a evitar"
summary: "Breve análisis del artículo 'Degrees of freedom in planning, running, analyzing, and reporting psychological studies. A checklist to avoid p-hacking'."

date: 2018-08-02T05:59:39+02:00
lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Grados de libertad", "Papers"]
categories: ["Estadística"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [João Silas](https://unsplash.com/@joaosilas), disponible en [Unsplash](https://unsplash.com/photos/I_LgQ8JZFGE)."
---

Hace unos días, completé la lectura del estupendo artículo *"Degrees of freedom in planning, running, analyzing, and reporting psychological studies. A checklist to avoid p-hacking"*, cuya lista de autores es casi tan extensa como el propio título, y de acceso abierto a través de [este enlace](http://journal.frontiersin.org/article/10.3389/fpsyg.2016.01832/abstract). 

En la línea de la famosa idea conocida como *"The Garden of Forking Paths"*, acuñada por *Andrew Gelman*, el mencionado documento lista los múltiples grados de libertad existentes en todas y cada una de las fases de un estudio. Ahora bien, ¿a qué nos referimos cuando hablamos de los grados de libertad de un estudio? 

Sin entrar aquí en demasiado detalle, se trata de ciertas decisiones arbitrarias (intencionadas o no) que los investigadores toman en sus investigaciones a la hora de diseñarlas, recoger los datos de interés, analizar éstos y posteriormente reportarlos en publicaciones científicas. Es lógico entonces que nos planteemos la siguiente cuestión: ¿qué efecto poseen los grados de libertad de un estudio sobre las conclusiones alcanzadas? 

Entre otras, las dos principales consecuencias son, por un lado, el incremento de la probabilidad de hallar resultados que no son más que falsos positivos, y, por otra parte, la posibilidad de inflar las estimaciones para los tamaños de los efectos observados. Así pues, ¿es posible evitar su aparición en un estudio? 

A día de hoy, el mejor método (aunque dista de ser perfecto) para que un estudio esté libre de grados de libertad es utilizar, de manera precisa y muy detallada, un recurso conocido como *pre-registro* (*preregistration* en inglés). La idea es presentar, e incluso someter a revisión de pares, el plan que seguirá cierta investigación antes de realizar la propia recolección de los datos de interés.

En el citado artículo se ofrece un listado (no totalmente exhaustivo) de los grados de libertad que puede presentar un estudio, restringiendo este al marco de referencia habitual utilizado para el contraste de hipótesis. De esta forma, los autores advierten que habría que eliminar o añadir ciertos grados de libertad si es otra la metodología empleada.

Algunos de los mencionados grados de libertad están relacionados entre sí (recomiendo consultar la tabla que figura en la última página del artículo) o incluso pueden llegar a dar la impresión de aparecer por duplicado. No obstante, se justifica este hecho por la importancia de adoptar cierta decisión en una fase del estudio u otra.

A modo de resumen, estos son los 34 grados de libertad de un estudio, desglosados en función de las distintas etapas de una investigación:

- *Fase de generación de hipótesis*:
    - *[T1]* Llevar a cabo investigaciones exploratorias. Esto conduce a una práctica conocida como *"HARKing"* (*"Hypothesizing After Results are Known"*, que vendría a ser generar hipótesis una vez se conocen los resultados).
    - *[T2]* Declarar hipótesis imprecisas que no indiquen la dirección del posible efecto. Es un tipo especial de *"HARKing"*, ya que el investigador puede luego analizar los datos de dos maneras alternativas.
- *Fase de diseño*:
    - *[D1]* Crear múltiples condiciones y variables independientes manipuladas. A medida que el diseño de un estudio adquiere complejidad, esta práctica puede conducir a posibles futuras decisiones con respecto a los niveles de las variables que se están considerando o sobre las condiciones en la que centra el foco de atención.
    - *[D2]* Medir variables adicionales sin decidir de antemano si éstas serán bien covariables, bien variables independientes, bien variables mediadoras, o bien variables moderadoras.
    - *[D3]* Registrar la misma variable dependiente de diferentes formas alternativas. Esta práctica puede tentar al investigador a adoptar al final la escala que favorezca la aparición de resultados significativos.
    - *[D4]* Medir variables dependientes (o incluso probar teorías) adicionales, diseñadas en principio como secundarias en el estudio, que luego adopten un rol primario en los resultados del estudio si las variables principales fallan a la hora de mostrar efecto alguno (esto podría considerarse también como una especie de *"HARKing"*).
    - *[D5]* Incorporar variables adicionales que permitan, *a posteriori*, al investigador, la exclusión del análisis de ciertos (o incluso grupos de) participantes, con el propósito de encontrar así resultados significativos.
    - *[D6]* No realizar un análisis del poder estadístico del estudio. Es más, el investigador suele adoptar una posición extremadamente optimista al respecto de este asunto cuando trabaja con muestras pequeñas, lo cual se traduce en estudios de bajo poder estadístico.
    - *[D7]* No informar acerca del plan de muestreo, permitiendo así la posibilidad de realizar, de manera consecutiva, múltiples pequeños estudios hasta dar con el resultado significativo deseado (y sin haber controlado el efecto que esta práctica posee sobre el *error de tipo I*).
- *Fase de recolección de datos*:
    - *[C1]* No asignar los participantes de un estudio a las condiciones de forma aleatoria, lo cual da lugar a la posible aparición de variables de confusión.
    - *[C2]* No escoger de manera acertada la técnica de enmascaramiento (simple, doble o triple ciego), bien para los participantes, bien para los investigadores, pudiendo sesgar así los resultados del estudio.
    - *[C3]* Corregir, codificar o descartar datos durante la fase de recolección, de una forma no coherente con la técnica de enmascaramiento asociada al estudio.
    - *[C4]* Determinar la regla de parada de recolección de datos en función de si se ha obtenido, o no, el resultado deseado.
- *Fase de análisis*: los puntos que se listan a continuación en este apartado son una serie de decisiones con marcado carácter [*ad hoc*](https://es.wikipedia.org/wiki/Ad_hoc) por parte del investigador.
    - *[A1]* Seleccionar entre diferentes opciones de tratamiento para los datos incompletos o perdidos.
    - *[A2]* Especificar el pre-procesamiento de los datos (limpieza, normalización, suavizado o correcciones).
    - *[A3]* Dictaminar cómo lidiar con las violaciones de los supuestos estadísticos.
    - *[A4]* Decidir cómo tratar con los valores atípicos.
    - *[A5]* Determinar la variable dependiente de entre las múltiples alternativas existentes asociadas a una misma teoría.
    - *[A6]* Probar diferentes maneras de anotar o registrar (o emplear distintas escalas para) una variable dependiente.
    - *[A7]* Optar por una teoría alternativa como principal resultado.
    - *[A8]* Escoger las variables independientes de entre un conjunto de variables independientes manipuladas.
    - *[A9]* Usar las variables independientes manipuladas de diversas formas.
    - *[A10]* Incluir diferentes variables probándolas bien como covariables, bien como variables independientes, bien como variables mediadoras, bien como variables moderadoras.
    - *[A11]* Utilizar las variables independientes no manipuladas de distintas maneras.
    - *[A12]* Usar un criterio alternativo de inclusión y exclusión de participantes.
    - *[A13]* La propia determinación del modelo estadístico.
    - *[A14]* La elección del método de estimación, el programa informático donde se va a llevar a cabo el análisis de datos, y la forma en la que se calculan los errores estándar.
    - *[A15]* La elección del criterio de inferencia.
- *Fase de informe*:
    - *[R1]* No asegurar la reproducibilidad del estudio.
    - *[R2]* No habilitar (o facilitar la posibilidad de) la replicación del estudio.
    - *[R3]* Para los estudios que han sido pre-registrados, no mencionar, falsificar o identificar erróneamente su pre-registro.
    - *[R4]* No informar de los denominados "estudios fallidos" que fueron originalmente considerados relevantes para la investigación propuesta.
    - *[R5]* No informar adecuadamente de los resultados y los *p*-valores.
    - *[R6]* Formular hipótesis después de observar los resultados (el ya nombrado *"HARKing"*).

Los autores dedican en el artículo, a cada uno de los anteriores 34 puntos, algunos párrafos para contextualizarlos, explicar su influencia sobre los resultados y ofrecer buenas prácticas para evitar que hagan acto de presencia en el estudio.

En resumen, una lectura que merece la pena y que recomiendo encarecidamente.
