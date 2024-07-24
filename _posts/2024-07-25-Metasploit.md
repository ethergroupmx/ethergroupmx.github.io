---
title: Cheat sheet de Metasploit
date: 2024-07-23 09:00:00 
categories: [HACKING]
tags: [tools, ciberseguridad, hacking]
description: Vulnerando sitios web haciéndo uso de módulos de Metasploit
---

## Vulnerando sitios web haciéndo uso de módulos de Metasploit

###  dir_listing

Este módulo se conectará al servidor web de destino y determinará
si la exploración de directorios está habilitada en él.

### dir_scanner

- Escanea uno o más servidores web en busca de directorios interesantes que puedan explorarse más a fondo.

### enum_wayback

Consultará el sitio archive.org en busca de cualquier URL que se haya archivado para un dominio determinado. Esto puede resultar útil para localizar información valiosa o para encontrar páginas en un sitio que ya no tengan vínculos.

### files_dir

Una lista de palabras como entrada y consulta un host o un rango de hosts para detectar la presencia de archivos interesantes en el objetivo.

### http_login

Es un escáner de inicio de sesión de fuerza bruta que intenta autenticarse en un sistema mediante la autenticación HTTP.

### robots_txt 

Escanea un servidor o un rango de servidores en busca de la presencia y el contenido de un archivo robots.txt . Estos archivos pueden contener con frecuencia información valiosa que los administradores no quieren que los motores de búsqueda descubran.



## Identificando configuraciones HTTPS

### OpenSSL client

Es un cliente que se encuentra dentro de cualquier distribución de GNU/Linux. Podemos probar la información que nos presenta haciéndo uso del comando:

    openssl s_client -connect <host>:<port>

### SSLYZE

Esta herramienta nos permite analizar la configuración de SSL que tiene el servidor. Verifica desde lo más simple hasta la detección de vulnerabilidades. Su forma de uso es:

    sslyze <host>

### SSL and NMAP

Gracias a los potentes scrips de análisis, nmap nos permite analizar y detectar huecos de seguridad. Para poder hacerlo, basta con ejecutar:

    nmap --script ssl-enum-ciphers

Las vulnerabilidades más comunes que puede encontrar son CRIME y POODLE.





