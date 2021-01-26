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