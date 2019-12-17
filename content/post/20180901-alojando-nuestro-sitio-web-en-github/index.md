---
title: "Alojando nuestro sitio web en GitHub"
slug: "alojando-nuestro-sitio-web-en-github"
subtitle: "It's globally alive!"
summary: "Lección 8: analizamos cómo utilizar GitHub para publicar nuestra página web."

date: 2018-09-01T05:59:39+02:00
lastmod: 2018-09-01T05:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Hugo", "GitHub"]
categories: ["Tutoriales"]
projects: ["metablog"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Soroush golpoor](https://unsplash.com/@soroushgolpoor), disponible en [Unsplash](https://unsplash.com/photos/mbUXFI5ZpLc)."
---

A estas alturas de la película, seguramente con algún que otro artículo redactado y revisado localmente de manera concienzuda, no nos queda más remedio que ocuparnos de un asunto un tanto tedioso: el alojamiento de nuestro sitio web en *Internet*.

Para tal empresa he optado por *GitHub*, que nos permite alojar páginas web estáticas de manera gratuita (¡y sin publicidad!). Desgraciadamente, el proceso dista de ser intuitivo, por lo que examinaremos todos y cada uno de los pasos de la [guía oficial](https://gohugo.io/hosting-and-deployment/hosting-on-github/) con sumo detalle.

Para empezar, existe una serie de requisitos que hemos de cumplir para subir nuestro sitio web a *GitHub* y son:

- Tener instalado en nuestro equipo una versión de *Git* superior a la `2.8`.
- Disponer de una cuenta de usuario en *GitHub*.
- Contar con una página web lista para ser publicada en *Internet*.

Por lo que respecta a los dos primeros puntos del listado anterior, si estamos siguiendo el [Proyecto Metablog](/proyecto/metablog/) desde sus orígenes, no supondrán problema alguno, pues fueron abordados en la [primera entrada](/2018/07/05/preparando-el-equipo-para-hugo/) de la serie. En cuanto al tercer punto, con todo el trabajo que llevamos acumulado hasta el momento, es más que posible que entre nuestras manos tengamos ya un esbozo de sitio web que merezca la pena mostrar al resto del mundo.

Una vez comprobado que satisfacemos los requisitos del procedimiento, el primer paso a realizar consiste en crear dos nuevos repositorios en nuestra cuenta de *GitHub*. Para ello, acudimos a la página de nuestro perfil en *GitHub* y hacemos clic en el símbolo `+` situado en la parte derecha del menú superior, para, a continuación, seleccionar la opción `New repositoy`.

{{< figure src="20180901-img01.png" title="Creación de un nuevo repositorio en *GitHub*." numbered="true" >}}

El primer repositorio que crearemos estará dedicado a almacenar el código fuente de nuestro sitio web y, en un alarde de infinita originalidad, lo denominaremos `sitio-web`, tal y como figura en la siguiente imagen. Cuando hayamos rellenado el campo `Repository name` haremos clic en el botón `Create repository`.

{{< figure src="20180901-img02.png" title="Elección del nombre del repositorio." numbered="true" >}}

A continuación, de las tres opciones que nos ofrece la página que aparece ante nosotros, vamos a escoger la segunda, ya que cuando en [esta entrada](/2018/07/11/creando-un-sitio-web-con-hugo/) generamos nuestro primer sitio web, a la vez iniciamos un repositorio *Git*. Aquella acción, que en su momento podía parecer un tanto extraña, queda ahora totalmente justificada.

Así pues, abrimos la terminal del sistema, nos desplazamos hasta el directorio raíz donde hayamos decidido almacenar localmente nuestro sitio web y tecleamos:

```bash
git remote add origin https://github.com/<USERNAME>/sitio-web.git
```

En mi caso, en lugar de `<USERNAME>`, aparece directamente `ImAlexisSaez`. Cada uno de nosotros tendrá definida esa parte del comando de manera diferente, por lo que recomiendo encarecidamente copiar la instrucción de la página de *GitHub* en lugar de la que aparece arriba.

Acto seguido, escribimos en la terminal:

```bash
git push -u origin master
```

De esta manera, transcurridos unos segundos, tendremos disponible en *GitHub* una copia del código fuente que permite generar nuestra página web estática.

A continuación, volvemos a *GitHub* y creamos un nuevo repositorio. Este último tendrá un nombre especial que será, además, la dirección de acceso a nuestro sitio web. Hemos de combinar nuestra cuenta de usuario en *GitHub* con la extensión `.github.io`. Por ejemplo, en mi caso queda `ImAlexisSaez.github.io` y así es como rellené en su momento el campo `Repository name`. Una vez escrito, simplemente tenemos que hacer clic en el botón `Create repository`.

Volvemos a la terminal del sistema y tecleamos `hugo server`, para poder dar así una última revisión local a nuestro sitio web, utilizando la dirección ``http://localhost:1313`, y comprobar que todo está en perfecto estado. Cuando estemos satisfechos, acudimos de nuevo a la terminal del sistema y cerramos el servidor local, empleando para ello la combinación de teclas `Ctrl + c`.

Acto seguido, escribimos:

```bash
rm -rf public
```

Este comando borra por completo la carpeta `public`, que se encuentra en el directorio donde tenemos almacenado localmente nuestro sitio web. Dicha carpeta se genera automáticamente cada vez que tecleamos `hugo server` en la terminal del sistema, y contiene la versión final de nuestra página web.

El siguiente paso, precisamente, es crear un submódulo de manera que la carpeta `public` apunte a otra dirección de *GitHub*. Para ello, desde la terminal del sistema, tecleamos

```bash
git submodule add -b master git@github.com:<USERNAME>/<USERNAME>.github.io.git public
```

donde sustituiremos `<USERNAME>` por el nombre de nuestra cuenta de usuario en *GitHub* (por ejemplo, `ImAlexisSaez` en mi caso).

¡Ya casi tenemos todo a punto! Únicamente hemos de abrir *Sublime Text 3* y en un archivo, que guardaremos como `deploy.sh` en el directorio raíz donde hayamos almacenado localmente nuestro sitio web, copiamos el siguiente bloque de código:

```bash
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project.
hugo # if using a theme, replace with `hugo -t <YOURTHEME>`

# Go To Public folder
cd public
# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin master

# Come Back up to the Project Root
cd ..
```

El anterior bloque de código se encarga, de manera automática, del proceso de subida de nuestro sitio web a *GitHub*. Para utilizarlo, desde la terminal del sistema, nos situaremos en el directorio raíz donde hayamos decidido almacenar nuestro sitio web y teclearemos

```bash
./deploy.sh "Mensaje que resuma los cambios"
```

En mi caso, no me suelo esforzar mucho en declarar mensajes óptimamente descriptivos y, por ejemplo, cuando suba esta entrada el comando será del estilo `./deploy.sh "Añade entrada 20180901"`. Los mensajes asociados al repositorio donde guardo el código fuente sí que intento que sean más expresivos y reflejen adecuadamente los cambios de las diferentes versiones.

Con esto, damos por finalizado el proceso y nuestro sitio web será ahora accesible para todo el mundo a través de la dirección web que proporciona el segundo repositorio que hemos creado (en mi caso `https://imalexissaez.github.io/`).

En la siguiente entrada del [Proyecto Metablog](/proyecto/metablog/) posiblemente empecemos a realizar cambios en la hoja de estilos *CSS* y personalizar todavía más el tema *Beautiful Hugo*.
