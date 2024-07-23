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
