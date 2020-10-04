---
layout: post
title:  "Tema 1 - Ejercicios"
date:   2020-10-04 11:30:00 +0200
categories: jekyll update
---

# Exercici 1.1

Segueix aquestes instruccions:

* Has de tindre una connexió al servidor des del SQL Developer (que està en la màquina real), concretament a l'usuari SCOTT.
* Des de la consola de l'Enterprise Manager finalitza aquesta sessió de Scott des del SQL Developer de la màquina real de forma immediata.
* Intenta fer alguna operació des del SQL Developer , per exemple SELECT * FROM DEPT;

Donarà un error. Escriu exactament l'error que dóna (el trobaràs en la barra d'estat del SQL Developer, en la part inferior).

Adjunta també una imatge on es puga veure aquest error.

La contestació i la imatge poden anar en un document de text Word o OpenOffice (o LibreOffice).

# Exercici 1.2

Segueix aquestes instruccions:

No has de tindre una connexió des del SQL Developer. Si tens el SQL Developer en marxa, tanca'l.

Des de la consola de l'Enterprise Manager posa la instància en mode MOUNT. Per a fer això primer ha de parar la instància, i per tant et preguntarà pel mètode: has de triar Inmediato.

Quan estigues segur/a que la instància està en mode MOUNT, intenta connectar des de SQL Developer (a SCOTT). Si és precís, intenta-ho més d'una vegada. Com que la instància no està oberta, t'eixirà un error. Escriu exactament l'error que dóna.

Adjunta també una imatge on es puga veure aquest error.

La contestació i la imatge poden anar en un document de text Word o OpenOffice (o LibreOffice).

Posteriorment posa en mode OPEN (Abierta) la instància, per a poder continuar treballant.

# Exercici 1.3

Apunta el nom i la grandària exacta del fitxer associat al Tablespace TS1 després de fer la Pràctica guiada 1. Ho pots consultar per mig de l'explorador de Windows.

Adjunta també una imatge on es puga veure el fitxer anterior des de l'explorador d'arxius de Windows.

La contestació i la imatge poden anar en un document de text Word o OpenOffice (o LibreOffice).

# Exercici 1.4

Des de la consola de l'Enterprise Manager crea una vista en l'esquema de SCOTT anomenada DEPARTAMENTS que continga el nom dels departaments juntament amb el número d'empleats de cada departament (fins i tot d'aqueslls que no tenen empleats).

Pots practicar primer la sentència SQL des del SQL Developer, però la creació de la vista l'has de fer des de la consola de l'Enterprise Manager en la màquina virtual on està el servidor Oracle. Pot ser especialment útil l'opció Sustituir si existe, per si no t'ha eixit com volies a la primera.

La solució hauria de ser aquesta (observeu que el camp amb el número d'empleats té l'àlias NUM_EMP). 

![img](/assets/tema1_ejercicios/1.png)

Adjunta també una imatge on es puga veure la creació (amb la sentència SQL) de la vista, és a dir, immediatament abans de crear-la.

Pots pujar la imatge solta o en un document de text Word o OpenOffice (o LibreOffice), i posar els comentaris que estimes oportuns.

# Exercici 1.5

Investiga els següents comandaments que es fan servir des de la consola o terminal:
*tnsping
*lsnrctl

Fes-ne un resum de la seua utilitat i adjunta el resultat que mostren quan els executes en les teues màquines.
