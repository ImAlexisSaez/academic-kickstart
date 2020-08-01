---
title: 15. Bucles II
linktitle: 15. Bucles II
toc: true
type: book
date: "2019-05-02T00:01:01+01:00"
lastmod: "2019-05-02T00:01:01+01:00"
draft: false
weight: 15
---

## Vídeo

{{< youtube D416qOEDrhI >}}

## Notas personales

Las instrucciones `print()` que aparecen en los bucles de tipo `for` insertan un salto de línea en cada iteración:

```python
for i in ["Píldoras", "Informáticas", 3]:
    print("Hola")

# Hola
# Hola
# Hola
```

Si deseamos que la impresión se produzca en la misma línea, hemos de declarar adecuadamente el argumento `end` de la función `print()`:

```python
for i in ["Píldoras", "Informáticas", 3]:
    print("Hola", end=" ")

# Hola Hola Hola
```

Si el elemento a recorrer es una cadena de texto, el bucle `for` ejecutará tantas iteraciones como letras tenga esta:

```python
for i in "Alexis":
    print(i, end="-")

# A-l-e-x-i-s-
```

Esta característica nos permite, por ejemplo, programar una primera aproximación a un verificador de direcciones de correo electrónico, que nos indique que una es correcta si alberga una arroba en su declaración:

```python
email = False

for i in "direccion@dominio.com":
    if i == "@":
        email = True

if email == True:
    print("El email es correcto.")
else:
    print("El email no es correcto.")

# El email es correcto.
```

El anterior bloque de código se puede simplificar un tanto:

```python
for i in "direccion@dominio.com":
    if i == "@":
        email = True

if email:
    print("El email es correcto.")
else:
    print("El email no es correcto.")

# El email es correcto.
```

Generemos una versión interactiva de este programa:

```python
def evalua_email(direcc):
    email = False

    for i in direcc:
        if i == "@":
            email = True
    if email:
        print("El email es correcto.")
    else:
        print("El email no es correcto.")


direcc = input("Introduce tu dirección de correo electrónico: ")

evalua_email(direcc)
```

Podemos ampliar la función de verificación de correos electrónicos para que compruebe si también hay un carácter `.` en la cadena de texto:

```python
def evalua_email(direcc):
    arroba = False
    punto = False

    for i in direcc:
        if i == "@":
            arroba = True
        if i == ".":
            punto = True
    if arroba and punto:
        print("El email es correcto.")
    else:
        print("El email no es correcto.")


direcc = input("Introduce tu dirección de correo electrónico: ")

evalua_email(direcc)
```

Veamos el uso del tipo `range` en combinación con el bucle `for`:

```python
for i in range(5):
    print(i)

# 0
# 1
# 2
# 3
# 4
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/15/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
