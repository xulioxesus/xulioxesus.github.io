---
layout: post
title:  "PostgreSQL - Ejercicios"
date:   2021-01-26 07:15:00 +0200
categories: jekyll update
---

Realiza los siguientes ejercicios y adjunta las capturas de pantalla necesarias.

## Ejercicio 7.1

Averigua cuántas **poblacions** están situadas a más de 700 metros de altura.

## Ejercicio 7.2

Desde **psql** conecta con el usuario **postgres**. Luego utiliza los comandos

    \c
    
y
    
    \conninfo
    
para cambiar de usuario y conectarte a la base de datos **geo** con el usuario **geo**.

## Ejercicio 7.3

Desde **psql** podemos utilizar el comando **\copy** para guardar el resultado de una consulta en un fichero. Aquí tienes dos ejemplos:

    \copy (select * from comarques) TO /tmp/prueba.txt;
    \copy (select * from comarques) TO /tmp/prueba.csv WITH CSV DELIMITER ';';
    
Guarda el resultado del ejercicio 7.1 en un fichero y comprueba que el fichero se ha generado de forma correcta.

## Ejercicio 7.4

Modifica el fichero **pg_hba.conf** para permitir conectar con el usuario **postgres** desde el equipo cliente a cualquier base de datos.

## Ejercicio 7.5

Modifica el fichero **pg_hba.conf** para permitir conectar con el usuario **geo** desde cualquier IP de la red local a la base de datos **geo**.

## Ejercicio 7.6

Desde el cliente abre una conexión con **geo**. Ahora desde el servidor intenta parar la Base de Datos utilizando el script **pg_ctl** con la opción **s**. Observa el resultado. Si has podido parar la Base de Datos recuerda ponerla en marcha con cualquiera de los métodos vistos en los apuntes.

## Ejercicio 7.7

Crea 3 usuarios (usu1, usu2 y usu3) con las siguientes características:

- La cuenta caduca el 31 de diciembre de este año.
- Límite de conexiones 5
- Puede crear roles
- El resto de parámetros tomará los valores por defecto.

Adjunta la sentencia SQL de creación de uno de los usuarios anteriores.

## Ejercicio 7.8

Crea el grupo1 con las siguientes características:

- Puede crear Bases de Datos
- Puede crear Triggers en la tabla comarques (de la BD geo)
- Puede consultar y añadir datos en la tabla instituts(no modificar ni eliminar).
- Puede otorgar sus permisos de la tabla instituts a otros usuarios.
- Haz que usu1 y usu2 sean miembros de este grupo.

Adjunta la sentencia SQL de creación del grupo y las sentencias de modificación de los usuarios
usu1 y usu2.

## Ejercicio 7.9

Desde psql ejecuta estas dos consultas:

	SELECT * FROM pg_user;

	SELECT * FROM pg_group;

Ahora contensta a esta pregunta. ¿Qué información podemos obtener del campo **grolist**?

### Ejercicio 7.10

Crea un tablespace **nuevo** que se llame **prueba**. Adjunta la sentencia SQL.

- En la ruta /var/lib/postgresql/12/main/data
- Recuerda crear el directorio y cambiar el propietario y el grupo.

### Ejercicio 7.11

Crea una BD que se llame **geo2** igual que la base de datos **geo** y que utilice el tablespace del ejercicio anterior. El propietario tiene que ser **usu2**.

Adjunta la sentencia SQL que se genera.

### Ejercicio 7.12

Haz que el propietario de geo2 sea **usu1**.

Adjunta la sentencia SQL que se genera.

### Ejercicio 7.13

Crea una copia de seguridad de la estructura de la Base de Datos geo.  Utiliza esta copia de seguridad para restaurar o crear una nueva BD que se llame "geo_nueva"

### Ejercicio 7.14

Traspasa los datos de la tabla comarques de la BD geo a la tabla comarques de la BD geo_nueva.
