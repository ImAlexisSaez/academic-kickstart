---
title: 57. Bases de datos III
linktitle: 57. BBDD III
toc: true
type: docs
date: "2019-05-30T00:00:01+01:00"
lastmod: "2019-05-30T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 57

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 57
---

## Vídeo

{{< youtube HVd6mPiD3pc >}}

## Notas personales

En esta lección, estudiaremos cómo gestionar las claves principales de nuestras bases de datos (BBDD). Los registros de una BBDD relacional han de estar identificados de manera única mediante un **campo clave**.

Hasta el momento, hemos creado una tabla en nuestra BBDD e insertado algunos registros, pero carece de dicho campo clave. Analicemos cómo añadir esta característica a las tablas de una BBDD. Para ello, partamos del siguiente bloque de código:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_conexion.commit()

mi_conexion.close()
```

En primer lugar, generemos una tabla, denominada `PRODUCTOS`, cuyos registros se van a caracterizar por poseer cuatro campos, uno de ellos clave. Así, tras la declaración del cursor, tecleamos:

```python
mi_cursor.execute('''
    CREATE TABLE PRODUCTOS (
    CODIGO_ARTICULO VARCHAR(4) PRIMARY KEY,
    NOMBRE_ARTICULO VARCHAR(50),
    PRECIO INTEGER,
    SECCION VARCHAR(20))
    ''')
```

Como apreciamos, la única novedad, con respecto a lecciones anteriores, es la aparición de la instrucción `PRIMARY KEY`, que convierte en clave el respectivo campo declarado, `CODIGO_ARTICULO` en este caso concreto. Por otro lado, el número que figura en el tipo de campo `VARCHAR` indica su longitud máxima.

Acto seguido, insertamos algunos registros en la tabla `PRODUCTOS`:

```python
productos = [("AR01", "Pelota", 20, "Juguetería"),
             ("AR02", "Pantalón", 15, "Confección"),
             ("AR03", "Destornillador", 25, "Ferretería"),
             ("AR04", "Jarrón", 45, "Cerámica")]

mi_cursor.executemany("INSERT INTO PRODUCTOS VALUES (?, ?, ?, ?)", productos)
```

Al ejecutar el programa, observamos que en el directorio donde hemos almacenado el código aparece un archivo denominado `gestion-productos`, que contiene la BBDD recién generada. 

A continuación, insertemos un nuevo registro en la BBDD:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("INSERT INTO PRODUCTOS VALUES ('AR05', 'Tren', 15, 'Juguetería')")

mi_conexion.commit()

mi_conexion.close()
```

Si ahora intentamos añadir un nuevo artículo a la BBDD cuyo código coincida con uno de los asignados a los cuatro productos existentes, *Python* nos arrojará un error:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("INSERT INTO PRODUCTOS VALUES ('AR03', 'Portátil', 750, 'Informática')")

mi_conexion.commit()

mi_conexion.close()
```

```bash
Traceback (most recent call last):
  File "bbdd_3.py", line 7, in <module>
    mi_cursor.execute("INSERT INTO PRODUCTOS VALUES ('AR03', 'Portátil', 750, 'Informática')")
sqlite3.IntegrityError: UNIQUE constraint failed: PRODUCTOS.CODIGO_ARTICULO
```

En la práctica, por comodidad, la construcción e inserción del campo clave se suele automatizar. Para ello, la estrategia consiste en crear un campo clave de tipo entero que sea autoincrementable.

Retomemos el primer ejemplo examinado en esta lección (modificando el fichero que contiene la BBDD) y estudiemos cómo implementar la funcionalidad comentada:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos-2")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute('''
    CREATE TABLE PRODUCTOS (
    ID INTEGER PRIMARY KEY AUTOINCREMENT,
    NOMBRE_ARTICULO VARCHAR(50),
    PRECIO INTEGER,
    SECCION VARCHAR(20))
    ''')

productos = [("Pelota", 20, "Juguetería"),
             ("Pantalón", 15, "Confección"),
             ("Destornillador", 25, "Ferretería"),
             ("Jarrón", 45, "Cerámica")]

mi_cursor.executemany("INSERT INTO PRODUCTOS VALUES (NULL, ?, ?, ?)", productos)

mi_conexion.commit()

mi_conexion.close()
```

*Notas*:

- Por convención, los campos de una tabla que van a ser automatizados reciben el nombre de `ID`.
- Con la instrucción `AUTOINCREMENT` conseguimos la mencionada gestión automática del campo entero que ahora hemos declarado como clave.
- La instrucción donde realizamos la llamada a la función `executemany()` hemos de modificarla, con respecto a lo programado anteriormente, ya que las tuplas de `productos` poseen tres elementos, mientras que figuran cuatro símbolos `?` en el comando *SQL* `INSERT INTO`. Para solucionar este escollo, sustituimos el primer `?` por la instrucción `NULL`, acción que permitirá a *Python* gestionar el campo clave de forma automática.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/57/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
