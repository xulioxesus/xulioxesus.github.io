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

# Conexión TNS

Abrimos el Asistente de Configuración de Red.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/7.png)

Seleccionamos la tercera opción.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/8.png)

Añadimos un nuevo nombre de servicio en red.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/9.png)

Especificamos el mismo nombre del servicio que tenemos configurado en el servidor: `orcl.w2008`.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/10.png)

Elegimos el tipo de protocolo.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/11.png)

Escribimos la dirección IP de nuestro servidor y dejamos el puerto por defecto.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/12.png)

Realizamos un test para comprobar que la conexión se realiza correctamente.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/13.png)
![Máquina limpia](/assets/SQL_developer_nueva_conexion/14.png)

Le damos el nombre `orcl` al servicio.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/15.png)

Y finalizamos el proceso.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/16.png)
![Máquina limpia](/assets/SQL_developer_nueva_conexion/17.png)

## Crear nueva conexión con TNS

Ahora podemos crear una nueva conexión utilizando la configuración que acabamos de generar.

Abrimos SQL Developer y creamos una nueva conexión.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/18.png)

Ponemos los datos del usuario scott y en Tipo de Conexión elegimos `TNS`. Probamos la conexión y listo.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/19.png)

Ahora tenemos dos conexiones:
* La primera utiliza el tipo de conexión básica.
* La segunda utiliza la conexión de tipo TNS.

![Máquina limpia](/assets/SQL_developer_nueva_conexion/20.png)


