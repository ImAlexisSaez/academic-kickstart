---
title: 18. Bucles V
linktitle: 18. Bucles V
toc: true
type: docs
date: "2019-05-05T00:01:01+01:00"
lastmod: "2019-05-05T00:01:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 18

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 18
---

## Vídeo

{{< youtube c8WCRTU4udo >}}

## Notas personales

En esta lección, abordaremos el uso de las instrucciones:

- `continue`: provoca que el flujo de ejecución de un programa, dentro de un bucle, salte a la siguiente iteración de este.
- `pass`: en cuanto se lee en el interior de un bucle, devuelve `null` (es como si no ejecutara el bucle). Su uso es reducido, salvo en definición de clases o casos muy concretos (dejar bucles vacíos, que sabemos serán precisos, para programar en un futuro próximo).
- `else`: cuando un bucle finaliza todas sus iteraciones, entonces comienza a leer las contenidas en el bloque de código asociado a esta instrucción.

Veamos algunos ejemplos:

```python
for letra in "Python":
    print(f"Viendo la letra {letra}.")

# Viendo la letra P.
# Viendo la letra y.
# Viendo la letra t.
# Viendo la letra h.
# Viendo la letra o.
# Viendo la letra n.
```

```python
for letra in "Python":
    if letra == "h":
        continue
    print(f"Viendo la letra {letra}.")

# Viendo la letra P.
# Viendo la letra y.
# Viendo la letra t.
# Viendo la letra o.
# Viendo la letra n.
```

Elaboremos, a continuación, un programa que cuente el número de caracteres de una cadena de texto, ignorando los espacios en blanco:

```python
nombre = "Píldoras Informáticas"

print(len(nombre))  # 21 (considera espacio en blanco como carácter)

contador = 0

for i in nombre:
    if i == " ":
        continue
    contador += 1

print(contador)  # 20
```

Cuando queremos crear una clase (o función), tan pequeña como sea posible, pero que seguramente en un futuro ampliemos, la instrucción `pass` es de suma utilidad:

```python
class mi_clase:
    pass  # A implementar más tarde
```

Por lo que respecta a la instrucción `else`, veamos un código para comprobar si una dirección de correo electrónico posee o no una arroba:

```python
email = input("Introduce tu email: ")

for i in email:
    if i == "@":
        arroba = True
        break
else:
    arroba = False

print(arroba)
```

Hemos de ser cautos, pues generalmente asociamos la instrucción `else` a estructuras condicionales y no a bucles. Fijarse en la identación del programa es clave.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/18/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
