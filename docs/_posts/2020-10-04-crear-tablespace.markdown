---
layout: post
title:  "Crear Tablespace - Práctica guiada 1"
date:   2020-10-04 18:30:00 +0200
categories: jekyll update
---
# Crear Tablespace 

Desde el Enterprise Manager nos dirigimos a `Servidor -> Almacenamiento -> Tablespaces`.

![Crear tablespace](/assets/crear_tablespace/1.png)

Por defecto nos aparecen los tablespaces existentes. Pulsamos el botón `Crear` para iniciar el proceso de creación de un nuevo tablespace.

![Crear tablespace](/assets/crear_tablespace/2.png)

Escribimos el nombre del nuevo tablespace `TS1`. El resto de opciones las dejamos por defecto. Presionamos el botón `Agregar` para crear un nuevo fichero asociado al tablespace.

![Crear tablespace](/assets/crear_tablespace/3.png)

Marcamos las siguientes opciones:
* Nombre del Archivo: `TS1`.
* Tamaño del Archivo: `1MB`.
* Marcamos la casilla de verificación `Ampliar automáticamente ..."`
* Incremento: `512KB`.
* Tamaño máximo de Archivo: `5MB`.

Presionamos el botón `Continuar`.

![Crear tablespace](/assets/crear_tablespace/4.png)

Presionamos el botón `Aceptar` para que las modificaciones sobre el fichero se hagan efectivas.

![Crear tablespace](/assets/crear_tablespace/5.png)

Obtenemos nuestro nuevo tablespace en la lista de tablespaces.

![Crear tablespace](/assets/crear_tablespace/6.png)

