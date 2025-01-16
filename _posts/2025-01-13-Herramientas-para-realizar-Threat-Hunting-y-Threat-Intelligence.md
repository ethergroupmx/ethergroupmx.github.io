---
title: Herramientas para realizar Threat Hunting y Threat Intelligence
date: 2025-01-13 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [hacking, ciberseguridad, tools]
description: Te compartimos una serie de herramientas Open Source para realizar Threat Intelligence y Threat Hunting.
image: /assets/109/preview1.png
---

### ¿Threat Hunting sinónimo de Threat Intelligence?

Falso. El termino Threat Hunting no es sinónimo de Inteligencia de Amenazas (Cyber Threat Intelligence). Nos parece muy importante volver a destacar las diferencias, ya que muchas veces se continúa utilizando ambos términos como lo mismo.

Por un lado, el proceso de Threat Intelligence implica el análisis y procesamiento de múltiples datos, tanto de las causas, los motivos, los objetivos y los comportamientos de los ataques llevados adelante por ciberdelincuentes. Y por otro lado se encuentra el Threat Hunting, que no responde a los mismos objetivos, por más que la inteligencia de amenazas represente un excelente punto de partida para el proceso de Threat Hunting,

Entendidas las diferencias de ambas disciplinas, avancemos con las herramientas:

## Herramientas para realizar Threat Intelligence

### YETI

YETI es una plataforma que nació con la inquietud de los analistas de CTI, ya que muchas veces los analistas no podían centralizar su información para el análisis. Algunos interrogantes que podían surgir de los analistas son: ¿Dónde observe este indicador? En el caso de un dominio o URL, ¿existe información relacionada con algún ataque o incluso familia de malware que lo utilice? Para resolver cuestiones de esa magnitud YETI permite a los analistas organizar IoC, TTP (Tácticas, Técnicas y Procedimientos) y producir conocimiento sobre amenazas en un único repositorio unificado. YETI enriquece automáticamente los indicadores que el analista coloque (por ejemplo, resolver dominios, geolocalizar direcciones IP).

![Imagen 01](/assets/109/109-01.jpg)

*Visualización de panel central de amenazas en Yeti.*

![Imagen 02](/assets/109/109-02.jpg)

*Ejemplo de tracking de campañas en Yeti.*

Dentro de las funcionalidades que presenta Yeti se destaca el envío de indicadores y el hecho de que a través de diversas fuentes OSINT nos permite visualizar todos los TTP, IoC y códigos maliciosos asociados.

El principal beneficio de esta herramienta es que permite que los analistas se concentren en agregar información de inteligencia en lugar de preocuparse por los formatos de exportación legibles por máquina.

Considerando que la plataforma de YETI posee una API, la cual permite automatizar diferentes consultas a otras plataformas de inteligencia, agrega la funcionalidad de realizar gráficos centralizados sobre amenazas concretas con fuentes externas. Adicionalmente, la inteligencia que se desarrolla dentro de la plataforma le permite a los analistas alimentar de forma sencilla otras tecnologías de bloqueo, como puede ser un servicio SIEM, ya que posee una integración amigable.

### MISP

MISP (Malware Information Sharing Platform) es una de las herramientas fundamentales para compartir Indicadores de Compromiso. Es utilizada por múltiples empresas a lo largo del mundo y de organismos/entidades que colaboran con la producción de inteligencia sobre los ataques, ya que el fin es enriquecer la basa de inteligencia para poder tener más capacidades de protección.

![Imagen 03](/assets/109/109-03.jpg)

*Herramienta MISP Threat Sharing*

La plataforma permite ordenar cómo se comparte la información; es decir que de cierta manera MISP ayuda con la estandarización de los indicadores, lo cual contribuye a que muchas empresas y organizaciones colaboran con la centralización de información.

### Open CTI

El proyecto OpenCTI (Open Cyber Threat Intelligence) es una plataforma destinada a procesar y compartir conocimientos sobre inteligencia de amenazas cibernéticas. En este sentido, la herramienta OpenCTI ayuda a las compañías a organizar los indicadores de inteligencia. Fue creada inicialmente por ANSSI (Agencia Nacional Francesa de Ciberseguridad) junto el CERT-EU (Equipo de Respuesta a Emergencias Informáticas de la Unión Europea).

Los datos son estructurados a partir de la estandarización STIX2 (Structured Threat Information eXpression). Además, unas de las principales ventajas de OpenCTI es que permite integrarse con otras herramientas como MISP, MITRE ATT&CK, entre otros.

![Imagen 04](/assets/109/109-04.jpg)

*Ejemplo de visualización en Open CTI*

### Harpoon

En cuanto a Harpoon, se trata de una herramienta desarrollada en Python para automatizar la inteligencia de amenazas y las tareas de inteligencia de código abierto. La ventaja principal de Harpoon es que permite consultar a distintas plataformas, como Malshare, MISP y Threat Miner.

![Imagen 05](/assets/109/109-05.jpg)

*Harpoon*

## Herramientas para Threat Hunting

### Sysmon

Si bien no es Open Source, System Monitor (Sysmon) es una herramienta gratuita del sistema de Windows que una vez instalada permanece dentro del reinicio del sistema, ya que de esta manera puede monitorear y registrar toda actividad perteneciente a los registros de Windows.

Sysmon brinda una gran variedad de información de actividades, como son las conexiones de red, las creaciones de procesos, cambios en las marcas de tiempo de creación de archivos, acceso a la memoria de procesos o incluso la creación de hilos remotos. Además, tiene la capacidad de identificar actividades sospechosas o maliciosas con el fin de interpretar las intrusiones que operan en la red.

### APT-Hunter

APT-Hunter es una herramienta de búsqueda de amenazas para registros de eventos de Windows, la cual es utilizada para detectar ya sea comportamientos de APT o actividades sospechosas ocultas en los registros de eventos Windows. Es utilizada principalmente por “Purple teams” y está escrita en el lenguaje Python.

Esta herramienta contiene una lista ya precargada, la cual permite detectar los IoC dentro del framework de MITRE ATT&CK.

Para realizar la recopilación de los registros de Windows presenta una interfaz sencilla, ofreciendo dos posibilidades de formato de registros. Uno de ellos es EVTX (Windows 7 Event Log Format) y el otro en formato CSV.

Luego de ejecutar la herramienta, APT-Hunter nos brinda dos archivos de salida:

- Un archivo con extensión .xlsx: incluye todos los eventos detectados como sospechosos o maliciosos por la herramienta.
- Un archivo con extensión .csv: en el cual brinda información de las actividades cronológicamente. Este archivo se puede cargar luego en una línea de tiempo para observar la cronología del ataque.

### DeepBlueCLI

Para la detección de amenazas o Threat Hunting es necesario contar con una base de datos que nos indique cuales son las actividades maliciosas o sospechosas. Esta base de conocimientos puede ser DeepBlueCLI, que consiste en un módulo de PowerShell para la búsqueda de amenazas a través de registros de eventos de Windows. Esta herramienta se encuentra dentro del repositorio de SANS-blue-team.


