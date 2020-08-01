---
title: 61. Práctica guiada III
linktitle: 61. Práctica III
toc: true
type: book
date: "2019-06-02T00:00:02+01:00"
lastmod: "2019-06-02T00:00:02+01:00"
draft: false
weight: 61
---

## Vídeo

{{< youtube OJzFGgOSpvI >}}

## Notas personales

En esta lección, una vez declarados los campos de introducción de datos en la anterior, nos centraremos en ubicar las etiquetas en la aplicación:

```python
id_label = Label(campos_frame, text="ID:")
id_label.grid(row=0, column=0, sticky="e", padx=2, pady=2)

name_label = Label(campos_frame, text="Nombre:")
name_label.grid(row=1, column=0, sticky="e", padx=2, pady=2)

lastname_label = Label(campos_frame, text="Apellido:")
lastname_label.grid(row=2, column=0, sticky="e", padx=2, pady=2)

address_label = Label(campos_frame, text="Dirección:")
address_label.grid(row=3, column=0, sticky="e", padx=2, pady=2)

password_label = Label(campos_frame, text="Contraseña:")
password_label.grid(row=4, column=0, sticky="e", padx=2, pady=2)

comment_label = Label(campos_frame, text="Comentarios:")
comment_label.grid(row=5, column=0, sticky="ne", padx=2, pady=2)
```

A continuación, ocupémonos de construir un *frame* en la parte inferior del ya disponible y disponer cuatro botones:

```python
# Frame inferior
botones_frame = Frame(root)
botones_frame.pack(expand=True)

crear_button = Button(botones_frame, text="Create")
crear_button.grid(row=0, column=0, sticky="e", padx=2, pady=2)

read_button = Button(botones_frame, text="Read")
read_button.grid(row=0, column=1, sticky="e", padx=2, pady=2)

update_button = Button(botones_frame, text="Update")
update_button.grid(row=0, column=2, sticky="e", padx=2, pady=2)

delete_button = Button(botones_frame, text="Delete")
delete_button.grid(row=0, column=3, sticky="e", padx=2, pady=2)
```

Así, ya únicamente nos resta programar la funcionalidad de la aplicación, tanto para el menú, como para los botones recién creados.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/61/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
