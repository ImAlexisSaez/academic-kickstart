---
title: "Curso de Python #10 (Nivel básico)"
slug: "curso-de-python-10-nivel-basico"
subtitle: "Lección 10: Bases de datos"
summary: "Recopilación de las notas personales (con códigos fuente incluidos) tomadas durante la realización del recomendable curso 'Python desde 0', disponible en la plataforma YouTube y ofrecido por el canal 'Píldoras Informáticas'."

date: 2019-08-28T05:59:39+02:00
lastmod: 2019-08-28T05:59:39+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Python"]
categories: ["Programación"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Chris Ried](https://unsplash.com/es/@cdr6934), disponible en [Unsplash](https://unsplash.com/es/fotos/ieic5Tq8YMk)."
---

## 1. Bases de datos I

### 1.1. Vídeo

{{< youtube ZJuVQ9jUg-A >}}

### 1.2. Notas personales

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

### 1.3. Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/55/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

## 2. Bases de datos II

### 2.1. Vídeo

{{< youtube eM0MkDc34qo >}}

### 2.2. Notas personales

En esta lección, aprenderemos cómo insertar varios registros simultáneamente en nuestra base de datos (BBDD), así como después estudiaremos cómo recuperar información de la BBDD.

En primer lugar, importemos la librería `sqlite3` y construyamos, tanto la conexión a la BBDD, como un cursor. Con tal objetivo en mente, tecleamos:

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_cursor = mi_conexion.cursor()
```

A continuación, mediante una lista de tuplas, establecemos los productos que nos interese insertar en la BBDD:

```python
productos = [("Camiseta", 10, "Deportes"), ("Jarrón", 90, "Cerámica"),
             ("Camión", 20, "Juguetería")]
```

y con el método `executemany()` ejecutamos la instrucción *SQL* adecuada:

```python
mi_cursor.executemany("INSERT INTO PRODUCTOS VALUES (?, ?, ?)", productos)
```

*Nota técnica*: en las instrucciones de *SQL* parametrizadas, hemos de insertar tantos interrogantes, `?`, como campos posee cada registro.

Finalmente, confirmamos los cambios y cerramos la conexión abierta:

```python
mi_conexion.commit()

mi_conexion.close()
```

Acto seguido, veamos cómo accedemos a la información registrada en la BBDD. Para ello, simplemente hemos de ejecutar, desde el cursor, una instrucción de *SQL* de tipo `SELECT`, para luego almacenar en una variable la información utilizando el método `fetchall()`:

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("SELECT * FROM PRODUCTOS")

productos = mi_cursor.fetchall()

print(productos)

mi_conexion.close()
```

```bash
[('BALÓN', 15, 'DEPORTES'), ('Camiseta', 10, 'Deportes'), ('Jarrón', 90, 'Cerámica'), ('Camión', 20, 'Juguetería')]
```

Ahora, aplicando aquello que conocemos sobre listas, podemos mostrar la información de manera más cómoda para el usuario:

```python
import sqlite3

mi_conexion = sqlite3.connect("base-de-datos")

mi_cursor = mi_conexion.cursor()

mi_cursor.execute("SELECT * FROM PRODUCTOS")

productos = mi_cursor.fetchall()

for producto in productos:
    print(producto)

mi_conexion.close()
```

```bash
('BALÓN', 15, 'DEPORTES')
('Camiseta', 10, 'Deportes')
('Jarrón', 90, 'Cerámica')
('Camión', 20, 'Juguetería')
```

### 2.3. Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/56/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

## 3. Bases de datos III

### 3.1. Vídeo

{{< youtube HVd6mPiD3pc >}}

### 3.2. Notas personales

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

### 3.3. Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/57/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

## 4. Bases de datos IV

### 4.1. Vídeo

{{< youtube m_FzVf9JTV8 >}}

### 4.2. Notas personales

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

### 4.3. Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/58/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
