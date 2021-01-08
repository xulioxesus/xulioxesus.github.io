---
layout: post
title:  "Mysql - Instalación en el cliente"
date:   2021-01-08 19:00:00 +0200
categories: jekyll update
---

# Instalación de Mysql Workbench en el cliente

Descarga la ova de Lbuntu Cliente de la carpeta compartida: https://drive.google.com/drive/u/2/folders/1zqUSboN6vQjZA0vaHR0ILJL7OhMv-czd

Importa la máquina en Virtualbox y configura el adaptador de red como `Adaptador puente`.

Inicia la máquina y accede con el usuario `vagrant` contraseña `vagrant`.

Descarga el repositorio de mysql.

`https://dev.mysql.com/downloads/repo/apt/`

Instala el repositorio de mysql mediante la instalación del paquete descargado.

`sudo dpkg -i mysql-apt-config_0.8.16-1_all.deb`

Actualiza los repositorios:

`sudo apt update`

Instala Workbench:

`sudo apt-get install mysql-workbench-community`

Inicia la aplicación `workbench`.

![Workbench](/assets/mysql_instalar_cliente/workbench.png)

Configura una conexión nueva para conectarse al servidor

![Workbench](/assets/mysql_instalar_cliente/workbenchConfig.png)

Verás que la conexión no funciona porque hay que modificar un archivo de configuración en el servidor.

# Configurar mysql para que acepte conexiones diferentes a localhost

En el servidor.

Edita el fichero de configuración `/etc/mysql/mysql.conf.d/mysqld.cnf`

Edita la línea en la que aparece `bind-address` para que quede como en la imagen:

![Workbench](/assets/mysql_instalar_cliente/bind.png)

Reinicia el servicio de mysql

`sudo service mysql restart`

Prueba la conexión desde el cliente para ver si funciona.
