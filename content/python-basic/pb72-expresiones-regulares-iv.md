---
title: 72. Expresiones regulares IV
linktitle: 72. RegExp IV
toc: true
type: book
date: "2019-06-13T00:00:01+01:00"
lastmod: "2019-06-13T00:00:01+01:00"
draft: false
weight: 72
---

## Vídeo

{{< youtube u3WBRgpxQcc >}}

## Notas personales

En esta lección, finaliremos la serie dedicada a expresiones regulares profundizando en el uso de las funciones `match()` y `search()` del módulo `re`. La función `match()` busca coincidencias, con respecto a un patrón determinado, siempre al comienzo del texto.

```python
import re

nombre1 = "Sandra López"
nombre2 = "Antonio Gómez"
nombre3 = "María López"

if re.match("Sandra", nombre1):
    print("Hemos encontrado el nombre.")
else:
    print("No hemos encontrado el nombre.")
```

```bash
Hemos encontrado el nombre.
```

Por otro lado, podemos evitar el comportamiento *case sensitive* de esta función mediante el parámetro `re.IGNORECASE`. Cambiemos `Sandra` por `sandra` y comprobémoslo:

```python
import re

nombre1 = "Sandra López"
nombre2 = "Antonio Gómez"
nombre3 = "María López"

if re.match("sandra", nombre1, re.IGNORECASE):
    print("Hemos encontrado el nombre.")
else:
    print("No hemos encontrado el nombre.")
```

```bash
Hemos encontrado el nombre.
```

Además, tenemos a nuestra disposición el uso de comodines en los patrones de búsqueda. Así, si añadimos dos nuevos nombres ''parecidos'', `Lara` y `Jara`, mediante el carácter `.` (que representa un carácter qualquiera sin determinar) podemos comprobar si ambos pertenecen o no a un listado de nombres:

```python
import re

nombres = ["Sandra López", "Antonio Gómez", "María López",
           "Jara Martín", "Lara Pérez"]

[print(nombre, end="\n") for nombre in nombres if re.match(".ara", nombre)]
```

```bash
Jara Martín
Lara Pérez
```

A continuación, veamos cómo emplear el patrón `\d` para averiguar si una cadena comienza o no por un número:

```python
import re

datos = ["Alexis Sáez", "123456789", "Number1"]

[print(d) for d in datos if re.match("\d", d)]
```

```bash
123456789
```

Ahora, cambiemos de tercio y estudiemos la función `search()` que, a diferencia de `match()` (que se limita a buscar al comienzo de un texto), examina la cadena de texto completa. Retomemos el ejemplo de los nombres y busquemos la aparición de ciertos apellidos concretos:

```python
import re

nombres = ["Sandra López", "Antonio Gómez", "María López",
           "Jara Martín", "Lara Pérez"]

[print(nombre, end="\n") for nombre in nombres if re.search("López", nombre)]
```

```bash
Sandra López
María López
```

No obstante, la principal utilidad de `search()` reside en la búsqueda de determinados patrones dentro de una cadena de caracteres de extensión considerable:

```python
import re

codigos = [
    '''
    Lorem ipsum dolor sit amet, 42consectetur adipiscing elit.
    Maecenas leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue
    sed ex in sollicitudin. Pellentesque luctus justo quis felis
    feugiat, et semper erat laoreet. Curabitur id dui arcu. Curabitur
    purus massa, placerat id pretium ac, ornare eleifend ante.
    ''',
    '''
    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Maecenas 42leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue sed
    ex in sollicitudin. Pellentesque luctus justo quis felis feugiat, et
    semper erat laoreet. Curabitur id dui arcu. Curabitur purus massa,
    placerat id pretium ac, ornare eleifend ante.
    ''',
    '''
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas
    leo erat, varius non laoreet sed, cursus ut tortor. Morbi maximus
    pulvinar ante, ut pulvinar ex malesuada blandit. Maecenas venenatis,
    sapien vitae sodales viverra, ante urna tincidunt tellus, a faucibus
    elit dui congue dui. Quisque congue sed ex in sollicitudin.
    Pellentesque luctus justo quis felis feugiat, et semper erat laoreet.
    Curabitur id dui arcu. Curabitur purus massa, placerat id pretium ac,
    ornare eleifend ante.
    ''']

[print(c, end="\n") for c in codigos if re.search("42", c)]
```

```bash
    Lorem ipsum dolor sit amet, 42consectetur adipiscing elit.
    Maecenas leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue
    sed ex in sollicitudin. Pellentesque luctus justo quis felis
    feugiat, et semper erat laoreet. Curabitur id dui arcu. Curabitur
    purus massa, placerat id pretium ac, ornare eleifend ante.
    

    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Maecenas 42leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue sed
    ex in sollicitudin. Pellentesque luctus justo quis felis feugiat, et
    semper erat laoreet. Curabitur id dui arcu. Curabitur purus massa,
    placerat id pretium ac, ornare eleifend ante.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/72/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
