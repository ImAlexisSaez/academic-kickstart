---
title: 37. Archivos I
linktitle: 37. Archivos I
toc: true
type: docs
date: "2019-05-14T00:00:01+01:00"
lastmod: "2019-05-14T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 37

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 37
---

## Vídeo

{{< youtube V87m9SltcI8 >}}

## Notas personales

En esta lección abordaremos cómo trabajar con ficheros externos de texto, utilizando para tal empresa el módulo `io`. Nuestro objetivo será conseguir la **persistencia de datos**, es decir, salvaguardar los datos que estamos manipulando para que no se pierdan al finalizar una sesión de *Python*.

Existen dos alternativas para conseguir el mencionado objetivo:

- Manejar archivos externos.
- Trabajar con bases de datos (BBDD).

Las fases necesarias para guardar cierta información en archivos externos son:

1. Creación del archivo externo.
2. Apertura del archivo externo.
3. Manipulación del archivo externo.
4. Cierre del archivo externo.

La documentación del módulo `io` la podemos encontrar en [este enlace](https://docs.python.org/3/library/io.html).

Veamos un ejemplo sencillo en el que crearemos un archivo donde almacenar una frase. Empecemos tecleando:

```python
from io import open

archivo_texto = open("prac37_files/archivo.txt", "w")
```

*Nota*: un archivo lo podemos abrir en modo lectura (`r`), escritura (`w`), agregar (`a`)... 

Si ahora acudimos al interior de la carpeta `prac37_files`, encontraremos un archivo de texto vacío denominado `archivo.txt`. En absoluto es necesario que almacenemos el fichero en una carpeta, pero únicamente procedo así para que el [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) mantenga una estructura coherente.

A continuación, veamos cómo incluir información (texto) en dicho archivo:

```python
from io import open

# Creación + Apertura
archivo_texto = open("prac37_files/archivo.txt", "w")

frase = "Es un estupendo día para estudiar Python\nen Youtube."

# Manipulación
archivo_texto.write(frase)

# Cierre
archivo_texto.close()
```

De esta manera, hemos incluido el texto declarado en la variable `frase` en el fichero `archivo.txt`.

Acto seguido, estudiemos cómo abrir un archivo en modo lectura y acceder a su contenido:

```python
from io import open

archivo_texto = open("prac37_files/archivo.txt", "r")

texto = archivo_texto.read()

archivo_texto.close()

print(texto)
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
```

Otro método que nos puede resultar de utilidad a la hora de leer un archivo es `readlines()`, que accede a la información almacenada línea a línea y la guarda en una lista:

```python
from io import open

archivo_texto = open("prac37_files/archivo.txt", "r")

lineas_texto = archivo_texto.readlines()

archivo_texto.close()

print(lineas_texto)
```

```bash
['Es un estupendo día para estudiar Python\n', 'en Youtube.']
```

Al ser una lista, podemos utilizar ahora todo lo que hemos aprendido sobre ellas:

```python
print(lineas_texto[0])
```

```bash
Es un estupendo día para estudiar Python
```

Finalmente, veamos cómo abrir un archivo para agregar información. Para no alterar el contenido de `archivo.txt`, almacenaremos sus frases en una variable, las escribiremos en un nuevo fichero, `archivo2.txt`, y sobre este último será donde agreguemos contenido adicional:

```python
from io import open

archivo1 = open("prac37_files/archivo.txt", "r")
texto = archivo1.read()
archivo1.close()

archivo2 = open("prac37_files/archivo2.txt", "w")
archivo2.write(texto)
archivo2.close()

archivo2 = open("prac37_files/archivo2.txt", "a")
archivo2.write("\n¡Mañana más!")
archivo2.close()
```

Si acudimos a la carpeta `prac37_files`, comprobaremos la existencia de un fichero denominado `archivo2.txt`, que contiene tres líneas.
