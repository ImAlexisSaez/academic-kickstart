---
title: 56. Bases de datos II
linktitle: 56. BBDD II
toc: true
type: docs
date: "2019-05-29T00:00:02+01:00"
lastmod: "2019-05-29T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 56

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 56
---

## Vídeo

{{< youtube eM0MkDc34qo >}}

## Notas personales

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

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/56/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
