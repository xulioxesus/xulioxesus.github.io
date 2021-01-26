---
layout: post
title:  "PostgreSQL - Gestión de usuarios y privilegios"
date:   2021-01-26 08:45:00 +0200
categories: jekyll update
---

# Tema 7 - PostgreSQL - Gestión de usuarios y privilegios

## Introducción

Para poder proteger los datos entre los múltiples usuarios que acceden a una Base de Datos, los SGBD utilizan la **autenticación por usuarios**.

En principio cada usuario sólo puede acceder a sus tablas (las crea y es el propietario). Pero también se pueden dar permisos. Así pues, un usuario puede permitir la utilización de una tabla a otro usuario, dándole diferentes grados de acceso: sólo consultar, o insertar, borrar, actualizar, o todos los permisos a la vez, incluso que pueda otorgar permisos a otros usuarios.

Cuando muchos usuarios van a tener permisos similares es conveniente el uso de **grupos de usuarios**. Así por ejemplo, si damos permiso de acceso a una tabla a un grupo de usuarios es como si hubiéramos dado permiso a todos los usuarios de ese grupo facilitando mucho el trabajo del DBA.  

A partir de la versión 8.1 de postgres tanto los usuarios como los grupos se gestionan con el concepto **rol** (**ROLE**). La diferencia entre ellos es que **unos se pueden conectar** (login) y son los roles de entrada (equivalentes a los usuarios) **y otros no se pueden conectar** (nologin) y son los roles de grupo.

![ejemplos](/assets/asgbdTema7/logingroup.png)

En la figura anterior sabemos que se está creando un rol de  usuario porque tiene activada la opción **Can login? a YES**. Si tuviera la opción **Can login? a NO** entonces sería un grupo.

También vemos que no puede crear otros roles ni puede crear BD.

## Gestión de Roles. Utilización como usuarios

Un **rol** es una entidad capaz de recoger permisos y privilegios. Uno de esos permisos es el de conexión (login). Podemos decir que **los roles con el permiso LOGIN son los usuarios**. Además del permiso de conexión también puede tener permisos para crear tablas, vistas, bases de datos, utilizarlos para hacer consultas o actualizaciones, etc 

Los roles no están incluidos en ninguna BD particular, son globales a toda la instalación PostgreSQL. Tanto si pueden hacer login como si no, todos los roles se guardan el la tabla **pg_authid**. También existen unas vistas de esta tabla para falcilitar la consulta y administración:

- `pg_roles`, contiene todos los roles
- `pg_user`, contiene los usuarios, es decir, los roles que pueden hacer login
- `pg_shadow`, con contraseñas
- `pg_group`, los roles que no pueden hacer login

Por tanto, la primera forma de manejar los roles sería manipulando directamente las tablas o las vistas anteriores, aunque esto no es muy recomendable.

Nosotros utilizaremos sentencias SQL para la gestión de los roles y también podremos gestionarlos de forma gráfica.

### psql: CREATE ROLE, ALTER ROLE, DROP ROLE

Estas sentencias permite gestionar usuarios (login) y grupos (nologin). Tienen muchas opciones y puedes consultar su sintaxis en la ayuda de PostgreSQL.

A continuación tienes algunos ejemplos sencillos de uso de estas sentencias:

Crea el usuario (login) geo1 sin contraseña

	CREATE ROLE geo1 LOGIN;

Crea el usuario (login) geo2 con la contraseña prueba

	CREATE ROLE geo2 LOGIN PASSWORD 'prueba2';

Modifica el rol geo1 y le asigna la contraseña prueba

	ALTER ROLE geo1 PASSWORD 'prueba1';

Modifica el rol geo1 y permite un máximo de 3 conexiones simultáneas

	ALTER ROLE geo1 CONNECTION LIMIT 3

Elimina el rol geo

	DROP ROLE geo2;

### Herramientas Gráficas: pgAdmin 

Desde pgadmin la creación, modificación y borrado de roles es muy sencilla. Además al finalizar la creación del rol podemos ver la sentencia SQL que se ha ejecutado para la creación del mismo. A continuación tienes un vídeo donde puedes ver la creación de roles con pgAdmin.

