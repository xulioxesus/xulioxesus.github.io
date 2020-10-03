---
layout: post
title:  "Abrir SQL Developer y corregir error"
date:   2020-10-03 09:30:00 +0200
categories: jekyll update
---
# Abrir SQL Developer

Abrimos SQL Developer desde el menú principal de Windows.

![Máquina limpia](/assets/SQL_developer_y_corregir_error/1.png)

Debemos indicarle la ubicación de "java".

![Máquina limpia](/assets/SQL_developer_y_corregir_error/2.png)

En mi caso la ubicación está en el directorio:  
`C:\app\alumno\product\11.2.0\client_1\jdk\bin`

![Máquina limpia](/assets/SQL_developer_y_corregir_error/3.png)

Podemos marcar las extensiones de ficheros que abrirá por defecto SQL Developer.

![Máquina limpia](/assets/SQL_developer_y_corregir_error/4.png)

En mi caso al abrirlo no hay forma de añadir una nueva conexión.

![Máquina limpia](/assets/SQL_developer_y_corregir_error/5.png)

Además aparece un error..
![Máquina limpia](/assets/SQL_developer_y_corregir_error/error.png)

# Corregir error

Después de investigar un poco [aquí](https://community.oracle.com/tech/developers/discussion/874529/missing-connection-panel-version-1-5-4-5940), damos con la solución.

Lo que tenemos que hacer es editar el fichero de configuración `sqldeveloper.conf` que en mi caso está en la ruta `C:\app\alumno\product\11.2.0\client_1\sqldeveloper\sqldeveloper\bin`. La edición se tiene que hacer como Administrador. Debemos añadir al final del fichero las siguientes líneas.

```
AddVMOption -Duser.country=ES
AddVMOption -Duser.territory=ES
AddVMOption -Duser.language=es
AddVMOption -Duser.timezone=+01:00
```

![Máquina limpia](/assets/SQL_developer_y_corregir_error/7.png)
![Máquina limpia](/assets/SQL_developer_y_corregir_error/8.png)

Vuelve a arrancar `SQL Developer` y listo.
