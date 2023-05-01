---
title: "¿Cómo actualizar fácilmente R en Windows?"
slug: "como-actualizar-facilmente-r-en-windows"
subtitle: "Realizando el proceso en un suspiro"
summary: "El proceso de actualización de la versión del lenguaje de programación *R* puede resultar un tanto tedioso si lo llevamos a cabo de forma manual. Veamos cómo hacer más liviana esta pesada carga."

date: 2018-08-04T05:59:39+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["R", "Windows"]
categories: ["Tutoriales"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Artem Sapegin](https://unsplash.com/@sapegin), disponible en [Unsplash](https://unsplash.com/photos/DErxVSSQNdM)."
---

El proceso de actualización de la versión del lenguaje de programación *R* puede resultar un tanto tedioso si lo llevamos a cabo de forma manual. Veamos cómo hacer más liviana esta pesada carga.

Por fortuna, tenemos a nuestra disposición el paquete [installr](https://cran.r-project.org/web/packages/installr/index.html), que se encarga de todo el anterior procedimiento automáticamente, a través de la llamada a la función `updateR()`.

De esta forma, basta con que tengamos a mano un *script* similar al que se muestra a continuación, y procedamos a ejecutarlo cuando se anuncie una nueva versión de *R*:

```r
# Instala el paquete
install.packages("installr")
 
# Actualiza R
library(installr)
updateR()
```

Al utilizar la función `updateR()`:

- Se comprueba cuál es la última versión de *R*. Si estamos al día, nos mostrará una ventana de confirmación de tal hecho. En caso contrario, nos dará la posibilidad de consultar las novedades de dicha versión y nos permitirá proceder a su descarga e instalación.
- Una vez completado el proceso, nos preguntará si deseamos mover (y borrar) las librerías desde nuestra antigua versión a la nueva. Además, nos dará la opción de ponerlas al día. Dependiendo del número de librerías que tengamos instaladas, completar estas acciones puede llevarnos un buen rato.

Si usamos *RStudio*, al principio se nos mostrará un aviso sugiriéndonos que llevemos a cabo todo el proceso desde la propia interfaz de *R*, en lugar de a través de este *IDE*. No obstante, en mi experiencia, podemos tranquilamente ignorar la advertencia y realizar el procedimiento utilizando *RStudio*. Al terminar, bastará con que reiniciemos el programa para que todo funcione con normalidad.

Finalmente, podemos ahorrarnos la sucesión de ventanas emergentes si sabemos de antemano que queremos actualizar *R*, mover (no copiar) las librerías y actualizarlas. Para ello, reescribimos el anterior script como sigue:

```r
# Instala / carga el paquete
if(!require(installr)) {install.packages("installr"); require(installr)} 
 
# Instala R, mueve y actualiza paquetes
updateR(F, T, T, F, T, F, T)
```
