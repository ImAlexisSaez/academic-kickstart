---
title: "Comandos de Linux #04"
slug: "comandos-de-linux-04"
subtitle: "Examinando la configuración de la terminal"
summary: "Lección 4: Configurando la terminal"

date: 2023-05-24T00:00:01+02:00
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

## Configurando la terminal

En esta lección nos adentraremos en la configuración de la terminal (*Bash* por defecto en la mayoría de las distribuciones de *Linux*). Para ello, hemos de ser conscientes de la existencia de archivos escondidos (*hidden files*) en nuestro sistema operativo, que no se muestran por defecto al listar los contenidos de un directorio mediante el comando `ls`.

Para que dicho listado incluya los mencionados ficheros escondidos, tecleamos

```bash
ls -a
```

Los archivos que aparecen con un punto delante de su nombre son los ficheros escondidos a los que hacíamos referencia antes y que no se listan por defecto al emplear el comando `ls` sin atributos.

*Nota*: podemos encadenar atributos en un comando de una manera bastante cómoda. Por ejemplo, teclear `ls -la` tiene el efecto de añadir los atributos `-l` y `-a` al comando `ls`.

Así pues, si ejecutamos `ls -la` en la carpeta `/home` y observamos el principio de largo listado que aparece, nos daremos cuenta de la existencia de un archivo denominado `.bashrc`. Utilizando

```bash
nano .bashrc
```

podemos acceder a su contenido. Las líneas que comienzan con el símbolo `#` son comentarios. Por otra parte, hemos de llevar cuidado de realizar modificaciones en este archivo y luego sobreescribir, pues las consecuencias pueden distar de ser deseables.

*Nota*: en caso de realizar alguna modificación con catastróficas consecuencias, podemos recuperar una especie de configuración por defecto en `/etc/skel/.bashrc`. La carpeta `skel` `contiene ciertos ficheros de configuración por defecto para asignarlos cuando creamos un nuevo usuario en el sistema. Por otro lado, si en *Google* buscamos *Xubuntu .bashrc*, el primer resultado contiene las líneas de la configuración por defecto de la terminal en *Xubuntu*.

En esta lección únicamente nos vamos a limitar a crear un *alias*. Para ello, añadimos al archivo la línea:

```bash
alias c=clear
```

Guardamos el fichero (con `Ctrl + O`, como indica en el menú inferior) y ahora, en la terminal, no es necesario escribir `clear` para limpiar la pantalla. Basta con teclear `c` y pulsar intro.

*Nota*: en mi caso, ha sido necesario reiniciar la terminal para que el cambio tuviera efecto.

Así, al abrir la terminal, esta accede al archivo de su configuración y tiene en cuenta las instrucciones allí declaradas. Si en un futuro hemos de realizar modificaciones al comportamiento de esta herramienta, seguramente lo hagamos a través de este archivo de configuración.

## El archivo `.bashrc` original

Como temo que fruto de experimentar con este archivo surja alguna consecuencia desastrosa, dejo a continuación una copia del contenido original del mismo.

```bash
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
 # We have color support; assume it's compliant with Ecma-48
 # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
 # a case would tend to support setf rather than setaf.)
 color_prompt=yes
    else
 color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```


## Referencias

- [Linux Commands for Beginners 07 - The Bash Configuration File](https://youtu.be/esNITi0RkPE)
- [The Odin Project](https://www.theodinproject.com/)