[https://youtu.be/D57uSCKvCro](https://youtu.be/D57uSCKvCro)

Debes conectarte desde el cliente para poder seguir las instrucciones del vídeo.


## Gestión de Roles. Utilización como grupos

Un grupo es un rol que no se puede conectar (nologin). **Los roles con el permiso NOLOGIN son los grupos**. Los grupos tienen una serie de permisos sobre tablas, bases de datos, etc. Un rol de grupo se utiliza para que otros roles (en principio usuarios) puedan heredar sus permisos y así facilitar el trabajo del DBA.

### psql: CREATE ROLE, ALTER ROLE, DROP ROLE

La forma de crear un rol de grupo es la misma que para crear usuarios con la particularidad de que siempre llevarán la opción NOLOGIN

Ejemplos:

Crea el grupo grupo1 sin usuarios

CREATE ROLE grupo1 NOLOGIN

Crea el grupo2 y "mete" a geo1 en él.

CREATE ROLE grupo2 NOLOGIN ROLE geo1;

### Herramientas Gráficas: pgAdmin

Igual que en el apartado anterior. Creamos los grupos con la opción NOLOGIN.

## Permisos

Una vez que sabemos como se crean los usuarios y los grupos vamos a ver que tipo de privilegios y permisos se les puede asignar. Los privilegios y permisos se pueden asignar desde **psql** mediante sentencias SQL o también de una forma mucho más cómoda desde **pgAdmin**. Tanto si lo hacemos por comandos como si lo hacemos de forma gráfica, **al final se creará una sentencia SQL** que al ejecutarse en la BD es la que finalmente otorgará o denegará los permisos.

### psql: GRANT y REVOKE

Para dar permisos se utiliza la sentencia GRANT. Se pueden dar tres tipos de permisos.

#### Otorgar permisos sobre tablas

La sintaxis es:

	GRANT { {SELECT|INSERT|UPDATE|DELETE|REFERENCES|TRIGGER} [,...] | ALL [ PRIVILEGES ] }
	ON [ TABLE ] nombre_tabla [, ...]
	TO { nombre_usuario | GROUP nombre_grupo | PUBLIC } [, ...]
	[ WITH GRANT OPTION ]


Sobre una tabla se pueden dar permisos sólo para selecciona, o insertar, o modificar, o borrar, o crear una clave externa, o crear un trigger, ... o todos ( ALL ).

Se pueden dar permisos a un usuario (o más) o a un grupo, o a PUBLIC , es decir, todos los usuarios.

Si ponemos la opción WITH GRANT OPTION , los usuarios a los que hemos dado permisos podrán otorgar estos permisos a otros usuarios.

Cuando damos permiso a un grupo (al que pertenecen una serie de miembros), éstos heredaran los permisos únicamene si tienen el privilegio I NHERIT.

Ejemplo:

	GRANT SELECT, UPDATE ON comarques, poblacions TO GROUP g_geo;


Para hacer miembro de un rol de grupo a otro rol (normalmente un usuario)

	GRANT rol_grupo TO rol_usuario;

Para dar permisos sobre la BD o sobre objetos de la misma (funciones, esquemas, etc).

Para quitar permisos se utiliza la sentencia **REVOKE**. Se pueden quitar los tres tipos de permisos que hemos visto en el apartado anterior.

La sintaxis es:

	REVOKE [ GRANT OPTION FOR ] { {SELECT|INSERT|UPDATE|DELETE|REFERENCES|TRIGGER} [,...] |
	ALL [ PRIVILEGES ] }
	ON [ TABLE ] nombre_tabla [, ...]
	FROM { nombre_usuario | GROUP nombre_grupo | PUBLIC } [, ...]
	[ CASCADE | RESTRICT ]

Hemos de tener en cuenta que sólo el usuario que ha otorgado los permisos (o el superusuario) puede quitar (revoke) permisos, excepto en el caso CASCADE , que quita los permisos a todos los usuarios que los han ido pasando por tener la opción WITH GRANT OPTION.

Para quitar un usuario de un grupo

	REVOKE rol_grupo FROM rol_usuario

### Herramientas Gráficas: pgAdmin

A continuación tienes un vídeo donde puedes ver como se otorgan y se quitan permisos de forma
gráfica.

[https://youtu.be/dZz1JMuTe0E](https://youtu.be/dZz1JMuTe0E)

Recuerda que esto debes hacerlo desde el cliente.


## Ejercicios

Realiza los siguientes ejercicios y adjunta las capturas de pantalla necesarias.

### Ejercicio 7.7

Crea 3 usuarios (usu1, usu2 y usu3) con las siguientes características:

- La cuenta caduca el 31 de diciembre de este año.
- Límite de conexiones 5
- Puede crear roles
- El resto de parámetros tomará los valores por defecto.

Adjunta la sentencia SQL de creación de uno de los usuarios anteriores.

### Ejercicio 7.8

Crea el grupo1 con las siguientes características:

- Puede crear Bases de Datos
- Puede crear Triggers en la tabla comarques (de la BD geo)
- Puede consultar y añadir datos en la tabla instituts(no modificar ni eliminar).
- Puede otorgar sus permisos de la tabla instituts a otros usuarios.
- Haz que usu1 y usu2 sean miembros de este grupo.

Adjunta la sentencia SQL de creación del grupo y las sentencias de modificación de los usuarios
usu1 y usu2.

### Ejercicio 7.8

Desde psql ejecuta estas dos consultas:

	SELECT * FROM pg_user;
	SELECT * FROM pg_group;

Ahora contensta a esta pregunta. ¿Qué información podemos obtener del campo **grolist**?
