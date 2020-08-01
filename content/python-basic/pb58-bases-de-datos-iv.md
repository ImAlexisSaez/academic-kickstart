---
title: 58. Bases de datos IV
linktitle: 58. BBDD IV
toc: true
type: book
date: "2019-05-31T00:00:01+01:00"
lastmod: "2019-05-31T00:00:01+01:00"
draft: false
weight: 58
---

## Vídeo

{{< youtube m_FzVf9JTV8 >}}

## Notas personales

En esta lección, abordaremos la cláusula `UNIQUE` y operaciones *CRUD* (*Create, Read, Update, Delete*). Para ello, partamos de un código ciertamente similar a los examinados en anteriores ocasiones:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute('''
    CREATE TABLE PRODUCTOS (
    ID INTEGER PRIMARY KEY AUTOINCREMENT,
    NOMBRE_ARTICULO VARCHAR(50) UNIQUE,
    PRECIO INTEGER,
    SECCION VARCHAR(20))
    ''')

productos = [("Pelota", 20, "Juguetería"),
             ("Pantalón", 15, "Confección"),
             ("Destornillador", 25, "Ferretería"),
             ("Jarrón", 45, "Cerámica")]

mi_cursor.executemany("INSERT INTO PRODUCTOS VALUES (NULL, ?, ?, ?)",
                      productos)

mi_conexion.commit()

mi_conexion.close()
```

*Notas*:

- Recordemos que al incorporar `PRIMARY KEY` en el campo `ID` (nuestro anterior campo `CODIGO_ARTICULO`) lo convertimos en clave y, de manera implícita, estamos forzando que la infomación registrada en él no pueda repetirse.
- Añadiendo `UNIQUE` al campo `NOMBRE_ARTICULO` impedimos la posibilidad de que dos artículos posean el mismo nombre. Esta cláusula la podemos ubicar en tantos campos como deseemos.

¿Qué sucede ahora si intentamos insertar un registro cuyo para `NOMBRE_ARTICULO` ya figura en la base de datos (BBDD)?

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("INSERT INTO PRODUCTOS VALUES (NULL, 'Pelota', 57, 'Deportes')")

mi_conexion.commit()

mi_conexion.close()
```

```bash
Traceback (most recent call last):
  File "bbdd_2.py", line 7, in <module>
    mi_cursor.execute("INSERT INTO PRODUCTOS VALUES (NULL, 'Pelota', 57, 'Deportes')")
sqlite3.IntegrityError: UNIQUE constraint failed: PRODUCTOS.NOMBRE_ARTICULO
```

Esto es, *Python* arroja un error de integridad por violarse la restricción de unicidad para el campo `NOMBRE_ARTICULO`.

A continuación, abordemos las operaciones de tipo operaciones *CRUD* (*Create, Read, Update, Delete*). Aunque las dos primeras ya las hemos analizado en lecciones anteriores, recordemos brevemente cómo realizar una de tipo *Read*:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("SELECT * FROM PRODUCTOS WHERE SECCION='Confección'")

productos = mi_cursor.fetchall()

for producto in productos:
    print(producto)

mi_conexion.commit()

mi_conexion.close()
```

```bash
(2, 'Pantalón', 15, 'Confección')
```

*Nota*: las instrucciones suministradas a la BBDD son *case sensitive*, es decir, hemos de proceder con cautela a la hora de introducir los datos y utilizar adecuadamente las mayúsculas y las minúsculas (además de los acentos y otros posibles caracteres conflictivos).

Para realizar una actualización de registro (operación de tipo *Update*), simplemente hemos de modificar la instrucción *SQL* de manera acertada:

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("UPDATE PRODUCTOS SET PRECIO=35 WHERE NOMBRE_ARTICULO='Pelota'")

mi_conexion.commit()

mi_conexion.close()
```

Finalmente, para borrar registros (operación de tipo *Delete*), la manera de proceder es similar a la vista antes, ya que únicamente hemos de emplear la instrucción *SQL* adecuada (y borrar por un criterio que no ocasione conflictos con otros registros almacenados en la BBDD):

```python
import sqlite3

mi_conexion = sqlite3.connect("gestion-productos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("DELETE FROM PRODUCTOS WHERE ID=1")

mi_conexion.commit()

mi_conexion.close()
```

*Nota*: cuando utilicemos una cláusula `DELETE`, no hemos de olvidar jamás añadir otra de tipo `WHERE` o terminaremos suprimiendo la tabla completa en lugar de uno o varios registros.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/58/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
