---
title: 39. Serialización I
linktitle: 39. Serialización I
toc: true
type: docs
date: "2019-05-15T00:00:01+01:00"
lastmod: "2019-05-15T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 39

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 39
---

## Vídeo

{{< youtube SOimkkfQIOM >}}

## Notas personales

En esta lección estudiaremos cómo serializar colecciones de ciertos objetos. La **serialización** consiste en guardar en un fichero externo una lista, un diccionario o, incluso, un objeto; con la particularidad de que la codificación de dicho fichero es binaria.

Esta estrategia resulta de utilidad a la hora de compartir archivos por Internet, ya que su distribución es más sencilla, o bien si deseamos guardarlo en un dispositivo de almacenamiento externo o en una base de datos.

Para tal empresa utilizaremos la biblioteca de *Python* `pickle`, para aprovechar los métodos:

- `dump()`: vuelca datos en un fichero binario externo, y
- `load()`: carga datos de un fichero binario externo.

Veamos un ejemplo sencillo de aplicación de ambas funciones. Almacenaremos en un archivo binario externo una lista de nombres y, posteriormente, la rescataremos:

```python
import pickle

nombres = ["Pedro", "Ana", "María", "Isabel"]

fichero = open("prac39_files/lista_nombres", "wb")

pickle.dump(nombres, fichero)

fichero.close()

del fichero
```

*Notas*:

- A la hora de crear el fichero externo en modo escritura, con el método `open()`, hemos de indicarle que esta será binaria, para lo cual el correspondiente parámetro toma como valor de argumento `"wb"`.
- La instrucción `del` borra el puntero de la memoria hacia la variable `fichero`, dejando de estar disponible su acceso a partir de ese momento.
- Al ejecutar el anterior bloque de código, en la carpeta denominada `prac39_files` (designada así para conservar la coherencia en la estructura del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0)), aparecerá un archivo externo de tipo binario denominado `lista_nombres`.

A continuamos, veamos cómo rescatar la información que reside en el interior del mencionado fichero.

```python
import pickle

fichero = open("prac39_files/lista_nombres", "rb")

lista = pickle.load(fichero)

fichero.close()

print(lista)
```

```bash
['Pedro', 'Ana', 'María', 'Isabel']
```

*Nota*: para activar el modo de lectura de archivos binarios, el  parámetro correspondiente de la función `open()` ha de tomar el valor de argumento `"rb"`.
