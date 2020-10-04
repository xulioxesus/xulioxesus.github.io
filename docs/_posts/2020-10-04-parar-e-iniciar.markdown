---
layout: post
title:  "Parar e iniciar la base de datos"
date:   2020-10-04 11:30:00 +0200
categories: jekyll update
---
# Parar la base de datos

Accedemos al Enterprise Manager con `sys` como `SYSDBA`.

![Máquina limpia](/assets/parar_e_iniciar/1.png)

En el apartado General presionamos el botón `Cerrar`.

![Máquina limpia](/assets/parar_e_iniciar/2.png)

Debemos poner nuestras credenciales de Host:
* Usuario: `Administrador`.
* Contraseña: `Hola01`.

Y las credenciales de Base de  Datos:
* Usuario: sys
* Contraseña: system
* Conectar como: SYSDBA

Presionamos el botón `Aceptar`.

![Máquina limpia](/assets/parar_e_iniciar/3.png)

Vamos a `Opciones Avanzadas` para ver los modos en que podemos cerrar la base de datos.

![Máquina limpia](/assets/parar_e_iniciar/4.png)

Matenemos la opción de cierre inmediato y presionamos `Aceptar`.

![Máquina limpia](/assets/parar_e_iniciar/5.png)

Confirmamos el cierre de la base de datos presionando `Sí`.

![Máquina limpia](/assets/parar_e_iniciar/4.png)

Nos informa de que la base de datos se está cerrando. Podemos presionar `Refrescar` para ver si cambia el estado de la base de datos.

![Máquina limpia](/assets/parar_e_iniciar/6.png)

Pasado un tiempo podemos ver que la instancia de la base de datos está cerrada.

# Iniciar la base de datos
 
Presionamos el botón `Iniciar`.

![Máquina limpia](/assets/parar_e_iniciar/7.png)

Tenemos que volver a rellenar las credenciales necesarias para poder iniciar la base de datos.

![Máquina limpia](/assets/parar_e_iniciar/8.png)

Presionamos el botón `Sí` para comenzar el proceso.

![Máquina limpia](/assets/parar_e_iniciar/9.png)

Esperamos a que se complete la operación.

![Máquina limpia](/assets/parar_e_iniciar/10.png)

Nos conectamos a la instancia con las credenciales necesarias.

![Máquina limpia](/assets/parar_e_iniciar/11.png)

Ya tenemos nuestra base de datos en marcha.

![Máquina limpia](/assets/parar_e_iniciar/12.png)
