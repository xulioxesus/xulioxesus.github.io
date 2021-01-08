---
layout: post
title:  "Mysql - Ejercicios"
date:   2021-01-08 20:20:00 +0200
categories: jekyll update
---

# Mysql - Ejercicios

# Ejercicio 6.1

Hemos visto dos herramientas gráficas para administrar MySQL: phpmyadmin y Workbench.

Utiliza como cliente el sistema que prefieras. Máquina real o máquina virtual.

- Adjunta capturas de pantalla que confirmen que has podido  conectar con  las dos herramientas desde el cliente.

- Adjunta capturas que confirmen que  NO  puedes conectar con Workbench desde el cliente antes de configurar bind.

- Razona porque desde el cliente SI SE PUEDE conectar con phpmyadmin pero NO SE PUEDE conectar con Workbench.

Todos los ejercicios se pueden hacer desde cualquiera de los 3 entornos que hemos visto:

- Consola de mysql
- phpmyadmin
- workbench

 Elige el que más te guste y adjunta capturas de pantalla necesarias.

# Ejercicio 6.2

Desde la base de datos de geo: ¿Cuántos institutos hay en Borriana?

# Ejercicio 6.3

Añade un campo numérico "habitantes" a la tabla  comarques. Actualiza con elvalor 2000 este campo para todas las comarcas de Alacant, el resto de comarcas tendrán valor 0.

# Ejercicio 6.4 

Crea las bases de datos geo2, geo3 y geo4. De momento estarán vacías.

# EJERCICIO 6.5:

Modifica el puerto de escucha de tu servidor MySQL. Asígnale el puerto 5000.

Cambia el parámetro bind-address a 0.0.0.0 (para permitir conexiones desde otros equipos). Está hecho en las instrucciones actualizadas.

Desde el servidor realiza una conexión MySQL Workbench (Crea una conexión nueva).

Adjunta capturas que demuestren que has realizado las tareas con éxito.

NOTA: Una vez terminado el ejercicio vuelve a dejar el puerto de escucha por defecto.

# Ejercicio 6.6

Recuperar la contraseña de root.

- Edita el fichero de configuracion `mysqld.cnf`.
- Añade la opción `skip-grant-tables`.
- Reinicia el servicio mysql: `sudo service mysql restart`
- Conecta al servidor con el comando `sudo mysql -u root` (no te pedirá contraseña)
- Ejecuta los siguientes comandos:
    - mysql> use mysql;
    - Si tu versión de MySQL es anterior a la 5.7
`mysql> UPDATE user SET password='nuevacontraseña' WHERE user ='root';`
    - Si tu versión de MySQL es 5.7 o posterior
`mysql> UPDATE user SET authentication_string=PASSWORD('nuevacontraseña')WHERE user ='root';`
`mysql> flush privileges;`
`mysql> quit`
- Elimina la opción `skip-grant-tables` del fichero de configuración
- Reinicia en servicio mysql
- Comprueba que necesitas la 'nuevacontraseña' para conectar: `sudo mysql -u root -p`

# Ejercicio 6.7

Crea  todos los  usuarios  "usu4"  que aparecen  en  la tabla del  punto  2.1  del documento.

Comprueba la contraseña que tendrá que utilizar usu4 para conectar con phpmyadmin desde el cliente.

Comprueba la contraseña que tendrá que utilizar  usu4  para conectar con Workbench desde el cliente.

# Ejercicio 6.8

Crea un usuario (desde el entorno de trabajo que prefieras) con las siguientes características:

- Tiene todos los privilegios en la base de datos geo.

- Conecta con este usuario desde la consola mysql y saca un listado con el código y elnombre de todos los institutos de "Alcoi".

# Ejercicio 6.9

 Crea otro usuario con las siguientes características:
 
 - Puede realizar todas las operaciones en la tabla instituts de la BD geo.
 - Puede realizar SELECT en las tablas comarques y poblacions.

# Ejercicio 6.10
 
 Desde la consola haz una copia de seguridad de la base de datos geo y recupéralaen la base de datos geo2.
 
 Adjunta el fichero de importación que has utilizado.
 
# Ejercicio 6.11
 
 ¿Cuál es el comando para exportar todas las bases de datos desde la consola?
 
# Ejercicio 6.12
 
 Desde phpmyadmin haz una copia de seguridad (en 2 pasos) de la bd geo.
 
 - Primer paso: Copia de seguridad de la estructura (definición de tablas).
 - Segundo paso: Copia de seguridad de los datos.Restaura los ficheros enteriores en la base de datos geo3.
 
 Indica exactamente que opciones has utilizado en la exportación y adjunta los ficheros de exportación que has utilizado.
 
 ¿Has tenido que modificar estos ficheros para poder realizar la importación?
 
 En caso afirmativo indica los motivos y adjunta los ficheros de importación.
 
# Ejercicio 6.13
 
 Desde Workbench.
 
 Realiza la exportación de la base de las tablas  comarques  y poblacions de la base de datos geo en un único fichero.
 
 A continuación importa estas tablas en la basede datos geo4.
 
 Indica exactamente que opciones has utilizado y adjunta el fichero de exportación que has generado.
 
 ¿Has tenido que modificar el fichero para poder realizar la importación? En caso afirmativoindica los motivos y adjunta el fichero de importación.