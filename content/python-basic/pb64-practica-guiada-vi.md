---
title: 64. Práctica guiada VI
linktitle: 64. Práctica VI
toc: true
type: book
date: "2019-06-05T00:00:01+01:00"
lastmod: "2019-06-05T00:00:01+01:00"
draft: false
weight: 64
---

## Vídeo

{{< youtube nx3OE31y0IY >}}

## Notas personales

En esta lección, abordaremos la implementación de las operaciones de tipo *Read* y *Update*. El criterio para posibilitar la lectura de registros será que el usuario introduzca en el formulario la *ID* de la cual desea consultar la información pertinente.

En primer lugar, implementemos la función de lectura, apoyándonos en cómo procedimos en anteriores lecciones:

```python
# Función que lee registros de la BBDD
def crud_read():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("SELECT * FROM DATOS_USUARIOS WHERE ID=" + id_data.get())
    usuario = cursor.fetchall()
    for u in usuario:
        id_data.set(u[0])
        name_data.set(u[1])
        lastname_data.set(u[2])
        address_data.set(u[3])
        password_data.set(u[4])
        comment_text.insert(1.0, u[5])
    conexion.commit()
    conexion.close()
```

Luego, añadimos la funcionalidad, tanto al elemento del menú correspondiente, como al botón asociado:

```python
crud_menu.add_command(label="Leer", command=crud_read)

read_button = Button(botones_frame, text="Read", command=crud_read)
```

*Nota*: así programa la funcionalidad, la aplicación no responde cuando se inserta un *ID* que no figura en la base de datos. Habría de mostrar un mensaje de advertencia mediante la clase `messagebox`.

Acto seguido, ocupémonos de la función de tipo *Update*, que será muy similar a la programada para *Create*:

```python
# Función que actualiza registros de la BBDD
def crud_update():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("UPDATE DATOS_USUARIOS SET NOMBRE_USUARIO='" +
                   name_data.get() + "', APELLIDO='" + lastname_data.get() +
                   "', DIRECCION='" + address_data.get() + "', PASSWORD='" +
                   password_data.get() + "', COMENTARIOS='" +
                   comment_text.get("1.0", END) + "'")
    conexion.commit()
    messagebox.showinfo(
        title="Actualizar registro",
        message="Registro actualizado con éxito en la base de datos.")
    conexion.close()
```

Después, añadimos el comportamiento, tanto al elemento del menú asociado, como al botón correspondiente:

```python
crud_menu.add_command(label="Actualizar", command=crud_update)

update_button = Button(botones_frame, text="Update", command=crud_update)
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/64/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
