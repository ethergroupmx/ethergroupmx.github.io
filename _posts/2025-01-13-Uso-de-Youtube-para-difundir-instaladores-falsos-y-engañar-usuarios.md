---
title: Uso de YouTube para difundir instaladores falsos y engañar usuarios
date: 2025-01-13 09:00:00 
categories: [HACKING]
tags: [hacking, malware]
description: Los atacantes utilizan plataformas como YouTube para difundir instaladores falsos a través de servicios de alojamiento confiables, empleando cifrado para evadir la detección y robar datos confidenciales del navegador.
image: /assets/108/preview1.png
---

### Puntos clave

- Los atacantes utilizan plataformas como YouTube y redes sociales para compartir enlaces de descarga de instaladores falsos para aprovechar la confianza de los usuarios y dirigirlos a sitios maliciosos.
- Los actores de amenazas a menudo utilizan servicios de alojamiento de archivos confiables como Mediafire y Mega.nz para ocultar el origen de su malware y dificultar su detección y eliminación.
- Muchas descargas maliciosas están protegidas con contraseña y codificadas, lo que complica el análisis en entornos de seguridad como los sandboxes y permite que el malware eluda la detección temprana.
- Una vez infectado, el malware recopila datos confidenciales de los navegadores web para robar credenciales. Esta situación muestra los graves riesgos que supone exponer su información personal al descargar software fraudulento sin saberlo.


El aumento de instaladores falsos junto con ladrones de información es una amenaza cada vez mayor para los usuarios que buscan software pirateado. Estos programas maliciosos se disfrazan de aplicaciones legítimas y suelen aparecer en los resultados de búsqueda o en los comentarios de plataformas como GitHub . Desafortunadamente, muchos usuarios caen víctimas de estos trucos. 

Los ladrones de información son un tipo de malware diseñado para robar información confidencial de un sistema infectado. Esto puede incluir credenciales, información financiera, datos personales y otra información confidencial que se puede utilizar para el robo de identidad, fraude u otros fines maliciosos.

## Cómo atraen a sus víctimas

Las víctimas son atraídas por la piratería por personas que se hacen pasar por guías en plataformas populares de intercambio de vídeos como YouTube. Estos actores engañosos se hacen pasar por ofrecer tutoriales legítimos de instalación de software para incitar a los espectadores a hacer clic en enlaces maliciosos en las descripciones o comentarios de los vídeos. Esto pone en peligro los dispositivos de los usuarios y promueve una cultura del robo. He aquí un ejemplo.

![Imagen 01](/assets/108/108-01.png)

*URL alojada en la sección de comentarios de YouTube*

Al acceder al enlace, se abre una publicación separada en YouTube, que revela el enlace de descarga del instalador falso.

![Imagen 02](/assets/108/108-02.png)

*Resultado del enlace de la sección de comentarios*

En el siguiente ejemplo, se realiza una descarga del archivo desde el sitio de alojamiento de archivos de Mediafire:

![Imagen 03](/assets/108/108-03.png)

*Contenido del enlace de Mediafire*

En otro caso, la amenaza se cargó en otro sitio de alojamiento de archivos llamado Mega.nz.

![Imagen 04](/assets/108/108-04.png)

*Muestra la descarga de un instalador falso alojado en mega.nz*


Está claro que la amenaza utiliza servicios de alojamiento de archivos conocidos como otra capa para ocultar aún más su descarga y evadir la detección.

En los casos que analizaremos en este blog, observamos que estas amenazas a menudo se distribuyen como instaladores falsos o software pirateado, que las víctimas encuentran sin darse cuenta mientras los buscan en motores de búsqueda.

En el siguiente ejemplo, palabras clave específicas activan resultados de búsqueda para estas entradas.

![Imagen 05](/assets/108/108-05.png)

*Resultados de la búsqueda de un posible crack/instalador*

El tercer elemento de los resultados de búsqueda (consulte la captura de pantalla anterior) proviene de OpenSea (un mercado de NFT), lo cual es inusual porque alojaba un archivo descargable. La entrada contiene un enlace abreviado que redirecciona al enlace real. Una suposición es que utilizan enlaces abreviados para evitar que los sitios de raspado accedan al enlace de descarga.

![Imagen 06](/assets/108/108-06.png)

*Enlace de descarga acortado de un instalador falso alojado en OpenSea*

El siguiente enlace le solicitará el enlace de descarga real y la contraseña del archivo zip. Proteger los archivos con contraseña puede ayudar a evitar el análisis de sandbox del archivo inicial al llegar, lo que puede ser una victoria rápida para un adversario.

![Imagen 07](/assets/108/108-07.png)

*Siguiente etapa del enlace que muestra el enlace de descarga real*

La cuarta y última entrada en los resultados de búsqueda (consulte la captura de pantalla de los resultados de búsqueda anterior) proviene de SoundCloud, una plataforma para compartir música que aloja el enlace de descarga con una descripción correspondiente. En este caso, el enlace de descarga se acortó mediante Twitter.

![Imagen 08](/assets/108/108-08.png)

*Enlace de descarga de un instalador falso alojado en un sitio para compartir contenido multimedia*

El mismo usuario también publicó entradas adicionales que incluyen medios para descargar un archivo específico.

![Imagen 09](/assets/108/108-09.png)

*Otras entradas en la misma cuenta que muestran posibles instaladores falsos alojados*

Los actores de amenazas continúan usando tácticas de ingeniería social para atacar a sus víctimas y aplican diferentes métodos para evitar las defensas de seguridad, que incluyen: carga lateral de DLL, uso de archivos de instalación grandes, archivos ZIP protegidos con contraseña, inyección de procesos en procesos legítimos, conexiones a sitios web legítimos y creación de copias de archivos y cambio de nombre para que parezcan benignos.

Es importante mantenerse actualizado sobre las amenazas actuales y permanecer alerta con respecto a los sistemas de detección y alerta. La visibilidad es importante porque confiar únicamente en la detección puede provocar que muchas actividades maliciosas pasen desapercibidas.




