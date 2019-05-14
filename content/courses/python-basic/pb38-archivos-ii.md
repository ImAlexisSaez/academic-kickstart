---
title: 38. Archivos II
linktitle: 38. Archivos II
toc: true
type: docs
date: "2019-05-14T00:00:02+01:00"
lastmod: "2019-05-14T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 38

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 38
---

## Vídeo

{{< youtube 0dEYVSRYl_s >}}

## Notas personales

Continuemos el estudio de la manipulación de ficheros externos de texto, con el módulo `io`, analizando en esta ocasión cómo manejar punteros en texto.

Para ello, movamos el último archivo de texto generado en la lección anterior (`archivo2.txt`) a la carpeta `prac38_files`, para así mantener la coherencia de la estructura de ficheros del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0). Tras ello, tecleemos:

```python
from io import open

archivo = open("prac38_files/archivo2.txt", "r")

print(archivo.read())

archivo.close()
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
```

Si no indicamos lo contrario, la función `.read()` sitúa el puntero al inicio del archivo y comienza entonces su lectura. Cuando finaliza esta, la posición del puntero se ubica tras el último carácter. Esto implica que si ahora escribimos de nuevo la instrucción `print(archivo.read())`, nada se mostraría en la consola, puesto que tras la posición que ha quedado el puntero no existe información alguna.

Se puede inicializar la posición del puntero utilizando la función `.seek()`, que como argumento recibe el carácter desde el que deseamos comenzar la lectura del archivo.

```python
from io import open

archivo = open("prac38_files/archivo2.txt", "r")

print(archivo.read())

archivo.seek(0)  # Reinicio posición puntero

print(archivo.read())

archivo.seek(10)  # Establezco posición puntero en carácter 10

print(archivo.read())

archivo.close()
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
pendo día para estudiar Python
en Youtube.
¡Mañana más!
```

Con el método `.read()` también podemos modificar la función del puntero, aunque de manera algo diferente a cómo se lleva a cabo el proceso con `.seek()`. La primera lee hasta la posición del puntero que le indiquemos como argumento, mientras que la segunda posiciona el puntero en una posición y la lectura se efectúa a partir de dicha posición.

```python
from io import open

archivo = open("prac38_files/archivo2.txt", "r")

print(archivo.read(11))
print(archivo.read())

archivo.close()
```

```bash
Es un estup
endo día para estudiar Python
en Youtube.
¡Mañana más!
```

Para situar el puntero justo en medio de un archivo de texto podemos emplear la siguiente estrategia:

```python
from io import open

archivo = open("prac38_files/archivo2.txt", "r")

archivo.seek(len(archivo.read()) / 2)

print(archivo.read())

archivo.close()
```

```bash
r Python
en Youtube.
¡Mañana más!
```

¿Y si queremos situar el puntero al final de la primera línea?

```python
from io import open

archivo = open("prac38_files/archivo2.txt", "r")

archivo.seek(len(archivo.readline()))

print(archivo.read())

archivo.close()
```

```bash

en Youtube.
¡Mañana más!
```

Un archivo lo podemos abrir, simultáneamente, en modo lectura y escritura (`"r+"`), para realizar ambas acciones a la vez si nos es preciso. Generemos un fichero denominado `archivo3.txt`, con el mismo contenido que aquel con el que llevamos trabajando a lo largo de toda esta lección. Después, tecleamos:

```python
from io import open

archivo = open("prac38_files/archivo3.txt", "r+")  # lectura y escritura

archivo.write("Comienzo del texto: ")

archivo.seek(0)

print(archivo.read())

archivo.close()
```

```bash
Comienzo del texto: para estudiar Python
en Youtube.
¡Mañana más!
```

Al abrir el archivo, el puntero se posiciona al principio del mismo. Así, cuando usamos el método `.write()`, efectivamente sobreescribimos el contenido que originalmente hubiera (en tantas posiciones como longitud posea la nueva cadena de texto).

Así, para incluir una línea en mitad del documento (la segunda en este caso particular), un posible enfoque sería:

```python
from io import open

archivo = open("prac38_files/archivo3.txt", "r+")  # lectura y escritura

lineas = archivo.readlines()

lineas[1] = "Esta línea ha sido incluida desde el exterior.\n"

archivo.seek(0)

archivo.writelines(lineas)

archivo.seek(0)

print(archivo.read())

archivo.close()
```

```bash
Comienzo del texto: para estudiar Python
Esta línea ha sido incluida desde el exterior.
¡Mañana más!
```




