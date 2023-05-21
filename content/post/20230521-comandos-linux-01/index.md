---
title: "Comandos de Linux #01"
slug: "comandos-de-linux-01"
subtitle: "Examinando los comandos `cd`, `ll`, `ls` y `pwd`"
summary: "Lección 1: Navegando por el sistema de ficheros."

date: 2023-05-21T00:00:01+02:00
# lastmod: 2023-04-29T00:00:01+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Linux", "Terminal", "The Odin Project"]
categories: ["Programación"]
# projects: []

image:
   focal_point: "Smart"
   caption: "Fotografía de [Gabriel Heinzer](https://unsplash.com/es/@6heinz3r), disponible en [Unsplash](https://unsplash.com/es/fotos/4Mw7nkQDByk)."
---

## Introducción

Esta semana he estado echando un vistazo a la plataforma [The Odin Project](https://www.theodinproject.com/) y más concretamente a su curso de fundamentos, [Foundations](https://www.theodinproject.com/paths/foundations/courses/foundations). Este es el punto de partida común que comparten las dos especializaciones de desarrollo web ofrecidas en este sitio: una basada en *Ruby* y otra en *JavaScript*.

Su primera sección, *Introduction*, es ciertamente interesante, pues trata temas tan variados como el aprendizaje en sí, la gestión de la frustración o la manera de realizar preguntas adecuadamente para obtener ayuda útil. Es un aspecto que la mayoría de los cursos no aborda y los recursos que ofrece esta plataforma son muy interesantes.

Completada dicha sección, la siguiente lleva por título *Prerequisites* y se centra en el funcionamiento básico de los ordenadores y de Internet. Además, es donde empezamos a configurar nuestro entorno de desarrollo para trabajar a lo largo de este curso. Como no podía ser de otra manera, sin ni tan siquiera haber generado un solo fichero, ya comienzan a aparecer los retos (que, por otra parte, bienvenidos sean tras las conclusiones que se extraen de las charlas que figuran en la sección *Introduction*):

- *The Odin Project* no da soporte oficial para *Windows*. ¿Qué sistema operativo utiliza un servidor? Efectivamente, *Windows*. No obstante, la plataforma no nos deja de lado y ofrece alternativas muy bien detalladas para seguir los contenidos de la especialización. A la hora de escribir estas líneas, estoy probando la emulación de una distribución de *Linux*, *Xubuntu*, a través de *Oracle VM VirtualBox* (he tenido hasta que trastear la *BIOS* para permitir la emulación en mi ordenador).
- La propia plataforma nos aconseja no caer en *rabbit holes* que nos distraigan y centrarnos en seguir sus contenidos. La misma plataforma, casi en cada uno de sus apartados, nos enseña docenas de tentadores *rabbit holes* en los que perdernos.

De hecho, esta serie de artículos para el blog son fruto de haber caído en uno de esos *rabbit holes*, pues una vez instalado *Xubuntu* recomiendan aprender los principales comandos que se emplean en su terminal. Para ello enlazan a una lista de reproducción en *YouTube* de 24 vídeos del canal *LearnLinuxTV*.

A continuación, comparto las notas tomadas durante el cuarto vídeo, que corresponde al primero del curso en el cual se empieza a utilizar la terminal.

## Navegando por el sistema de ficheros

Para empezar, el comando 

```bash
ls
```

muestra el contenido del directorio actual de trabajo (`ls` es la abreviatura de *list storage*). Así, al iniciar una nueva terminal, accederíamos con él a los contenidos de la carpeta del usuario.

Si tecleamos 

```bash
ls /
```

accedemos a los contenidos almacenados en la raíz del sistema (`/`). Asimismo, con 

```bash
ls /home
```

se muestran las carpetas habilitadas para los distintos usuarios del sistema. En mi caso, tras la instalación de *Xubuntu* siguiendo las instrucciones de la plataforma, únicamente aparece la carpeta `alexis`.

*Nota*: Por comodidad, para limpiar la terminal y dejar de mostrar la información acumulada hasta el momento, podemos emplear el comando `clear` o, en ocasiones, dependiendo de la distribución de *Linux* que tengamos en nuestro sistema, la combinación de teclas `Ctrl + L`.

Por otra parte, podemos añadir atributos a un comando de la terminal. Por ejemplo, si tecleamos

```bash
ls -l /
```

obtendremos mucha más información que antes de cada una de las carpetas y de los ficheros ubicados en la raíz del sistema (el atributo `-l` indica *long listing*). Además, cada carpeta o fichero aparece en su propia línea. Al inicio de cada una de las mencionadas líneas aparece una extraña secuencia de caracteres que, en su mayor parte, recoge los permisos asociados a la correspondiente carpeta o archivo. De momento, si nos centramos únicamente en el primer carácter:

- `d`: indica directorio o carpeta.
- `-`: indica que es un archivo.
- `l`: indica un enlace a otro archivo.

*Nota*: Una alternativa a la combinación `ls -l` es el comando `ll`.

En la raíz del sistema encontramos algunos directorios de vital importancia. Aunque de momento no entraremos en profundidad en los detalles de cada uno de ellos, para hacernos una idea resulta que:

- `bin`: es el directorio que contiene los programas ejecutables del sistema.
- `boot`: es el directorio que contiene los archivos necesarios para iniciar el sistema operativo.
- `home`: es el directorio asociado a los usuarios del sistema.
- `etc`: es el directorio que contiene los archivos de configuración del sistema.
- `media`: es el directorio donde se montan dispositivos externos (usb, cd-rom...).
- `var`: es el directorio que contiene *logs* del sistema.

*Nota*: la terminal de algunas distribuciones de *Linux* emplea un código de colores para diferenciar los distintos tipos de elementos almacenados. Así, el color azul suele indicar carpetas; el blanco, archivos; y el verde, archivos binarios.

Para cambiar de directorio y navegar por el sistema de archivos utilizamos el comando 

```bash
cd
``` 

que es la abreviatura de *change directory*. Por ejemplo, `cd /` nos lleva a la raíz del sistema y combinando los comandos `cd` y `ls` es como habitualmente nos desplazaremos por el interior del sistema de archivos. En cualquier momento podemos acceder a la ruta del directorio actual de trabajo en el que nos encontramos sin más que teclear

```bash
pwd
```

que es la abreviatura de *print working directory*.

*Nota*: la tilde o virgulilla, `~`, actúa como atajo hacia la carpeta del usuario. Así, con `cd ~` acudimos directamente a nuestra carpeta de usuario.


## Referencias

- [Linux Commands for Beginners 04 - Navigating the Filesystem](https://youtu.be/MnY0K-3_Fjk)
- [The Odin Project](https://www.theodinproject.com/)
