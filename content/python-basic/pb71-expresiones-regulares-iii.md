---
title: 71. Expresiones regulares III
linktitle: 71. RegExp III
toc: true
type: book
date: "2019-06-12T00:00:01+01:00"
lastmod: "2019-06-12T00:00:01+01:00"
draft: false
weight: 71
---

## Vídeo

{{< youtube Q4vXCQd1zwc >}}

## Notas personales

En esta lección, continuaremos el estudio de las expresiones regulares analizando cómo trabajar con **rangos**. Estos nos permiten buscar patrones indicando un rango de números, de caracteres, etc.

Por ejemplo, a partir de una lista de nombres, supongamos que estamos interesados en hallar todos aquellos que tengan letras comprendidas entre la `o` y la `t`:

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("[o-t]", nombre)]
```

```bash
Pedro
María
Rosa
Sandra
```

*Nota*: los rangos son *case sensitive*, esto es, distinguen entre minúsculas y mayúsculas. Por ejemplo, si combinamos el rango anterior con el ancla `^`, la ejecución no arrojará resultado alguno, porque todos los nombres están declarados con su inicial en mayúscula.

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("^[o-t]", nombre)]
```

No obstante, completando el rango solucionamos esta situación:

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("^[o-tO-T]", nombre)]
```

```bash
Pedro
Rosa
Sandra
```

A continuación, estudiemos el uso de rangos cuando se nos presenta una lista de códigos:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4"]

[print(codigo) for codigo in codigos if re.findall("Ma[0-3]", codigo)]
```

```bash
Ma1
Ma2
Ma3
```

Por otro lado, *Python* nos permite la posibilidad de negar rangos, es decir, de obtener aquellos resultados que no se ajustan al patrón de búsqueda especificado. Para ello, antecediendo el rango, utilizamos el carácter `^`:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4"]

[print(codigo) for codigo in codigos if re.findall("Ma[^0-3]", codigo)]
```

```bash
Ma4
```

Acto seguido, agreguemos algunos códigos nuevos y sigamos experimentando el uso de rangos:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4",
           "MaA", "Ma5", "MaB", "MaC"]

[print(codigo) for codigo in codigos if re.findall("Ma[0-3A-B]", codigo)]
```

```bash
Ma1
Ma2
Ma3
MaA
MaB
```

Ahora, insertemos algunos caracteres especiales en mitad de ciertos códigos y veamos entonces cómo lidiar con ellos. Imaginemos que buscamos todos aquellos cuyo tercer carácter sea bien un punto, bien dos puntos:

```python
import re

codigos = ["Ma.1", "Se1", "Ma2", "Ba1", "Ma:3", "Va1", "Va2", "Ma4",
           "MaA", "Ma.5", "MaB", "Ma:C"]

[print(codigo) for codigo in codigos if re.findall("Ma[.:]", codigo)]
```

```bash
Ma.1
Ma:3
Ma.5
Ma:C
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/71/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
