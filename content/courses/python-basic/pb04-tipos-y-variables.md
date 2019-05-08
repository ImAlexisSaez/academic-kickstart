---
title: 4. Tipos, operadores y variables
linktitle: 4. Tipos y variables
toc: true
type: docs
date: "2019-04-29T00:01:01+01:00"
lastmod: "2019-04-29T00:01:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 4

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

## Vídeo

{{< youtube u4I9PqhqCo8 >}}

## Notas personales

Los **tipos de datos** disponibles en *Python* son:

- Numéricos
    + Enteros (`int`)
    + Coma flotante (`float`)
    + Complejos
- Textos
- Booleanos
    + `True`
    + `False`

Los principales **operadores** en *Python* son:

- Aritméticos: `+`, `-`, `*`, `/`, `%`, `**` y `//`.
- Comparación: `==`, `!=`, `>`, `<`, `>=` y `<=`.
- Lógicos: `AND`, `OR` y `NOT`.
- Asignación: `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=` y `//=`.
- Especiales: `is`, `is not`, `in` y `not in`.

Los operadores aritméticos nos permiten utilizar *Python* a modo de calculadora.

```python
>>> 5 + 6 # Suma
11
>>> 11 - 8 # Resta
3
>>> 2 * 6 # Multiplicación
12
>>> 7 / 2 # División
3.5
>>> 10 % 3 # Módulo
1
>>> 5 ** 2 # Exponenciación
25
>>> 7 // 2 # División entera
3
```

Una **variable** es un espacio en la memoria del ordenador donde se almacenará un valor que podrá cambiar durante la ejecución del programa. Para declararla, utilizamos el patrón `nombre = valor` y su tipo lo establece el contenido, no el contenedor.

*Nota*: en *Python* todo son objetos (variables, números...).

```python
>>> nombre = 5
>>> type(nombre)
<class 'int'>
>>> nombre = "Alexis"
>>> type(nombre)
<class 'str'>
>>> nombre = 5.2
>>> type(nombre)
<class 'float'>
```

Definimos cadenas de texto mediante los símbolos `'`, `"` y `'''`, permitiendo esta última opción saltos de líneas.

```python
>>> mensaje = 'Esto es un mensaje.'
>>> print(mensaje)
Esto es un mensaje.
>>> mensaje = "Esto es un mensaje."
>>> print(mensaje)
Esto es un mensaje.
>>> mensaje = '''Esto es un mensaje
... con tres saltos
... de línea.'''
>>> print(mensaje)
Esto es un mensaje
con tres saltos
de línea.
```

Los operadores de comparación suelen aparecer en bloques condicionales.

```python
>>> numero1 = 5
>>> numero2 = 7
>>> if numero1 > numero2:
...     print("El número 1 es mayor.")
... else:
...     print("El número 2 es mayor.")
... 
El número 2 es mayor.
```

*Nota*: no confundir el operador de asignación `=` con el operador de comparación `==`.

```python
>>> numero1 = 2
>>> numero2 = 3
>>> if numero1 == numero2:
...     print("Los números son iguales.")
... else:
...     print("Los números son diferentes.")
... 
Los números son diferentes.
```
