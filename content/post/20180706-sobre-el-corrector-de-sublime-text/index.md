---
title: "Sobre el corrector de Sublime Text"
slug: "sobre-el-corrector-de-sublime-text"
subtitle: "Añadiendo un diccionario en español a este editor de texto"
summary: "Trabajar con Sublime Text 3 no implica renunciar al uso de un buen corrector ortográfico."

date: 2018-07-06T07:59:39+02:00
lastmod: 2018-07-06T07:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Sublime Text 3"]
categories: ["Tutoriales"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Romain Vignes](https://unsplash.com/@rvignes), disponible en [Unsplash](https://unsplash.com/photos/ywqa9IZB-dU)."
---

Si nos decidimos a utilizar este editor de texto plano para escribir en español, ¿tenemos entonces que prescindir sin remedio del uso del corrector ortográfico? ¡En absoluto! Veamos cómo configurar esta característica fácilmente.

En la instalación por defecto de *Sublime Text 3*, el mencionado corrector ortográfico únicamente tiene a su disposición dos listados de palabras, asociados estos a los idiomas:

- inglés británico, e
- inglés estadounidense (o ''americano'').

Comúnmente conocidos también como *diccionarios* (aunque no se incluyan los significados para las palabras contenidas en este tipo de listados nombrado), podemos seleccionar cualquiera de ellos a través del menú `View`, dentro del apartado `Dictionary`, y luego activar el modo de corrección ortográfica sin más que pulsar la tecla `F6`.

En apenas unos minutos podemos ampliar el número de listado de palabras siguiendo esta serie de pasos:

1. Desde nuestro navegador habitual, acudimos a [este repositorio](https://github.com/titoBouzout/Dictionaries) de *GitHub*, donde encontraremos un extenso listado de diccionarios disponibles.
2. Cada idioma tiene tres archivos asociados, con las extensiones `.aff`, `.dic` y `.txt`. Por ejemplo, si nos interesa que el corrector ortográfico de *Sublime Text 3* sea capaz de utilizar un listado de palabras en español, los correspondientes ficheros que hemos de descargar serán: `Spanish.aff`, `Spanish.dic` y `Spanish.txt`.
3. Si no vamos a clonar el repositorio a nuestro equipo y pretendemos bajar directamente los archivos desde *GitHub*, debemos tener cierto cuidado a la hora de hacerlo. No hay que utilizar la cásica estrategia de clic derecho y "Guardar enlace como..." sobre los enlaces que aparecen en el listado del repositorio, puesto que descargaríamos tres archivos en formato `.html`. Una posible manera de proceder sería abrir cada uno de los enlaces de interés en una nueva pestaña y emplear entonces la estrategia de clic derecho y "Guardar enlace como..." sobre el botón `Raw` que aparece en la parte superior derecha.
4. Una vez tenemos en nuestro haber los tres archivos asociados al idioma que nos interesa, acudiremos a la carpeta `Packages` de *Sublime Text 3*, cuya ruta podemos encontrar a través del menú `Preferences`, pulsando sobre el apartado `Browse Packages...`. En tal localización crearemos un directorio llamado `Language - Spanish` y ubicaremos ahí los mencionados tres ficheros.
5. Si ahora volvemos al apartado `Dictionary` del menú `View`, comprobaremos que podemos navegar por dos subapartados: uno asociado a los diccionarios para la lengua inglesa y otro para el correspondiente al idioma español. Seleccionamos este último y pulsamos la tecla `F6`, activando así el corrector ortográfico de *Sublime Text 3* en dicho idioma.
6. Los pasos 3 y 4 podemos repetirlos tantas veces como necesitemos en función del distinto número de diccionarios que estimemos que vayamos a emplear. El proceso que seguir es siempre el indicado, con los correspondientes cambios lógicos que cada nuevo idioma incorpora al procedimiento.

Dejo pendiente para una futura entrada explicar cómo he configurado *Sublime Text 3* para convertirlo en un más que agradable editor de texto plano orientado a trabajar con documentos de tipo *markdown*.
