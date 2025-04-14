---
title: Fortinet advierte que atacantes pueden conservar el acceso después de la aplicación de parches
date: 2025-04-13 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, vulnerabilidad, news]
description: Fortinet ha revelado que actores de amenazas han encontrado una manera de mantener el acceso de solo lectura a dispositivos FortiGate vulnerables
image: /assets/124/preview1.png
---

Incluso después de que se parcheara el vector de acceso inicial utilizado para vulnerarlos.

Se cree que los atacantes aprovecharon vulnerabilidades de seguridad conocidas y ahora parcheadas, incluyendo, entre otras, CVE-2022-42475, CVE-2023-27997, y CVE-2024-21762.

*"Un actor de amenazas utilizó una vulnerabilidad conocida para implementar acceso de solo lectura a dispositivos FortiGate vulnerables*, declaró la compañía en un aviso publicado el jueves. *"Esto se logró mediante la creación de un enlace simbólico que conectaba el sistema de archivos del usuario con el sistema de archivos raíz en una carpeta utilizada para servir archivos de idioma para SSL-VPN"*.

Fortinet afirmó que las modificaciones se realizaron en el sistema de archivos del usuario y lograron evadir la detección, lo que provocó que el enlace simbólico (también conocido como symlink) permaneciera incluso después de que se solucionaran las vulnerabilidades de seguridad responsables del acceso inicial.

Esto, a su vez, permitió a los actores de amenazas mantener acceso de solo lectura a los archivos del sistema de archivos del dispositivo, incluidas las configuraciones. **Sin embargo, los clientes que nunca han habilitado SSL-VPN no se ven afectados por el problema.**

No está claro quién está detrás de la actividad, pero Fortinet afirmó que su investigación indicó que no se dirigía a ninguna región o industria específica. También indicó que notificó directamente a los clientes afectados por el problema.

Como medidas adicionales para evitar que estos problemas vuelvan a ocurrir, se han implementado una serie de actualizaciones de software para FortiOS:

- FortiOS 7.4, 7.2, 7.0, 6.4: El enlace simbólico se marcó como malicioso, por lo que el motor antivirus lo eliminó automáticamente.
- FortiOS 7.6.2, 7.4.7, 7.2.11, 7.0.17 y 6.4.16: Se eliminó el enlace simbólico y se modificó la interfaz de usuario de SSL-VPN para evitar la publicación de estos enlaces simbólicos maliciosos.

**Se recomienda a los clientes que actualicen sus instancias a las versiones 7.6.2, 7.4.7, 7.2.11, 7.0.17 o 6.4.16 de FortiOS,** revisen las configuraciones de los dispositivos, las consideren potencialmente comprometidas y realicen las acciones de recuperación adecuadas.

CISA ha emitido un aviso propio, instando a los usuarios a restablecer las credenciales expuestas y a considerar la desactivación de la funcionalidad SSL-VPN hasta que se puedan aplicar los parches. El Equipo de Respuesta a Emergencias Informáticas de Francia (CERT-FR), en un boletín similar, afirmó tener conocimiento de vulnerabilidades que se remontan a principios de 2023.

- 
