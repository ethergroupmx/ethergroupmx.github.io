---
title: "Insecure Boot: Inyección de initramfs desde un shell de depuración de Linux"
date: 2025-07-10 09:00:00 
categories: [LINUX]
tags: [linux, sistema operativo, software libre, vulnerabilidad]
description: Un nuevo informe de seguridad ha sacado a la luz una grave vulnerabilidad que afecta a varias distribuciones Linux y que permite acceder al sistema.
image: /assets/145/preview1.png
---

Un nuevo informe de seguridad ha sacado a la luz una grave vulnerabilidad que afecta a varias distribuciones Linux y que permite acceder al sistema eludiendo la protección del cifrado de disco y que, si bien no se trata de un fallo en el software como tal, sí pone de manifiesto una carencia preocupante en las medidas de "endurecimiento" de algunos sistemas.

El *initramfs (Initial RAM Filesystem)* es un sistema de archivos mínimo cargado en memoria durante el arranque. Su función es preparar el entorno para montar el disco raíz —especialmente cuando está cifrado— y entregar el control al sistema operativo. Sin él, en configuraciones con cifrado, el arranque simplemente no es posible. El archivo initramfs no es estrictamente necesario pero, puede ser necesario para arrancar el sistema en instalaciones sencillas donde, por ejemplo, la partición raíz tiene formato ext4 y reside en un dispositivo de almacenamiento local. El kernel puede leer todos los archivos necesarios y transferirlos a init.

Este tipo de ataque, conocido como *evil maid attack*, requiere acceso físico al equipo, pero demuestra una vez más que cifrar el disco no garantiza una protección total si otros elementos del arranque permanecen vulnerables o sin firmar.

La investigación ha sido llevada a cabo por el equipo de seguridad de ERNW Insinuator y demuestra que es posible obtener acceso a una shell de depuración (debug shell) desde el entorno de arranque (initramfs), simplemente introduciendo varias veces una contraseña de cifrado incorrecta. Tan sencillo como eso. A partir de ahí, el atacante puede modificar el sistema sin necesidad de autenticarse ni de romper el cifrado.

El vector de ataque identificado se basa en el uso del initramfs, un entorno mínimo que se ejecuta al arrancar el sistema para preparar la carga del núcleo principal y que, en los casos en los que la raíz está cifrada, gestiona la introducción de la contraseña de descifrado. Un procedimiento común a la mayoría de distribuciones Linux que se puede utilizar para realizar diferentes operaciones relacionadas con el arranque del sistema.

Al parecer, tras varios intentos fallidos de autenticación algunas distribuciones permiten acceder a una shell de depuración pensada precisamente para facilitar la recuperación del sistema, pero que también puede utilizarse como una puerta de entrada maliciosa. Para conseguirlo bastaría con utilizar una memoria USB con herramientas preparadas para montar el sistema y alterar el initramfs sin necesidad de autenticación.

Con más detalle, los investigadores muestran en su reporte cómo es posible inyectar un script malicioso que se ejecuta automáticamente en el siguiente arranque del dispositivo, una vez introducida la contraseña correcta. Ese script puede realizar cualquier acción con privilegios elevados: desde instalar un keylogger hasta abrir una puerta trasera remota o robar datos.

Lo curioso del problema es que no se trata en un error de software, sino de una omisión de las guías de seguridad más extendidas, las cuales contemplan recomendaciones de endurecimiento del sistema como Secure Boot, cifrado completo del disco y contraseñas en el cargador de arranque, pero olvidan el riesgo que supone dejar accesible la shell del initramfs, que en la mayoría de casos no está firmada ni protegida contra modificaciones, señalan los expertos.

CVE-2016-4484 describe un método similar para obtener acceso a la consola. Modificar el archivo initramfs tampoco es nuevo, como demostraron EvilAbigail en 2015 y de-LUKS en 2018. Este ataque representa un escenario de usuario malicioso en el que el atacante tiene acceso físico al sistema. Muchos ataques similares asumen que el atacante modifica directamente el dispositivo de almacenamiento (es decir, la unidad de estado sólido). En cambio, este ataque sigue una secuencia de arranque normal, activa una consola de depuración y monta una unidad USB preparada que contiene un script que manipula el archivo initramfs en la partición de arranque.

De hecho, desde ERNW advierten de que ni los benchmarks de seguridad del CIS ni los perfiles STIG del NIST mencionan este vector de ataque, así como tampoco lo detectan algunas herramientas de auditoría especializadas.

#### Impacto por distribución (según pruebas reales)

![Imagen 00](/assets/145/145-01.png)

*Parcial: requiere pasos adicionales para obtener herramientas o cargar módulos USB.*

##### Cómo mitigar el riesgo

Mitigar esta vulnerabilidad es posible y relativamente sencillo, aunque requiere atención técnica:

- **Desactivar el acceso a la shell de emergencia:**

  En sistema Ubuntu:

  Añadir panic=0 al parámetro de arranque del kernel.

  En sistemas Red Hat/Fedora:

  Añadir rd.shell=0 rd.emergency=halt para evitar shells automáticas.

- **Cifrar la partición de arranque (boot):**

  Solo algunas distribuciones, como OpenSUSE en configuraciones avanzadas, cifran el /boot. Esto impide modificar initramfs sin la clave.

- **Usar imágenes firmadas (Unified Kernel Images):**

  Un enfoque más robusto consiste en usar imágenes UKI (Unified Kernel Images), donde el kernel, initramfs y el cargador están firmados como una sola unidad.

- **Configurar contraseñas para arrancar el sistema:**

  No solo para modificar entradas del GRUB, sino para arrancar el sistema en sí.

Dicho lo cual, que no cunda el pánico. Este es, como la mayoría, uno de esos problemas que requiere de acceso físico al dispositivo para ser explotado, por lo que sí, es una amenaza real, pero no está dirigida ni puede tener una incidencia reseñable para el común de los usuarios. Porque si hay acceso físico... Ahora bien, el riesgo existe y es responsabilidad de las distribuciones darle solución.


