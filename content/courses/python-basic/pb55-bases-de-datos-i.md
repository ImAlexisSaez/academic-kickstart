---
title: 55. Bases de datos I
linktitle: 55. BBDD I
toc: true
type: docs
date: "2019-05-29T00:00:01+01:00"
lastmod: "2019-05-29T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 55

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 55
---

## Vídeo

{{< youtube ZJuVQ9jUg-A >}}

## Notas personales

En esta lección, cambiamos de tercio y abordamos el tratamiento de las bases de datos (BBDD) en *Python*. Estudiaremos cómo crearlas, conectar con ellas e insertar registros en su interior.

*Python* es capaz de gestionar la información que se encuentra almacenada en diferentes gestores de bases de datos, como, por ejemplo:

- *SQL Server*
- *Oracle*
- *MySQL*
- *SQLite*
- *PostgreSQL*

En este curso trabajaremos, principalmente, con *MySQL* y *SQLite* debido a su popularidad. No obstante, ello requiere que tengamos unos mínimos conocimientos del lenguaje utilizado para realizar consultas en bases de datos: **SQL** (*Structured Query Language*).

Por lo que respecta a *SQLite*:

- Es un sistema de gestión de BBDD relacional.
- Está escrito en *C*, siendo de código abierto.
- La BBDD forma parte integral del programa y se guarda como un único fichero en *host*.

Así, entre sus ventajas, encontramos que ocupa muy poco espacio en disco y memoria, es muy eficiente y rápido, es multiplataforma, no requiere configuración o administración y es de dominio público, esto es, sin costo alguno añadido. Sin embargo, también posee asociadas una serie de desventajas, como que no admite cláusulas anidadas (de tipo `where`), no existen usuarios (no permite acceso simultáneo por parte de varios usuarios) y carece de clave foránea cuando se crea en modo consola.

A continuación, los pasos a seguir para conectar con una BBDD son:

1. Abrir (o crear) una conexión.
2. Crear un puntero (o cursor).
3. Ejecutar una consulta (*query*) *SQL*.
4. Manejar los resultados de la consulta.
    + Insertar, leer, actualizar, borrar (*Create*, *Read*, *Update*, *Delete*). 
5. Cerrar puntero.
6. Cerrar conexión.

En *Python*, comenzamos importando la librería `sqlite3` para luego crear la conexión con la BBDD. La primera vez que realizamos este proceso, al no haber disponible ninguna, procederemos a su creación.

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_conexion.close()
```

Al ejecutar el anterior bloque de código, aparece en el correspondiente directorio una BBDD de datos vacía, de nombre `base-de-datos`. Veamos, acto seguido, cómo crear nuestra primera tabla:

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("CREATE TABLE PRODUCTOS (NOMBRE_ARTICULO VARCHAR(50), PRECIO INTEGER, SECCION VARCHAR(20))")

mi_conexion.close()
```

Tras crear el puntero o cursor, `mi_cursor`, lanzamos, a través de la función `execute()`, el comando *SQL* correspondiente a la creación de una tabla que poseerá tres columnas. Si ejecutamos el anterior bloque de código, observaremos que el tamaño del fichero `base-de-datos` se incrementa y deja de estar vacío.

*Nota*: podemos investigar qué contiene el archivo `base-de-datos`, de manera visual, mediante la herramienta [DB Browser for SQLite](https://sqlitebrowser.org/).

A continuación, analicemos cómo insertar información en la tabla que acabamos de crear. Para ello, comentamos la anterior línea de código, que precisamente generaba la tabla (porque ya existe y entonces *Python* arrojaría un error llegado a ese momento), y ejecutamos, a través del cursor, la instrucción de *SQL* apropiada. Tras ello, verificamos que deseamos realizar el cambio en la tabla, utiliando el método `commit()` asociado a la conexión:

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("INSERT INTO PRODUCTOS VALUES('BALÓN', 15, 'DEPORTES')")

mi_conexion.commit()

mi_conexion.close()
```

*Nota técnica*: cuando trabajamos con cadenas de caracteres que poseen comillas anidadas, hemos de alternar los simbolos `'` y `"`.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/55/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
