---
layout: post
title:  "PostgreSQL - Entornos de trabajo"
date:   2021-01-25 10:22:00 +0200
categories: jekyll update
---

# Tema 7 - PostgreSQL - Entornos de trabajo

Una vez que hemos instalado el servidor, vamos a trabajar con él. Tradicionalmente se han utilizado tres entornos de trabajo con Postgres.

- **psql:** Es la consola de comandos. Un poco "primitiva" pero en ocasiones puede ser la única opción de conectar con el servidor.Como regla general se utilizarán otros entornos de trabajo más "amigables".
- **pgAdmin:** Es el entorno gráfico oficial de Postgres. pgAdmin ha ido evolucionando a la par que ha ido evolucionando Postgres. Es un entorno de trabajo potente, robusto y amigable. Será el entorno de trabajo que utilizaremos mayormente en este tema.
- **phppgAdmin:** Es un entorno web que por lo tanto no necesita ser instalado en el cliente. Nos permite acceder a nuestro servidor Postgres desde cualquier equipo. Es similar al phpmyadmin que vimos en el tema de MySQL pero no funciona "tan fino" como debería y por lo tanto no lo vamos a utilizar. Si quieres probar la instalación aquí tienes el enlace a la página oficial: [https://github.com/phppgadmin/phppgadmin](https://github.com/phppgadmin/phppgadmin)

## psql

Como ya hemos comentado, el cliente más sencillo sin entorno gráfico es **psql**. Este programa nos permite realizar cualquier tipo de operación sobre las bases de datos de postgres. Al tener que trabajar por comandos sólo se recomienda para casos puntuales o para usuarios expertos.

Para iniciar psql desde el servidor escribimos:

    sudo -u postgres psql

Los datos de la conexión que utiliza plsql por defecto son:

- server: localhost
- puerto: 5432
- base de datos: postgres
- usuario: postgres

También podemos conectar con otros usuarios, base de datos, puertos, etc especificando la opción correcta al llamar al programa psql. Aquí tienes algunas opciones:

    -? Ayuda
    -d nombre_bd Nombre de la Base de datos
    -p puerto Puerto de conexión del servidor
    -U nombre Nombre del Usuario
    -W Para que solicite obligatoriamente la contraseña

Una vez dentro del programa (ya hemos conectado con psql) ya podemos escribir los comandos
que necesitemos.

Las sentencias SQL pueden ocupar más de una línea y tienen que terminar con punto y coma.

Con las flechas del cursos se puede recuperar la sentencia anterior (únicamente una línea).

También existen comandos propios de psql que podemos utilizar:

    \e Invoca un editor para editar la última entencia
    \d Listado de las tablas
    \d tabla Descripción de la tabla
    \g [fichero] Ejecuta la sentencia SQL y envía el resultado a un fichero
    \i fichero Ejecuta la sentencias (o sentencias) SQL del fichero
    \w fichero Guarda la sentencia del buffer en un fichero
    \q Salir de psql

A continuación tienes un vídeo donde puedes ver la forma de conectar y algunos ejemplos de
utilización de **psql** : [https://youtu.be/1raopEYJpio](https://youtu.be/1raopEYJpio)

Para seguir los pasos del vídeo en nuestro servidor sin interfaz gráfica debes seguir los siguientes pasos:

Descarga el fichero sql mediante wget.

    wget https://pastebin.com/raw/UexT4J4w -O dades_geo.sql

Inicia sesión en psql

    sudo -u postgres psql

Una vez dentro de psql ejecuta los comandos que se muestran en el vídeo. La única diferencia es que probablemente el fichero se tenga que importar cambiando la ruta donde se ha descargado.

    \i /home/vagrant/dades_geo.sql

## pgAdmin:

pgAdmin es el entorno oficial de trabajo de postgres. Es un entorno gráfico muy intuitivo y que nos permite realizar todas las tareas necesarias en la Base de Datos.

A continuación tienes un vídeo donde puedes ver la forma de conectar y algunos ejemplos de utilización de **pgAdmin** : [https://youtu.be/drp6CmbYpQg](https://youtu.be/drp6CmbYpQg).

Dado que no tenemos pgadmin instalado en el servidor, no podemos seguir el vídeo hasta que podamos conectarnos desde el cliente utilizando pgadmin4.


## Ejercicios

Realiza los siguientes ejercicios y adjunta las capturas de pantalla necesarias.

### Ejercicio 7.1

Averigua cuántas **poblacions** están situadas a más de 700 metros de altura.

### Ejercicio 7.2

Desde **psql** conecta con el usuario **postgres**. Luego utiliza los comandos

    \c
    
y
    
    \conninfo
    
para cambiar de usuario y conectarte a la base de datos **geo** con el usuario **geo**.

### Ejercicio 7.3

Desde **psql** podemos utilizar el comando **\copy** para guardar el resultado de una consulta en un fichero. Aquí tienes dos ejemplos:

    \copy (select * from comarques) TO /tmp/prueba.txt;
    \copy (select * from comarques) TO /tmp/prueba.csv WITH CSV DELIMITER ';';
    
Guarda el resultado del ejercicio 7.1 en un fichero y comprueba que el fichero se ha generado de forma correcta.