---
layout: post
title:  "PostgreSQL - Introducción"
date:   2021-01-25 09:22:00 +0200
categories: jekyll update
---

# Tema 7 - PostgreSQL - Introducción

## Objetivos

Una vez que ya sabemos cuál es el trabajo de administrar una gran base de datos como Oracle, vamos a aplicarlo a otro Sistema Gestor de Bases de Datos: **PostgreSQL**.

Hemos elegido PostgreSQL por su potencia y fiabilidad, y por otra característica muy importante: es software libre, así habremos visto a lo largo del curso dos sistemas gestores de bases de
datos muy potentes: **Oracle** (como sistema propietario) y **PostgreSQL** (como software libre).

Los objetivos de este tema básicamente serán:
- Instalar el sistema gestor.
- Arrancar y parar el servidor.
- Crear usuarios que puedan conectar al servidor con diferentes privilegios.
- Gestionar las Bases de Datos.
- Hacer copias de seguridad, y saber recuperar los datos en caso de necesidad.

## Conocimientos previos

En este tema instalaremos PostgreSQL sobre Linux (aunque también se puede hacer sobre Windows u otros sistemas operativos). Se puede instalar sobre cualquier versión de Linux aunque nosotros preferentemente utilizaremos **Ubuntu Server 20.04**, esta máquina virtual se puede descargar desde el drive del módulo.

Las credenciales para acceder a ella son:

    Usuario: vagrant 
    Contraseña: vagrant

## Introducción

Definido de forma rápida, PostgreSQL es un SGBD Relacional que incorpora conceptos de objetos.

Al ser un SGBD relacional, significa que soporta perfectamente la integridad referencial, las restricciones, disparadores o triggers, transacciones, etc. Además ofrece soporte prácticamente total al estandar SQL 92 / SQL 3.

Intenta ser muy flexible permitiendo tipos de datos nuevos creados por el usuario, operadores nuevos, etc.

Y sobretodo, incorpora también conceptos de BD orientadas a objetos. No es un SGBD completamente orientado a objetos, sino que incorpora algunos conceptos como la herencia y las clases.

El origen de PostgreSQL fue un proyecto de la Universidad de Berkeley. El nombre de Postgres se creó en 1986. En 1987 se lanzó la primera versión que fue mejorando hasta llegar a la versión 4.
En 1994 se lanzó un "descendiente" de Postgres de dominio público y código abierto que e denominó **Postgre95**. Este nombre no podía tener futuro y en 1996 se cambió a PostgreSQL. La primera
versión de PostgreSQL fue la 6.0 para continuar con la secuencia del proyecto original de la Universidad.

En Linux, o mejor dicho, en el mundo del software libre, e utilizan principalmente dos SGBD: **MySQL y PostgreSQL**

- En **MySQL** se intenta, por encima de todo, que sea muy rápido y que gaste pocos recursos. Para conseguir esto incluso sacrifica (en algunos casos) cosas impensables como la integridad referencial, transacciones, etc. MySQL se ha impuesto en la creación de páginas web (junto con Apache, PHP y Perl) donde se busca sobretodo la velocidad.
- **PostgreSQL** se puede definir como "más serio", y aunque no llega a ser tan rápido como MySQL puede ser perfectamente un SGBD para sitios o empresas realmente grandes y que necesiten entornos seguros.

Existen muchas comparativas en Internet de SGBDs, y normalmente, la conclusión no es que uno sea mejor que otro, sino que depende de lo que se quiera hacer. ¿Qué necesitamos, velocidad o
potencia?

## Instalación del servidor

PostgreSQL se puede instalar en diversos sistemas operativos (Linux, Windows, OS). En estos apuntes veremos la instalación en Linux, concretamente en la máquina virtual Ubuntu Server 20.04.

En Linux existen varias formas de instalar PostgreSQL, por  paquetes, descargando el código fuente, etc.

Los repositorios por defecto de Ubuntu contienen paquetes Postgres, así que podemos instalarlo fácilmente utilizando `apt`. Si realizamos la instalación de esta forma no tendremos la última versión del sistema gestor.


A continuación tienes los comandos para instalar postgres desde el terminal:

    sudo apt-get update
    sudo apt-get install postgresql postgresql-contrib

El procedimiento de instalación creó un usuario llamado postgres, para poder conectar al servidor debemos cambiar a la cuenta postgres

    sudo -i -u postgres

Ahora ya se puede acceder a la consola de postgres

    psql

También se puede acceder directamente a la consola de postgres con el siguiente comando:

    sudo -u postgres psql

A continuación se muestra un vídeo donde se puede ver una forma sencilla de instalar PostgreSQL. Este vídeo sería útil si en el servidor se tiene interfaz gráfica y se desea realizar la instalación haciendo uso de la misma. NO DEBES SEGUIR EL VÍDEO.

[Instalación de PostgreSQL en Ubuntu Mate 16.04](https://www.youtube.com/watch?v=SWUzgFPR1-E)

Durante el proceso de instalación se ha creado un usuario **postgres** que será el propietario de todo PostgreSQL.

De momento, en la base de datos sólo existe un usuario que también se llama **postgres** que será el DBA.

## Instalación del cliente

El cliente oficial de Postgres es **pgAdmin**. El cliente recomendado es pgadmin4.

### Cliente Windows

A continuación tienes un vídeo donde puedes ver la instalación de pgAdmin en Windows. Sigue este vídeo si deseas utilizar como cliente una máquina real o virtual con Windows.

[Instalar pgAdmin4 en Windows](https://youtu.be/rvQaphk4gCw)

### Cliente Linux

Sigue estos pasos para utilizar como cliente una máquina real o virtual con Linux. Puedes utilizar el Lubuntu 20.04 del tema anterior.

    curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

    sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

    sudo apt install pgadmin4