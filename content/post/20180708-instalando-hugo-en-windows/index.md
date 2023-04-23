---
title: "Instalando Hugo en Windows"
slug: "instalando-hugo-en-windows"
subtitle: "Un soplo de aire fresco en comparación con Jekyll"
summary: "Lección 2: cómo instalar Hugo en Windows sin morir en el intento."

date: 2018-07-08T05:59:39+02:00
lastmod: 2018-07-08T05:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Hugo", "Metablog", "Windows"]
categories: ["Tutoriales"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Carl Heyerdahl](https://unsplash.com/@carlheyerdahl), disponible en [Unsplash](https://unsplash.com/photos/KE0nC8-58MQ)."
---

Llevar a cabo la instalación de *Hugo* en *Windows* es extremadamente fácil, hecho que nos permite empezar a experimentar con esta tecnología en apenas unos minutos. Veamos, sin más dilación, todo el proceso en detalle.

Así pues, en este segundo artículo correspondiente a la etiqueta [Metablog](/etiqueta/metablog/), retomaremos la senda en el lugar que nos quedamos al finalizar la [primera entrada](/2018/07/05/preparando-el-equipo-para-hugo/). Recuerdo que, en ella, instalamos un par de útiles herramientas en nuestro equipo (*git* y *Sublime Text 3*) y nos creamos una cuenta en el portal *GitHub*, que será donde alojemos tanto el código fuente de nuestros futuros sitios web, como los propios sitios web en sí.

En la documentación oficial de *Hugo*, existe una extensa página dedicada a su instalación, con una sección que orienta específicamente a los usuarios de *Windows* y a la que podemos acceder directamente a través de [este enlace](https://gohugo.io/getting-started/installing#windows).

Los desarrolladores han intentado que la experiencia de instalación sea muy intuitiva, pero, en mi opinión, alguna de las indicaciones puede no ser coherente con la estructura de archivos y carpetas que hayamos decidido implementar en nuestros equipos. ¿A qué se debe esta afirmación? Por ejemplo:

- *Hugo* no deja de ser simplemente un programa, por lo que en lugar de instalarlo donde indica la guía, quizá sería mejor opción ubicarlo en la carpeta `Archivos de programa`.
- Nos señalan, en la menciona guía, un directorio muy específico donde almacenar nuestros sitios web. No obstante, aunque vayamos a utilizar la pareja *git* + *GitHub*, es posible que nos interese, además, utilizar un servicio de alojamiento de archivos y, por tanto, ubicar las páginas en otra ruta diferente.

Simplemente lo comento para que quede claro que las instrucciones que, a continuación, compartiré admiten cierta flexibilidad a la hora de llevarlas a cabo. Dicho esto, sin más preámbulos, veamos cómo instalar *Hugo* en *Windows*.

En primer lugar, bien desde la terminal, bien desde el explorador de archivos de *Windows*, creamos en el directorio raíz de nuestro disco duro (generalmente `C:\`) una carpeta denominada `Hugo`. En su interior engendramos otras dos carpetas: `bin`, donde almacenaremos la aplicación, y `Sites`, donde ubicaremos nuestros futuros sitios web. Al final, debemos tener disponibles las siguientes dos rutas:

- `C:\Hugo\bin\`, y
- `C:\Hugo\Sites\`.

Para ir acostumbrándonos al uso de la terminal *Git Bash*, todo el anterior proceso lo podíamos haber conseguido escribiendo en ella la siguiente serie de comandos:

```bash
cd c:
```

```bash
mkdir Hugo
```

```bash
cd Hugo
```

```bash
mkdir bin Sites
```

A continuación, abrimos la página de descarga de *Hugo* siguiendo [este enlace](https://github.com/gohugoio/hugo/releases). A la hora de escribir estas líneas, la versión más reciente es la etiquetada como `v0.42.2`. Ahora, desplazamos con cuidado hacia abajo el extenso listado de ficheros, hasta dar con el adecuado para nuestro sistema operativo (en mi caso es `hugo_0.42.2_Windows-64bit.zip`). Hacemos clic sobre él e inmediatamente comenzará la descarga a nuestro disco duro de un archivo comprimido.

Acto seguido, descomprimimos el contenido de dicho archivo en la ruta `C:\Hugo\bin\` (o donde hayamos decidido que sería un buen sitio para almacenar la aplicación) y borramos el fichero que hemos descargado, pues no vamos a necesitarlo en un futuro próximo.

De esta manera, si desde la terminal nos desplazamos hasta la anterior ruta y escribimos `hugo version`, recibiremos el siguiente mensaje `Hugo Static Site Generator v0.42.2 windows/amd64 BuildDate: 2018-06-28T12:36:53Z`, que indica que hemos llevado a cabo la instalación con éxito.

No obstante, rápidamente vamos a encontrar un pequeño inconveniente a la hora de empezar a experimentar con *Hugo*. Si escribimos `hugo version` en cualquier otra ruta distinta a la indicada arriba, recibiremos en la terminal un mensaje de error como este: `bash: hugo: command not found`. Dado que nuestra intención es poder utilizar la aplicación en cualquier ruta de nuestro disco duro, tenemos que añadir la ubicación de *Hugo* al `PATH` de *Windows*.

Cada versión de *Windows* tiene una manera más o menos distinta y, en ocasiones, ciertamente enrevesada, de editar el `PATH`. Para ello, en *Windows 10*, comenzamos pulsando el botón de inicio y seleccionamos *Configuración*, accediendo así a la siguiente ventana:

{{< figure src="20180708-img01.png" title="Configuración de *Windows*." numbered="true" >}}

En el cuadro de búsqueda escribimos "configuración avanzada" y seleccionamos la opción *Ver la configuración avanzada del sistema*, tal y como figura en la siguiente imagen:

{{< figure src="20180708-img02.png" title="Ilustración del cuadro de búsqueda." numbered="true" >}}

Apareciendo así esta ventana:

{{< figure src="20180708-img03.png" title="Ventana de configuración avanzada del sistema." numbered="true" >}}

Hacemos clic en el botón *Variables de entorno...*, surgiendo entonces una nueva ventana. En ella seleccionamos la fila del primer cuadro denominada *Path* y pulsamos el botón *Editar...*, que aparece justo debajo de dicho cuadro.

{{< figure src="20180708-img04.png" title="Ventana de variables de entorno." numbered="true" >}}

Surge, cual capricho de un diabólico destino que parece que quiere poner nuestro temple a prueba, otra nueva ventana (ya por fin la última), donde tenemos que hacer clic sobre el botón *Nuevo* y escribir `C:\Hugo\bin\`. Finalmente, solo nos resta ir pulsando sobre el botón *Aceptar* sucesivas veces, hasta cerrar por completo la ristra de ventanas precedentes que en unos segundos hemos acumulado.

Así, si en cualquier ruta del sistema ahora tecleamos en la terminal `hugo version`, no aparecerá el anterior mensaje de comando desconocido, sino la versión de la aplicación instalada, tal y como pretendíamos.

En el próximo artículo correspondiente a la etiqueta [Metablog](/etiqueta/metablog/) exploraremos el proceso de creación de un sitio web utilizando *Hugo*.
