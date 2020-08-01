---
title: 62. Práctica guiada IV
linktitle: 62. Práctica IV
toc: true
type: book
date: "2019-06-03T00:00:01+01:00"
lastmod: "2019-06-03T00:00:01+01:00"
draft: false
weight: 62
---

## Vídeo

{{< youtube 5XPLCDp7nDk >}}

## Notas personales

En esta lección, implementaremos cierta funcionalidad a nuestra aplicación, comenzando por el menú *BBDD*. Programaremos la función que realiza la conexión a la base de datos (BBDD) y la que posibilita la opción de salir de la aplicación.

Por lo que respecta a la conexión de la BBDD, como la primera vez que pulsemos la función va a encargarse de crear la tabla, después hemos de controlar la excepción que aparece al volver a llamar la función con dicha tabla ya creada.

```python
# Función para conectar a la BBDD
def conecta_bbdd():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    try:
        cursor.execute('''
            CREATE TABLE DATOS_USUARIOS (
            ID INTEGER PRIMARY KEY AUTOINCREMENT,
            NOMBRE_USUARIO VARCHAR(50),
            APELLIDO VARCHAR(50),
            DIRECCION VARCHAR(50),
            PASSWORD VARCHAR(50),
            COMENTARIOS VARCHAR(250))
            ''')
    except sqlite3.OperationalError:
        pass
    finally:
        messagebox.showinfo(
            title="Conexión a la base de datos",
            message="La conexión a la base de datos se ha realizado con éxito."
        )
```

Acto seguido, acudimos a la instrucción que gestiona el elemento del menú *BBDD* correspondiente y la modificamos como sigue:

```python
bbdd_menu.add_command(label="Conectar", command=conecta_bbdd)
```

Finalmente, implementemos la función que gestiona la salida de la aplicación. El código es idéntico al visto en lecciones anteriores:

```python
# Función para salir de la aplicación
def sale_aplicacion():
    valor = messagebox.askquestion(
        title="Salir",
        message="¿Deseas realmente salir de la aplicación?")
    if valor == "yes":
        root.destroy()
```

Y añadimos la funcionalidad al correspondiente elemento del menú *BBDD*:

```python
bbdd_menu.add_command(label="Salir", command=sale_aplicacion)
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/62/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
