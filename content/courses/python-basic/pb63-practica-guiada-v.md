---
title: 63. Práctica guiada V
linktitle: 63. Práctica V
toc: true
type: docs
date: "2019-06-04T00:00:01+01:00"
lastmod: "2019-06-04T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 63

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 63
---

## Vídeo

{{< youtube mNzHPglBuUk >}}

## Notas personales

En esta lección, analizaremos cómo limpiar los campos de registros (por si el usuario comete algún error al transcribir los datos) e insertar datos en la base de datos (BBDD), es decir, ejecutar la operación de tipo *Create*.

Para empezar, de cara a poder realizar manipulaciones sobre el texto que un usuario escriba en los campos de registros, hemos de emplear variables de tipo `StringVar`:

```python
id_data = StringVar()
name_data = StringVar()
lastname_data = StringVar()
address_data = StringVar()
password_data = StringVar()
```

A continuación, las asignamos a sus correspondientes `Entry`:

```python
id_entry = Entry(campos_frame, width=40, textvariable=id_data)
name_entry = Entry(campos_frame, width=40, textvariable=name_data)
lastname_entry = Entry(campos_frame, width=40, textvariable=lastname_data)
address_entry = Entry(campos_frame, width=40, textvariable=address_data)
password_entry = Entry(campos_frame, width=40, textvariable=password_data)
```

Después, construimos la función que limpia los campos de registros:

```python
# Función que limpia los registros de la aplicación
def limpia_registros():
    id_data.set("")
    name_data.set("")
    lastname_data.set("")
    address_data.set("")
    password_data.set("")
    comment_text.delete(1.0, END)
```

*Notas*: 

- Notemos cómo se limpia un cuadro de comentario, ya que el procedimiento a seguir es un tanto diferente. Hemos de utilizar la función `delete()`, indicándole el punto de partida (`1.0`) y el de finalización (`END`).
- Al hilo de lo anterior, `END` es asimismo una instrucción de la librería `tkinter`, de manera que hemos de importarla si estamos siguiendo la estrategia de `from tkinter import ...`. De hecho, en mi código dicha instrucción comienza a adquirir una longitud considerable, siendo en la actualidad:

```python
from tkinter import Button, END, Entry, Frame, Label, Menu, messagebox, Scrollbar, StringVar, Text, Tk
```

Ahora, asignamos esta funcionalidad al elemento correspondiente el menú:

```python
borrar_menu.add_command(label="Borrar campos", command=limpia_registros)
```

Acto seguido, abordemos la primera operación *CRUD*, *Create*, que nos permitirá añadir registros a la BBDD. 

```python
def crud_create():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("INSERT INTO DATOS_USUARIOS VALUES (NULL, '" +
                   name_data.get() + "', '" + password_data.get() + "','" +
                   address_data.get() + "','" + password_data.get() + "','" +
                   comment_text.get("1.0", END) + "')")
    conexion.commit()
    messagebox.showinfo(
        title="Crear registro",
        message="Registro insertado con éxito en la base de datos.")
    conexion.close()
```

*Notas*: 

- No recogemos aquello que el usuario escribe en el campo *ID*, ya que lo hemos declarado en la tabla como clave primaria autoincrementable (de ahí el `NULL` en la instrucción *SQL* de arriba). Este proceder puede resultar un tanto confuso para el usuario y admite margen de mejora.
- Es muy sencillo equivocarse a la hora de escribir la anterior instrucción *SQL* por el elevado número de concatenaciones. Un enfoque alternativo consiste en escribir primero una serie de datos concretos de ejemplo y, después, poco a poco sustituir dichos datos por las correspondientes variables con sus métodos `get()` asociados.

Finalmente, añadimos la funcionalidad, tanto al elemento de menú correspondiente, como al botón que figura en la parte inferior de la aplicación:

```python
crud_menu.add_command(label="Crear", command=crud_create)

crear_button = Button(botones_frame, text="Create", command=crud_create)
```


## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/63/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
