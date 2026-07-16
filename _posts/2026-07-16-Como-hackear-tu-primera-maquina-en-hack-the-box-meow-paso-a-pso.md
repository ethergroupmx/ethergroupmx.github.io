---
title: "Cómo hackear tu primera máquina en Hack The Box: Meow paso a paso"
date: 2026-07-16 09:00:00 
categories: [HACKING]
tags: [hacking, pentesting, ciberseguridad, tools]
description: Hack The Box es una de las plataformas más utilizadas para aprender y practicar habilidades de ciberseguridad en entornos controlados.
image: /assets/276/preview1.png
---

Sus laboratorios permiten poner a prueba conocimientos de reconocimiento, explotación y análisis, siendo una excelente opción tanto para quienes comienzan como para quienes desean perfeccionar sus técnicas.

En este artículo analizaremos Meow, la primera máquina del Starting Point (Tier 0). Se trata de un laboratorio de dificultad Very Easy, ideal para familiarizarse con las bases del hacking ético, desde el reconocimiento del objetivo hasta la obtención de la flag.

Abre tu terminal de Kali Linux y acompáñanos paso a paso en la resolución de este reto.

### Objetivo

En Hack The Box, el objetivo siempre es el mismo: encontrar una vulnerabilidad en el sistema objetivo (la dirección IP que nos da la plataforma) para acceder a él y leer un archivo de texto secreto llamado `flag.txt`.

### Fase 1: Reconocimiento (Escaneo de puertos con Nmap)

No puedes atacar lo que no conoces. Lo primero que hace un hacker ético es escanear la dirección IP de la víctima para ver qué “puertas” (puertos) tiene abiertas hacia internet. Para esto usamos la herramienta reina: Nmap.

Lanzamos el siguiente comando en la terminal:

Bash

    sudo nmap -sV [IP_DE_LA_MAQUINA]

*(Nota: El parámetro `-sV` sirve para que Nmap no solo nos diga qué puertos están abiertos, sino qué versión exacta de software está corriendo en ellos).*

**El resultado:** Nmap nos devuelve que el **puerto 23** está abierto y ejecutando un servicio llamado **Telnet**.

![Imagen 01](/assets/276/276-01.png)

### Fase 2: Análisis de la vulnerabilidad (¿Qué es Telnet?)

Telnet es un protocolo muy antiguo (creado en los años 69) que sirve para conectarse a un ordenador de forma remota a través de la terminal. Tiene un problema gigantesco hoy en día: no cifra las comunicaciones. Todo lo que viaja por Telnet va en texto plano.

Además, en el caso de la máquina Meow, nos enfrentamos a la peor de las vulnerabilidades: una mala configuración de fábrica.

### Fase 3: Explotación (Consiguiendo acceso)

Para intentar conectarnos al servidor de la víctima a través de Telnet, simplemente escribimos en nuestra terminal:

Bash

    telnet [IP_DE_LA_MAQUINA]

El sistema nos responderá saludándonos y pidiéndonos un nombre de usuario (login:).

Aquí viene el truco de la máquina: muchos administradores de sistemas perezosos o despistados dejan las cuentas por defecto activas. Probamos a loguearnos con el usuario administrador supremo de Linux: root.

Plaintext

    meow login: root

¡Y listo! El sistema **no nos pide contraseña**. Nos deja pasar directamente porque la cuenta `root` no tenía clave configurada. Ya estamos dentro del servidor de Meow y tenemos el control total.

![Imagen 02](/assets/276/276-02.png)

### Fase 4: Capturando la Bandera (The Flag)

Ahora que somos dueños del sistema, solo nos queda buscar nuestro trofeo. En los sistemas Linux, el usuario root tiene su propia carpeta personal en la raíz.

Usamos los comandos básicos de navegación:

Bash

    ls          # Para listar los archivos (veremos el archivo flag.txt)
    cat flag.txt # Para leer el contenido del archivo

En la pantalla aparecerá una cadena de caracteres aleatorios (la bandera). La copiamos, la pegamos en la plataforma de Hack The Box y ¡máquina completada!

### Lección aprendida para el mundo real
Meow es un ejemplo perfecto de que muchas veces los hackers no necesitan usar virus complejos para entrar en una empresa; les basta con encontrar un servicio antiguo expuesto a internet con credenciales por defecto o inexistentes.

- **¿Cómo se protege esto?** 1. Desactivando Telnet por completo y usando en su lugar **SSH**, que sí cifra las contraseñas y las conexiones. 2. Asegurándote de que NUNCA haya un usuario (y mucho menos `root`) con una contraseña en blanco.

**Mira el laboratorio en acción**

<iframe width="560" height="315" src="https://www.youtube.com/embed/6N9UYiBmK0w?si=lfSxhOD6rdvHbaYy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Créditos: [https://www.elvigilantedigital.com/](https://www.elvigilantedigital.com/)













