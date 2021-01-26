---
layout: post
title:  "PostgreSQL - Copias de seguridad"
date:   2021-01-26 10:25:00 +0200
categories: jekyll update
---

# Tema 7 - PostgreSQL - Copias de seguridad

## Introducción

Esta tarea tan fundamental del DBA es muy sencilla de hacer en Postgres y se puede planificar con un script que se ejecute periódicamente.

Se puede decir que existen tres formas de hacer el backup:

- Con el programa **pg_dump**
- De forma gráfica con **PgAdmin**
- Copiando directamente los ficheros

También existe la posibilidad de realizar un **PITR (Point in Time Recovery)** que consiste en la recuperación del sistema hasta un momento concreto (parecido a la recuperación de Oracle en el modo ARCHIVELOG).  Para poder hacer una recuperación en el tiempo, es necesario que Postgres guarde todos los cambios que se realicen en el sistema en unos ficheros llamados **WAL** (Write Ahead Log - información sobre las transacciones realizadas). Este tipo de recuperación es muy avanzada y no la vamos a ver en
este curso.

## Copia de seguridad con pg_dump

Básicamente consiste en generar un fichero de texto con las consultas SQL necesarias para rehacer la Base de Datos tal y como estaba en el momento de ejecutar el **pg_dump**.  

El programa **pg_dump** se encuentra en la misma ruta ( **/usr/lib/postgresql/12/bin** ) que el resto de programas de postgres y sus opciones principales son las siguientes:

- `-a`, sólo guarda los datos
- `-s`, Sólo guarda la estructura
- `--inserts`, utiliza la sentencia INSERT para los datos (sino utilizará COPY)
- `--column-inserts`, incluye los nombres de las columnas en las sentencias
- `-f fichero`, envía el resultado a un fichero
- `-F formato`, indica el formato de salida ( c custom, d directory, t tar, p plain text)
- `-n nombreBD`, sólo copia la BD especificada
- `-t`, nombreTabla Sólo copia la tabla especificada
- `--help`, muestra la ayuda con todas las opciones (igual que -? )

Además, también tenemos las habituales opciones de conexión: **-h** (host), **-p** (puerto), **-U** usuario y **-W**.

A continuación tienes algunos ejemplos de uso del programa pg_dump:

Se conecta con el usuario geo y hace una copia de seguridad de toda la base de datos geo. La guarda en el fichero geo.sql

	pg_dump -U geo > geo.sql

Esta vez sólo copia la estructura de la base de datos geo.
	pg_dump -s -U geo > geo.sql


Sólo copia los datos utilizando sentencias INSERT

	pg_dump -a --inserts -U geo > geo.sql

Sólo copia la estructura de las tablas comarques e instituts.

	pg_dump -s -t comarques -t instituts -U geo > geo.sql

Si no tenemos suficientes permisos para crear archivos en el directorio donde nos encontramos nos mostrará el error "Permiso denegado".

Una variante de pg_dump es **pd_dumpall** que hace la copia de seguridad de **todas las BD** del sistema. Este programa habrá que ejecutarlo como postgres para tener acceso a todas las BD. También guarda otros objetos que no pertenecen a ninguna BD como son los usuarios y los grupos.El inconveniente es que hay que introducir la contraseña del usuario postgres tantas veces como BD haya en el sistema.

En la imagen anterior puedes ver que el programa **pg_dumpall** pide 4 veces la contraseña porque existen 4 BD en el sistema.

Muestra la ayuda con todas las opciones del programa

	pg_dumpall -?

## Restauración del fichero generado con pg_dump

Si el fichero de salida **no tiene ningún formato** (no hemos utilizado la opción -F), entonces lo ejecutaremos desde **psql** ya que son sentencias SQL. Desde fuera (sin entrar en psql) se puede hacer de dos maneras:

	psql nombre_bd < fichero

o

	psql -f fichero nombre_bd

También se puede hacer desde dentro de psql con la opción \i fichero

Para que este tipo de restauración funcione tanto la Base de Datos como el usuario deben existir.

Combinando el programa pg_dump con psql se puede "pasar" la información de una BD a otra:

	pg_dump bd1 | psql bd

o incluso a otra BD que esté en otro servidor

	pg_dump bd1 | psql -h host bd

Si el fichero de salida **tenía algún formato** (porque hemos utilizado la opción -F), entonces la restauración se realizará con el programa pg_restore.

Las principales opciones de pg_restore son:

- `-a`, sólo restaura los datos
- `-s`, sólo restaura la estructura
- `-c`, borra los objetos antes de rellenarlos
- `-C`, crea la BD antes de restaurarla
- `-d`, nombreBD Se conecta a la BD y restaura directamente en ella
- `-F`, formato Indica el formato del fichero de entrada
- `-t`, nombretabla Restaura la tabla especificada

Además, también tenemos las habituales opciones de conexión: **-h** (host), **-p** (puerto), **-U** usuario y **-W**.  

## Copia de seguridad desde pgAdmin

Hacer copias de seguridad desde pgAdmin es muy sencillo. Realmente estaremos ejecutando **pg_dump** pero desde un entorno gráfico, sin necesidad de conocer la sintaxix de todas las opciones que nos ofrece pg-dump.

A continuación tienes un vídeo donde puedes ver la creación de copias de seguridad y restauración desde pgAdmin.

[https://youtu.be/YKCAuic0mD](https://youtu.be/YKCAuic0mD)

## Copia de seguridad copiando directamente los ficheros

También podemos hacer copias de seguridad "en frío" copiando directamente los ficheros del servidor.

Para ello tenemos que relizar las siguientes tareas:

Parar el servidor (de cualquiera de las formas vistas con anterioridad)

	sudo service postgresql stop

Copiar todos los ficheros con la estructura de directorios

	sudo tar -cf nombre_fichero_tar /var/lib/postgresql/12/main/data

Poner en marcha el servidor

	sudo service postgresql start

La restauración será el proceso inverso:

Parar el servidor

	sudo service postgresql-10 stop

Restaurar los ficheros

	sudo tar -xf nombre_fichero_tar -C /

Poner en marcha el servidor

	sudo service postgresql-10 start


## Ejercicios

Los siguientes ejercicios se pueden realizar de varias formas. Elige una y adjunta las capturas de
pantalla necesarias.

### Ejercicio 7.13

Crea una copia de seguridad de la estructura de la Base de Datos geo.  Utiliza esta copia de seguridad para restaurar o crear una nueva BD que se llame "geo_nueva"

### Ejercicio 7.14

Traspasa los datos de la tabla comarques de la BD geo a la tabla comarques de la BD geo_nueva.
