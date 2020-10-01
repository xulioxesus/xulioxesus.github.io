---
layout: post
title:  "Instalar Oracle 11g Server en Windows 2008"
date:   2020-10-01 22:46:09 +0200
categories: jekyll update
---
El primer paso es descargar la máquina virtual (OVA) del Drive de la asignatura. Se trata de un Windows Server 2008 de 64 bits.

Después de importarla se debería ver como la siguiente imagen.

![Máquina limpia](/assets/w2008_oracle_instalacion/1.png)

A continuación hay que descargar los dos archivos .zip con el Oracle Database 11g Release 2. Descomprime ambos archivos en el Escritorio para que quede así:

![Máquina limpia](/assets/w2008_oracle_instalacion/2.png)

Lanza el archivo setup.exe para comenzar con la instalación.

![Máquina limpia](/assets/w2008_oracle_instalacion/3.png)

No proporciones ningún dato en esta pantalla e ignora el mensaje de advertencia.

![Máquina limpia](/assets/w2008_oracle_instalacion/4.png)

Selecciona la primera opción para que después de instalar el software de Oracle se configure una base de datos.

![Máquina limpia](/assets/w2008_oracle_instalacion/5.png)

Elige la opción "Clase de Escritorio" puesto que no vamos a trabajar en producción.

![Máquina limpia](/assets/w2008_oracle_instalacion/6.png)

En este punto lo único que vamos a completar es el "Nombre de la Base de Datos Global". Rellénalo con "orcl.w2008". Como contraseña de Administrador y su confirmación pon "system".

![Máquina limpia](/assets/w2008_oracle_instalacion/7.png)

Ignora el mensaje de advertencia y avanza en la instalación.

![Máquina limpia](/assets/w2008_oracle_instalacion/8.png)

Esta pantalla informativa nos sirve para poder revisar que las opciones de instalación son correctas. Presiona "Terminar" para comenzar el proceso de instalación.

![Máquina limpia](/assets/w2008_oracle_instalacion/9.png)

En este punto comienza el proceso de instalación...

![Máquina limpia](/assets/w2008_oracle_instalacion/10.png)

Al terminar, el "Asistente de Configuración de Bases de Datos" nos crea la instancia que habíamos configurado previamente.

![Máquina limpia](/assets/w2008_oracle_instalacion/11.png)

Cuando el asistente termina, presionamos "Gestión de Contraseñas..." para editar y desbloquear unos cuantos usuarios.

![Máquina limpia](/assets/w2008_oracle_instalacion/12.png)

Cambiamos la contraseña del usuario "SYS" y del usuario "SYSTEM". En ambos casos ponemos como contraseña "system".

![Máquina limpia](/assets/w2008_oracle_instalacion/13.png)

Desbloqueamos el usuario "SCOTT" y el usuario "HR".
* SCOTT: contraseña "tiger".
* HR: contraseña "hr".

![Máquina limpia](/assets/w2008_oracle_instalacion/14.png)

Ignoramos la advertencia sobre la seguridad de las contraseñas.

![Máquina limpia](/assets/w2008_oracle_instalacion/15.png)

Presionamos "Aceptar" y habremos finalizado la instalación.

![Máquina limpia](/assets/w2008_oracle_instalacion/16.png)

En esta última pantalla vemos la url que debemos poner en el navegador para poder adminsitrar la base de datos creada (orcl).

La dirección es: https://localhost:1154/em

![Máquina limpia](/assets/w2008_oracle_instalacion/17.png)

Abrimos Firefox y habilitamos TLS 1.0 y 1.1.

![Máquina limpia](/assets/w2008_oracle_instalacion/18.png)

Presionamos "Avanzado..." porque vamos a añadir una excepción de seguridad.

![Máquina limpia](/assets/w2008_oracle_instalacion/19.png)

Presionamos "Aceptar el riesgo y continuar" para poder llegar a la página de "Logon".

![Máquina limpia](/assets/w2008_oracle_instalacion/20.png)

Rellenamos las credenciales del usuario "sys" y nos conectamos como "SYSDBA" para tener más privilegios de administración.

![Máquina limpia](/assets/w2008_oracle_instalacion/21.png)

Una vez autenticados, podremos administrar la base de datos desde esta interfaz web.

![Máquina limpia](/assets/w2008_oracle_instalacion/22.png)

Nos podremos desconectar utilizando el enlace de la parte superior derecha de la página.


![Máquina limpia](/assets/w2008_oracle_instalacion/23.png)
