---
title: CrossLinked – Herramienta OSINT para el descubrimiento de emails
date: 2024-06-07 09:00:00 
categories: [HACKING]
tags: [ciberseguridad, tools, hacking]
description: Una de las partes de la metodología OSINT consiste en encontrar información acerca de personas relacionadas con la organización objetivo.
image: /assets/73/preview1.png
---

Una de las partes de la metodología OSINT consiste en encontrar información acerca de personas relacionadas con la organización objetivo. CrossLinked es una herramienta de código abierto que permite la enumeración de nombres válidos de usuarios y de cuentas de correo de una organización.

Esta herramienta utiliza el scraping de los distintos motores de búsqueda de Internet contra la aplicación LinkedIn. Esta técnica proporciona resultados precisos sin necesidad de usar claves de API y sin acceder directamente a LinkedIn.

## ¿Cómo funciona? 

Para poder utilizar esta herramienta en concreto, es necesario tener Python instalado en el sistema, más concretamente en su versión Pyhton3.

Para instalarla solo es necesario clonar el repositorio de la herramienta con la versión más actualizada del código:

![Imagen 00](/assets/73/073-01.png)

De esta manera se creará una carpeta que contendrá los scripts que usa la herramienta y donde se guardarán por defecto los ficheros que se generan con cada uso.

Para poder usar CrossLinked hace falta tener claro que nomenclatura de cuentas usa la organización objetivo. Por ejemplo, para una organización que utiliza para sus correos corporativos la forma “{f}{apellido}@dominio.com” (la primera letra del nombre y el primer o segundo apellido), se introducirá así en la herramienta.

El formato que utiliza CrossLinked puede ser de tres tipos:

![Imagen 01](/assets/73/073-02.png)

Un ejemplo básico de uso podría ser:

![Imagen 02](/assets/73/073-03.png)

Para especificar la nomenclatura se utiliza la opción -f, mientras que para especificar el nombre de los archivos que se generarán se utiliza la opción -o.

Adicionalmente, se recomienda que para obtener mejores resultados se añada inmediatamente seguido de la nomenclatura el nombre de la compañía tal y como aparece en LinkedIn, no el nombre de dominio. De la manera:

![Imagen 03](/assets/73/073-04.png)

Resultados
El resultado de la ejecución sería algo como:

![Imagen 04](/assets/73/073-05.png)

Una vez ejecutado, se generan dos tipos de ficheros:

- Archivo .txt que almacena solo los nombres recopilados.
- Archivo .csv que almacena toda la información obtenida (nombre, puesto de trabajo y Url del usuario en LinkedIn).

Existen varias herramientas OSINT muy conocidas para el reconocimiento de cuentas de correo, como puede ser Hunter.io, Snov.io o Harvester entre otras. Pero esta herramienta se puede utilizar sobre todo al comienzo de la fase de reconocimiento, ya que permite obtener información fiable sin necesidad de API keys o credenciales para su funcionamiento. 

Además, al conectarse a LinkedIn para obtener la información, la convierte en una herramienta muy fiable que obtiene datos actualizados, con un 88 % en tiempo real y un 12 % restante en los últimos 29 días.

Por lo tanto, podemos considerar a CrossLinked como una herramienta muy recomendable para realizar esta parte del reconocimiento.

Credits: Flu-project



