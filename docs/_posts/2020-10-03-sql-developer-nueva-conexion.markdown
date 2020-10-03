---
layout: post
title:  "SQL Developer - Crear nueva conexión"
date:   2020-10-03 19:45:00 +0200
categories: jekyll update
---
# Abrir puertos en el servidor

Lo primero que se debe hacer es abrir los puertos adecuados en el servidor:
* 1158
* 1521

![Máquina limpia](/assets/SQL_developer_nueva_conexion/abrir_puertos.png)

Comprobamos que podemos acceder a la interfaz web del servidor desde el cliente.
* Hay que utilizar el protocolo https.
* El puerto es el 1158
* Hay que aceptar las excepciones de seguridad pertinentes.
* En mi caso, la IP del servidor es 192.168.2.164
* La ruta completa para acceder es: `https://192.168.2.164:1158/em`.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/1.png)

# Conexión básica

Vamos a crear una conexión básica desde SQL Developer

![Máquina limpia](/assets/SQL_developer_nueva_conexion/3.png)
![Máquina limpia](/assets/SQL_developer_nueva_conexion/4.png)

Los parámetros necesarios en este caso son:
* Nombre de la conexión: orcl.
* Usuario: scott.
* Contraseña: tiger.
* Tipo de conexión: Basic.
* Nombre del host: IP de tu servidor.
* Puerto: 1521 (ya está abierto en el servidor).
* Puerto: 1521 (ya está abierto en el servidor).
* SID: orcl

![Máquina limpia](/assets/SQL_developer_nueva_conexion/5.png)

Presionamos `Probar` y nos conectamos.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/6.png)
