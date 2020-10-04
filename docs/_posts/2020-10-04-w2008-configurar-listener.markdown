---
layout: post
title:  "Configurar el listener en el servidor"
date:   2020-10-04 11:30:00 +0200
categories: jekyll update
---
# Configurar el listener en el servidor

Para poder conectarnos desde el cliente, debemos configurar el listener para que acepte peticiones que vayan dirigidas a la propia IP del servidor.

Hacemos esto conectándonos al Enterprise Manager con el usuario SYS. Desde la pantalla principal entramos en `LISTENER_localhost`.

![Máquina limpia](/assets/w2008_configurar_listener/106.png)

Editamos el listener.

![Máquina limpia](/assets/w2008_configurar_listener/107.png)

Agregamos una nueva dirección.

![Máquina limpia](/assets/w2008_configurar_listener/108.png)

Ponemos la IP del servidor y mantenemos el puerto por defecto.

![Máquina limpia](/assets/w2008_configurar_listener/109.png)

Ahora tenemos dos direcciones en el listener.

![Máquina limpia](/assets/w2008_configurar_listener/110.png)

Confirmamos los cambios y listo.

![Máquina limpia](/assets/w2008_configurar_listener/111.png)

