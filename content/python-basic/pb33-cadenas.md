---
title: 33. Métodos de cadenas
linktitle: 33. Cadenas
toc: true
type: book
date: "2019-05-11T00:00:01+01:00"
lastmod: "2019-05-11T00:00:01+01:00"
draft: false
weight: 33
---

## Vídeo

{{< youtube zH0VsRuD2ok >}}

## Notas personales

Examinemos algunos de los métodos disponibles en *Python* a la hora de trabajar con cadenas de texto, que son objetos de tipo `String`. Entre los más habituales encontramos:

- `upper()`
- `lower()`
- `capitalize()`
- `count()`
- `find()`
- `isdigit()`
- `isalum()`
- `isalpha()`
- `split()`
- `strip()`
- `replace()`
- `rfind()`

Para obtener más información sobre su utilización, conviene que visitemos [esta página](http://pyspanishdoc.sourceforge.net/lib/string-methods.html).

Veamos algunos ejemplos sencillos que ilustren el uso de algunos de los anteriores métodos:

```python
nombre_usuario = input("Introduce tu nombre de usuario: ")

print("El nombre es:", nombre_usuario)
print("El nombre es:", nombre_usuario.upper())
print("El nombre es:", nombre_usuario.lower())
print("El nombre es:", nombre_usuario.capitalize())
```

```bash
Introduce tu nombre de usuario: Alexis Sáez
El nombre es: Alexis Sáez
El nombre es: ALEXIS SÁEZ
El nombre es: alexis sáez
El nombre es: Alexis sáez
```

Algunas de estas funciones resultan útiles a la hora de validar los datos que un usuario proporciona a nuestros programas:

```python
edad = input("Introduce la edad: ")

while not edad.isdigit():
    print("Por favor, introduce un valor numérico.")
    edad = input("Introduce la edad: ")

if int(edad) < 18:
    print("No puede pasar.")
else:
    print("Puede pasar.")
```

```bash
Introduce la edad: 8iu9
Por favor, introduce un valor numérico.
Introduce la edad: o9098
Por favor, introduce un valor numérico.
Introduce la edad: 99
Puede pasar.
```

**Ejercicio**: crea un programa que pida introducir una dirección de email por teclado. El programa debe imprimir en consola si la dirección de email es correcta o no en función de si esta tiene el símbolo `@`. Si tiene una `@` la dirección será correcta. Si tiene más de una o ninguna `@` la dirección será errónea. Si la `@` está al comienzo de la dirección de email o al final, la dirección también será errónea

```python
email = input("Introduce email: ")

if email.count("@") == 1 and email.count("@", 1, len(email) - 1) == 1:
    print("La dirección de correo es correcta.")
else:
    print("La dirección de correo es incorrecta.")
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/33/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
