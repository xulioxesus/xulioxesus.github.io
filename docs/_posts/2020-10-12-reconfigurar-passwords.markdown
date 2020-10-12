---
layout: post
title:  "Reconfigurar las contraseñas de los usuarios"
date:   2020-10-12 10:50:00 +0200
categories: jekyll update
---

# Reconfigurar las contraseñas de los usuarios

En el servidor.

Abre un terminal `Simbolo del sistema`. También puedes ejecutar el comando `cmd`.

![Reconfigurar passwords](/assets/reconfigurar_passwords/1.png)

Ejecuta el comando `sqlplus /nolog` para acceder a la base de datos sin utilizar credenciales. Esto lo podemos hacer porque nuestro usuario local es `Administrador`.

![Reconfigurar passwords](/assets/reconfigurar_passwords/2.png)

Ejecuta el comando `connect / as sysdba` para alcanzar los privilegios más altos.

![Reconfigurar passwords](/assets/reconfigurar_passwords/3.png)

Ahora modificamos la contraseña de los usuarios `sys`, `system`, `scott` y `hr`; utilizando los comandos:
* `alter user sys identified by system;`
* `alter user system identified by system;`
* `alter user scott identified by tiger;`
* `alter user hr identified by hr;`

![Reconfigurar passwords](/assets/reconfigurar_passwords/4.png)
![Reconfigurar passwords](/assets/reconfigurar_passwords/5.png)
![Reconfigurar passwords](/assets/reconfigurar_passwords/6.png)
![Reconfigurar passwords](/assets/reconfigurar_passwords/7.png)

Salimos de la conexión utilizando el comando `exit`.

![Reconfigurar passwords](/assets/reconfigurar_passwords/8.png)

Accedemos al Enterprise Manager mediante el navegador.

Nos conectamos utilizando el usuario `sys` con la contraseña `system` y como `sysdba`.

![Reconfigurar passwords](/assets/reconfigurar_passwords/9.png)
![Reconfigurar passwords](/assets/reconfigurar_passwords/10.png)


