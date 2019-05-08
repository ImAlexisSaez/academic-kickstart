---
title: 16. Bucles III
linktitle: 16. Bucles III
toc: true
type: docs
date: "2019-05-02T00:02:01+01:00"
lastmod: "2019-05-02T00:02:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 16

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 16
---

## Vídeo

{{< youtube KFz-mXB7qVI >}}

## Notas personales

Veamos algunas opciones de la función `print()` a la hora de imprimir el valor de variables durante la ejecución de un bucle:

```python
for i in range(5):
    print(f"valor de la variable {i}")

# valor de la variable 0
# valor de la variable 1
# valor de la variable 2
# valor de la variable 3
# valor de la variable 4
```

La `f` que aparece antes del texto entrecomillado indica el uso de **funciones f**, que permiten interesantes opciones de cara a la impresión de textos en la consola. En esta ocasión, concatena la cadena de caracteres con el valor que toma la variable en cada iteración, indicada por `{i}`.

El tipo `range` admite el uso de argumentos adicionales:

```python
for i in range(5, 10):
    print(f"valor de la variable {i}")

# valor de la variable 5
# valor de la variable 6
# valor de la variable 7
# valor de la variable 8
# valor de la variable 9
```

```python
for i in range(5, 50, 5):
    print(f"valor de la variable {i}")

# valor de la variable 5
# valor de la variable 10
# valor de la variable 15
# valor de la variable 20
# valor de la variable 25
# valor de la variable 30
# valor de la variable 35
# valor de la variable 40
# valor de la variable 45
```

La función `len` también resulta de utilidad a la hora de emplear bucles `for`. Veámosla en acción retomando el ejemplo de la validación de una dirección de correo electrónico visto en la lección anterior:

```python
valido = False

email = input("Introduce tu email: ")

for i in range(len(email)):
    if email[i] == "@":
        valido = True

if valido:
    print("El email es correcto.")
else:
    print("El email no es correcto.")
```

**Ejercicio 1**: crea un programa que muestre los números impares del 1 al 100. Los números deberán aparecer una al lado del otro sin salto de línea.

```python
for i in range(1, 100, 2):
    print(i, end=" ")
```

**Ejercicio 2**: crea un programa que pida por teclado introducir una contraseña. La contraseña no podrá tener menos de 8 caracteres ni espacios en blanco. Si la contraseña es correcta, el programa imprime ''Contraseña OK''. En caso contrario imprime ''Contraseña errónea''.

```python
def evalua_password(password):
    valido = True
    if len(password) < 8 or " " in password:
        valido = False
    return valido

password = input("Introduce contraseña: ")

if evalua_password(password):
    print("Constraseña OK.")
else:
    print("Contraseña errónea.")
```

**Ejercicio 3**: crea un programa que evalúe si una dirección de correo electrónico es válida o no en función de si tiene `@` o `.` Hay que tener en cuenta que la dirección se considera correcta si solo tiene una `@` y si tiene uno o más `.`.

```python
def evalua_mail(mail):
    arroba = False
    punto = False

    if "." in mail:
        punto = True

    contador = 0
    for i in mail:
        if i == "@":
            contador += 1

    if contador == 1:
        arroba = True

    return punto and arroba

mail = input("Introduce dirección de correo electrónico: ")

if evalua_mail(mail):
    print("Dirección de correo electrónico VÁLIDA.")
else:
    print("Dirección de correo electrónico INVÁLIDA.")
```
