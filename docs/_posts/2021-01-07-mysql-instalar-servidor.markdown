---
layout: post
title:  "Mysql - Instalación en el servidor"
date:   2021-01-07 21:12:00 +0200
categories: jekyll update
---

# Instalación de LAMP en Ubuntu Server

Descarga la ova de Ubuntu Server de la carpeta compartida: https://drive.google.com/drive/u/2/folders/1zqUSboN6vQjZA0vaHR0ILJL7OhMv-czd

Importa la máquina en Virtualbox y configura el adaptador de red como `Adaptador puente`.

Inicia la máquina y accede con el usuario `vagrant` contraseña `vagrant`.

Actualiza los repositorios:

`sudo apt update`

Instala LAMP:

`sudo apt-get install lamp-server^`

Podemos comprobar que apache está bien instalado visitando la dirección ip de nuestro servidor:

![Apache](/assets/mysql_instalar_servidor/apache.png)

# Instalación de phpmyadmin

Utiliza el comando:

`sudo apt-get install phpmyadmin`

Selecciona apache2 como servidor web utilizando la barra espaciadora.

Selecciona que `Sí`cuando se pregunta si se quiere configurar una base de datos para phpmyadmin.

Elige como contraseña `phpmyadmin`

Podemos acceder a phpmyadmin utilizando la dirección adecuada desde un navegador:

![phpmyadmin](/assets/mysql_instalar_servidor/phpmyadmin.png)

# Permisos del usuario phpmyadmin en mysql

Para dar todos los permisos de administrador al usuario phpmyadmin debemos ejecutar los siguientes comandos.

Nos conectamos a mysql mediante:

`sudo mysql -u root -p`

La contraseña será `vagrant`.

Desde la consola de mysql ejecutamos:

`create user 'phpmyadmin'@'%' identified by 'phpmyadmin';`.

Una vez creado el usuario phpmyadmin que se puede conectar desde cualquier host, le damos permisos sobre todos los objetos de mysql:

`grant all privileges on *.* to 'phpmyadmin'@'%' with grant option;`.

![phpmyadmin](/assets/mysql_instalar_servidor/phpmyadmin2.png)







