---
title: 3. Sintaxis básica
linktitle: 3. Sintaxis básica
toc: false
type: docs
date: "2019-04-28T00:01:01+01:00"
lastmod: "2019-04-28T00:01:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## Vídeo

{{< youtube yppT6GPZMyo >}}

## Notas personales

En el IDLE de *Python*, tecleamos:

```python
>>> print("¡Hola mundo!") # Esto es una instrucción
¡Hola mundo!
```

Usando `;` escribimos varias instrucciones en una misma línea, aunque es desaconsejable por restar legibilidad.

```python
>>> print("¡Hola mundo!"); print("¡Bienvenidos!")
¡Hola mundo!
¡Bienvenidos!
```

Introducimos los **comentarios** con el símbolo `#` para:

- Anotar el código, facilitando futuros mantenimientos.
- Desactivar bloques de instrucciones, para localizar errores cometidos.

```python
>>> # Esto es un comentario
... 
```

Mediante el símbolo `\` dividimos una instrucción en varias líneas, aunque es desaconsejable por restar legibilidad.

```python
>>> mi_nombre = "Mi nombre es Alexis."
>>> mi_nombre
'Mi nombre es Alexis.'
>>> mi_nombre = "Mi nombre es \
... Alexis"
>>> mi_nombre
'Mi nombre es Alexis'
```

Construimos los bloques de código mediante **identación**. El IDLE se encarga automáticamente de procurarla:

```python
>>> a = 0
>>> for i in range(5):
...     a += 1
...     print(a)
... 
1
2
3
4
5
>>> 
```

Durante el curso, usaremos el IDLE de *Sublime Text 3*. Para ello, descargamos el editor a través de [este enlace](https://www.sublimetext.com/3) y lo instalamos. Al iniciarlo:

- Desplegamos el menú `Tools` y seleccionamos `Command Palette...`.
- Escribimos `Install Package Control` y clicamos sobre la opción que aparece.
- Desplegamos, de nuevo, el menú `Tools`, seleccionamos `Command Palette...` y tecleamos `install package`.
- En la siguiente ventana, escribimos `SublimeREPL`, para así tener el interprete de *Python* disponible desde el propio editor.
- Para activarlo, desde el menú `Tools`, seleccionamos ahora `SublimeREPL` y buscamos `Python`. Entre las opciones que aparecen, escogemos `Python`.
