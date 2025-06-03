---
title: Instala escritorios virtuales con KASM Workspaces
date: 2025-05-26 09:00:00 
categories: [SERVIDORES]
tags: [servidores, tools, tecnología, linux]
description: Una herramienta que te permite usar escritorios y aplicaciones directamente desde el navegador, sin instalar nada en tu computadora local.
image: /assets/139/preview1.png
---

**KASM Workspaces** es una herramienta que te permite usar escritorios y aplicaciones directamente desde el navegador, sin instalar nada en tu computadora local. Funciona con contenedores, lo que hace que sea muy ligera, segura y fácil de manejar. Es ideal para pruebas, acceso remoto o simplemente para tener un entorno de trabajo limpio y listo para usar en pocos minutos.

Ahora instalaremos el sistema KASM Workspaces. Para eso necesitamos:

- Instalación limpia (en este caso de Debian 12) Para este lab:
  - 8G en RAM
  - 200 GB de disco
  - 3 vCPU
  - 1 NIC

Hay que descargar el sistema de KASM desde el sitio web:

[https://kasmweb.com/downloads](https://kasmweb.com/downloads)

> **NOTA:** Para instalar KASM necesitamos tener instalado `sudo`.

Buscaremos la versión de Linux y la descargaremos como root dentro de nuestro servidor.  
Una vez descargada, haremos:

```bash
wget https://kasm-staticcontent.s3.amazonaws.com/kasm_release_1.17.0.7f020d.tar.gz
gunzip kasm_release_1.17.0.7f020d.tar.gz
tar -xvf kasm_release_1.17.0.7f020d.tar
```

Ahora desde dentro de KASM, haremos la instalación del servicio.  
Recuerda guardar en un lugar seguro las llaves que generará el sistema.

```bash
# Recuerda tener sudo instalado: aptitude install sudo
chmod 110 install.sh
```

Al terminar, el sistema arrojará las llaves.  
Tendrás que guardarlas ya que esas no se volverán a mostrar.

¡Y listo, ya tienes tu instalación de KASM Workspaces en Linux!

¡Saludos y nos vemos en el Ragnarök! 
