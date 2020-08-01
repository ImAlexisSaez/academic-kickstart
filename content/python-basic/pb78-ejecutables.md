---
title: 78. Ejecutables
linktitle: 78. Ejecutables
toc: true
type: book
date: "2019-06-17T00:00:02+01:00"
lastmod: "2019-06-17T00:00:02+01:00"
draft: false
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

Ahora bien, tras ella aparece la propia terminal de *Python*, característica que quizá no nos interese y posiblemente solo deseemos trabajar con la interfaz gráfica de la calculadora. Para conseguirlo, hemos de incluir el modificador `--windowed`, en la llamada a `pyinstaller`, a la hora de crear el ejecutable:

```bash
pyinstaller --windowed calculadora.py
```

No obstante, la aplicación requiere de la presencia de todos los ficheros contenidos en el directorio `/calculadora/` para su correcto funcionamiento. Sería deseable que todo ello se ''compilase'' en un único archivo y que se pudiera ejecutar en cualquier ordenador, independientemente de si tiene o no instalado *Python*. El mencionado comportamiento se obtiene agregando el modificador `--onefile` a la anterior instrucción, esto es,

```bash
pyinstaller --windowed --onefile calculadora.py
```

Ahora, en la carpeta `/dist/` hallamos únicamente el archivo.

Finalmente, de cara a modificar el icono de la aplicación, simplemente hemos de añadir un nuevo modificador a la instrucción `pyinstaller`: `--icon=./icon.ico`, siendo `icon.ico` el nombre del archivo que contiene el icono y que se ubica en el mismo directorio donde se halla el fichero `calculadora.py`. Así pues, tecleamos:

```bash
pyinstaller --windowed --onefile --icon=./icon.ico calculadora.py
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/78/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

