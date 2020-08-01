---
title: 65. Práctica guiada VII
linktitle: 65. Práctica VII
toc: true
type: book
date: "2019-06-06T00:00:01+01:00"
lastmod: "2019-06-06T00:00:01+01:00"
draft: false
weight: 65
---

## Vídeo

{{< youtube nj-alxd7YvM >}}

## Notas personales

En esta lección, abordaremos cómo borrar registros (operación de tipo *Delete*) y la creación de consultas parametrizadas. 

En cuanto a la primera tarea, empecemos construyendo la correspondiente función:

```python
# Función que borra registros de la BBDD
def crud_delete():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("DELETE FROM DATOS_USUARIOS WHERE ID=" + id_data.get())
    conexion.commit()
    conexion.close()
    messagebox.showinfo(
        title="Borrar registro",
        message="Registro borrado con éxito en la base de datos.")
```

Acto seguido, añadimos la funcionalidad, tanto al elemento del menú asociado, como al botón correspondiente:

```python
crud_menu.add_command(label="Borrar", command=crud_delete)

delete_button = Button(botones_frame, text="Delete", command=crud_delete)
```

A continuación, analicemos cómo modificar algunas de las consultas *SQL* para hacerlas parametrizadas y que su escritura sea mucho más sencilla:

```python
# Función que inserta registros en la BBDD
def crud_create():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    datos = name_data.get(), lastname_data.get(), address_data.get(), password_data.get(), comment_text.get("1.0", END)
    cursor.execute("INSERT INTO DATOS_USUARIOS VALUES (NULL, ?, ?, ?, ?, ?)", (datos))
    conexion.commit()
    messagebox.showinfo(
        title="Crear registro",
        message="Registro insertado con éxito en la base de datos.")
    conexion.close()
```

```python
# Función que actualiza registros de la BBDD
def crud_update():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    datos = name_data.get(), lastname_data.get(), address_data.get(), password_data.get(), comment_text.get("1.0", END)
    cursor.execute("UPDATE DATOS_USUARIOS SET NOMBRE_USUARIO=?, APELLIDO=?, DIRECCION=?, PASSWORD=?, COMENTARIOS=? WHERE ID=" + id_data.get(), (datos))
    conexion.commit()
    messagebox.showinfo(
        title="Actualizar registro",
        message="Registro actualizado con éxito en la base de datos.")
    conexion.close()
```

Finalmente, como extra, incluyamos funcionalidad para los dos elementos del menú *Ayuda*:

```python
# Función licencia
def licencia():
    messagebox.showwarning(title="Licencia",
                           message="Producto bajo licencia GNU.")


# Función acerca de...
def acerca_de():
    messagebox.showinfo(title="Acerca de...",
                        message="Aplicación creada por Alexis Sáez.")
```

Ahora, incorporemos dicha funcionalidad en los elementos del menú:

```python
help_menu.add_command(label="Licencia", command=licencia)

help_menu.add_command(label="Acerca de...", command=acerca_de)
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/65/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
