---
title: 36. Paquetes distribuibles
linktitle: 36. Paquetes II
toc: true
type: book
date: "2019-05-13T00:00:01+01:00"
lastmod: "2019-05-13T00:00:01+01:00"
draft: false
weight: 36
---

## Vídeo

{{< youtube Zf9sN-w0BVE >}}

## Notas personales

Veamos cómo crear **paquetes distribuibles** para que otras personas puedan utilizar nuestro código fuente. El proceso a seguir se reduce a dos sencillos pasos:

1. Crear el paquete.
2. Instalar el paquete.

En la lección anterior generamos el paquete `calculos` como una carpeta en el interior del directorio del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) donde estamos almacenando todos los archivos de este curso. Desde la raíz del mencionado directorio, utilizamos los módulos contenidos en dicho paquete en, por ejemplo, `paquetes_1.py`.

Ahora bien, si movemos este último archivo a otro directorio, *Python* seguramente no será capaz de encontrar el paquete `calculos`. Para solventar esta situación, hemos de proceder a su instalación.

En primer lugar, creamos un archivo denominado `setup.py` en la raíz del directorio, que contendrá una descripción del paquete que vamos a distribuir (nombre, versión, autor...). En su interior, tecleamos:

```python
from setuptools import setup

setup(name="prac35_calculos",
      version="1.0",
      description="Paquete de cálculos matemáticos",
      author="Alexis Sáez",
      author_email="cucoalexis@hotmail.com",
      url="https://imalexissaez.github.io/",
      packages=["prac35_calculos"])
```

A continuación, abrimos la terminal de *Windows* y nos dirigimos a la carpeta donde hemos almacenado el fichero `setup.py` (la instrucción `cd` es clave en este proceso). Escribimos ahora

```bash
python setup.py sdist
```

Si todo ha ido bien, habrán aparecido dos nuevas carpetas:

- `calculos.egg-info`
- `dist`

En esta última hallamos el archivo comprimido denominado `calculos-1.0.tar.gz`. Este es el fichero que podemos enviar por correo electrónico o subir a alguna plataforma online para distribuirlo a otras personas.

Acto seguido, imaginemos que lo hemos recibido y queremos instalarlo. Para ello, desde la terminal de *Windows* acudimos al directorio donde resida el fichero comprimido y tecleamos:

```bash
pip3 install calculos-1.0.tar.gz
```

Recibiremos rápidamente en la consola el mensaje ''Successfully installed calculos-1.0''.

Ahora, desde cualquier carpeta de nuestro ordenador, podemos emplear el paquete recién instalado escribiendo, por ejemplo:

```python
from calculos.calculos_generales import sumar

sumar(6, 7)
```

```bash
El resultado de la suma es: 13
```

*Nota*: para comprobar que efectivamente el procedimiento se ha llevado a cabo con éxito, he creado una nueva carpeta, `test_paquete`, y allí he ubicado el archivo `paquetes.py`. De no haber instalado correctamente el paquete, *Python* habría sido incapaz de encontrar la función `sumar()` utilizando la instrucción dada arriba.

Finalmente, para desinstalar el paquete, desde la terminal de *Windows* tecleamos:

```bash
pip3 uninstall calculos
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/36/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
