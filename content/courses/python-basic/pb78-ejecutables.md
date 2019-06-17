---
title: 78. Ejecutables
linktitle: 78. Ejecutables
toc: true
type: docs
date: "2019-06-17T00:00:02+01:00"
lastmod: "2019-06-17T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 78

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 78
---

## Vídeo

{{< youtube Vr9vl0qlggE >}}

## Notas personales

En esta lección, estudiaremos cómo generar un ejecutable de una aplicación escrita en *Python* y que tomará el formato nativo del sistema operativo en el que estemos trabajando (`.exe` en *Windows*, por ejemplo).

Para empezar, desde la terminal del sistema, instalamos `pyinstaller`, utilizando para ello la instrucción:

```bash
pip3 install pyinstaller
```

A continuación, rescatemos los archivos de la aplicación que simulaba una calculadora, correspondiente a la lección 50. Generemos una copia de ellos, por coherencia con la estructura del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0), en el directorio `/lecciones/78/`.

Ahora, desde la terminal, nos desplazamos a dicho directorio y tecleamos:

```bash
pyinstaller calculadora.py
```

Esto es, la instrucción `pyinstaller` seguida del nombre del archivo del cual deseamos generar un ejecutable. 

El proceso da a luz a una cantidad considerable de ficheros y carpetas, siendo de nuestro interés la denominada `/dist/`, en cuyo interior encontraremos otra designada como `/calculadora/`, que contiene la aplicación lista para ser distribuida. Si hacemos doble clic sobre `calculadora.exe`, podemos corroborar que la aplicación funciona a la perfección.

*Nota técnica*: la calculadora que diseñé poseía icono y, curiosamente, `pyinstaller` no genera una copia de él en la carpeta `/dist/`, por lo que hemos de moverlo manualmente al directorio `/calculadora/` para que la aplicación se ejecute con éxito.

Ahora bien, tras ella aparece la propia terminal de *Python*, característica que quizá no nos interese y posiblemente solo deseemos trabajar con la interfaz gráfica de la calculadora. Para conseguirlo, hemos de incluir el modificador `--windowed`, en la llamada a `pyinstaller`, a la hora de crear el ejecutable:

```bash
pyinstaller --windowed calculadora.py
```

No obstante, la aplicación requiere de la presencia de todos los ficheros contenidos en el directorio `/calculadora/` para su correcto funcionamiento. Sería deseable que todo ello se ''compilase'' en un único archivo y que se pudiera ejecutar en cualquier ordenador, independientemente de si tiene o no instalado *Python*. El mencionado comportamiento se obtiene agregando el modificador `--onefile` a la anterior instrucción, esto es,

```bash
pyinstaller --windowed --onefile calculadora.py
```

Ahora, en la carpeta `/dist/` hallamos únicamente el archivo.

*Nota ténica*: incluso utilizando esta última estrategia, es necesario que movamos manualmente el archivo del icono a la carpeta donde se ha generado el ejecutable.

Finalmente, para solventar el problema del icono que nos viene acompañando desde el inicio de esta lección, añadimos un nuevo modificador a la instrucción `pyinstaller`, `--icon=./icon.ico`, ya que así es como se denomina el archivo que contiene el icono. Así pues, tecleamos:

```bash
pyinstaller --windowed --onefile --icon=./icon.ico calculadora.py
```

*Nota técnica*: ni tan siquiera así evitamos el problema, pero ahora la aplicación posee como icono el asignado.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/78/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

