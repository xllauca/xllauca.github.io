---
layout: post
title: Review of the Vulnerable Adverse Programming Interface (vAPI)
summary: "En este post compartiré una guía de como explotar las vulnerabilidades de OWASP API Security Top 10 en  (vAPI) utilizando Postman y Burp Suite."
author: xllauca
date: '2022-02-12 10:00:00 +0530'
category: pentesting
thumbnail: /assets/img/posts/vapi_logo.png
keywords: pentesting,owasp,api,vAPI
permalink: /blog/owasp-api-security-vAPI/
usemathjax: true
---
<!-- https://github.com/sujaykundu777/devlopr-jekyll -->
##### **Nota:** Esta información se recopiló de varias fuentes, que serán citadas al final de este post.

Esta entrada del blog es un recorrido de la explotación de las 10 principales vulnerabilidades de la API en vAPI que es Vulnerable Adversely Programmed Interface, una interfaz de PHP auto-alojable que imita OWASP API Top 10 escenarios en los medios de ejercicios. Se puede descargar del siguiente<a target="_blank" href="https://github.com/roottusk/vapi"> link</a> 

## 1. Instalación y preparación del ambiente.
Se puede configurar fácilmente de acuerdo con las instrucciones proporcionadas en README.md.
### 1.1 Requisitos
* Docker
* Postman
* Burpsuite (Community/Pro)

<!-- Sin perder más tiempo, vamos a empezar con las 10 principales vulnerabilidades de la API de OWASP. -->
#### 1.2 Instalación  de Docker.
Para descargar/instalar Docker podemos seguir la [guía](https://docs.docker.com/engine/install/) de la pagina oficial.
#### 1.3 Instalación del laboratorio en (Docker).
Nota: Por defecto los contenedores de este proyecto (vAPI) son persistentes.
```bash
xllauca@archlinux:~$ git clone https://github.com/roottusk/vapi.git
xllauca@archlinux:~$ cd vapi
xllauca@archlinux:~$ docker-compose up -d
```
Verificamos que los contenedores estén levantados
```bash
xllauca@archlinux:~$ docker ps
CONTAINER ID   IMAGE                   COMMAND                  CREATED         STATUS         PORTS                               NAMES
bd2d30185928   vapi_www                "docker-php-entrypoi…"   6 minutes ago   Up 6 minutes   0.0.0.0:80->80/tcp                  vapi_www_1
c46915696082   phpmyadmin/phpmyadmin   "/docker-entrypoint.…"   6 minutes ago   Up 6 minutes   0.0.0.0:8000->80/tcp                vapi_phpmyadmin_1
20821e5dd71e   mysql:8.0               "docker-entrypoint.s…"   6 minutes ago   Up 6 minutes   0.0.0.0:3306->3306/tcp, 33060/tcp   vapi_db_1
```

Ingresamos en el navegador y escribimos lo siguiente:  http://localhost/vapi/

<p align="center">
  <img width="800" src="/assets/img/posts/vapi.png">
</p>

En caso de que paremos/cerremos el servicio de docker y deseemos trabajar con los contenedores que habíamos estado trabajando anteriormente, nos situarnos dentro del directorio "vapi" que clonamos de GitHub  y ejecutamos lo siguiente:
```console
xllauca@archlinux:~$ pwd
/home/xllauca/vapi
xllauca@archlinux:~$ docker-compose up -d
```
Para limpiar/borrar los datos de los contenedores ejecutamos los siguientes comandos, esto cuando los contenedores de proyecto (vAPI) estén levantados.

```console
xllauca@archlinux:~$ docker rm -f $(docker ps -a -q)
xllauca@archlinux:~$ docker volume rm $(docker volume ls -q)
xllauca@archlinux:~$ docker-compose up -d
```

#### 1.4 Instalacion de Burp Suite Professional/Community.
Para descargar/instalar Burp Suite Professional/Community podemos seguir la [guía](https://portswigger.net/burp/documentation/desktop/getting-started) de la pagina oficial.
#### 1.5 Instalacion y Configuración de Postman.
Para descargar/instalar Postman podemos seguir la [guía](https://learning.postman.com/docs/getting-started/installation-and-updates/) de la pagina oficial.

## 4.Explotación

### 4.1. Broken object level authorization
Las APIs suelen acceder a los datos de los usuarios utilizando un identificador en el parámetro (como id=5). Este identificador puede ser predicho y sustituido por un atacante (usuario con intenciones maliciosas) por el identificador de otros usuarios (por ejemplo, id=6). Si la API no realiza las comprobaciones de autorización adecuadas, permitirá al atacante acceder a los datos de otros usuarios. Este ataque también se denomina IDOR (Insecure Direct Object References).
