---
layout: post
title:  "PostgreSQL - Ejercicios"
date:   2021-01-26 07:15:00 +0200
categories: jekyll update
---

# Ejercicios

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