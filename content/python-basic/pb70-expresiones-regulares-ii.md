---
title: 70. Expresiones regulares II
linktitle: 70. RegExp II
toc: true
type: book
date: "2019-06-11T00:00:01+01:00"
lastmod: "2019-06-11T00:00:01+01:00"
draft: false
weight: 70
---

## Vídeo

{{< youtube V8316ao08tQ >}}

## Notas personales

En esta lección, continuaremos el estudio de las expresiones regulares abordando los denominados **metacaracteres** (o *caracteres comodín*). 

Empecemos con las *anclas*, que dentro de una lista nos van a permitir encontrar coincidencias al principio y al final de cada elemento de esta. Por ejemplo, mediante el ancla `^`, las buscamos al inicio de la cadena de texto:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

for nombre in lista_nombres:
    if re.findall("^Sandra", nombre):
        print(nombre)
```

```bash
Sandra López
```

El último bucle lo podemos compactar utilizando comprensiones de listas de la siguiente forma:

```python
[print(nombre) for nombre in lista_nombres if re.findall("^Sandra", nombre)]
```

Así, podemos extraer de `lista_nombres`, si nos interesa, todos los nombres que comiencen por `S`:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

[print(nombre) for nombre in lista_nombres if re.findall("^S", nombre)]
```

```bash
Sandra López
Santiago Martín
```

¿Y si queremos todos los nombres cuyo apellido sea `Martín`? El ancla `$` es el metacarácter que hemos de emplear:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

[print(nombre) for nombre in lista_nombres if re.findall("Martín$", nombre)]
```

```bash
María Martín
Santiago Martín
```

Veamos otro ejemplo de su uso, trabajando ahora con una lista de dominios, estamos interesados en encontrar aquellos que acaben en `.es`:

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com"]

[print(url) for url in urls if re.findall(".es$", url)]
```

```bash
https://pildorasinformaticas.es
ftp://pildorasinformaticas.es
```

Quizá nos interese hallar qué dominios son de tipo `ftp`:

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com"]

[print(url) for url in urls if re.findall("^ftp", url)]
```

```bash
ftp://pildorasinformaticas.es
ftp://pildorasinformaticas.com
```

Por otro lado, tenemos las **clases de caracteres**, que nos permiten introducir patrones de búsqueda utilizando el operador `[]`. Cambiemos ligeramente los dominios para ver su utilidad (buscando aquellos dominios que contengan el carácter `ñ`):

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com",
        "https://informaticaenespaña.es"]

[print(url) for url in urls if re.findall("[ñ]", url)]
```

```bash
https://informaticaenespaña.es
```

Un ejemplo un tanto más complejo: en una lista de palabras, queremos encontrar si se hallan las palabras `niños` y `niñas`. Como solo se diferencias ambas cadenas en un carácter, podemos escribir:

```python
import re

urls = ["hombres", "mujeres", "mascotas", "niños", "niñas"]

[print(url) for url in urls if re.findall("niñ[oa]s", url)]
```

```bash
niños
niñas
```

*Nota*: al escribir `[oa]` no exigimos que deban estar presentes los dos caracteres y en ese preciso orden. La función `findall()` nos arrojará una coincidencia cuando alguno de los dos esté presente (o ambos, siendo indiferente el orden en el que se encuentren en este último caso).

Esta estrategia es también útil cuando lidiamos con tildes:

```python
import re

urls = ["hombres", "mujeres", "mascotas", "camión", "camion"]

[print(url) for url in urls if re.findall("cami[oó]n", url)]
```

```bash
camión
camion
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/70/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
