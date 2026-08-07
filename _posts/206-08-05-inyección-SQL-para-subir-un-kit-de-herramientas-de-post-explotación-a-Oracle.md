---
title: "khunt: inyección SQL para subir un kit de herramientas de post-explotación a Oracle"
date: 2026-08-05 09:00:00
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, vulnerabilidad, seguridad informática]
description: Investigadores descubrieron khunt, un kit de post-explotación que aprovecha una vulnerabilidad de inyección SQL para ejecutar código en bases de datos Oracle sin escribir archivos en el disco.
image: /assets/282/preview1.png
---

Los atacantes accedieron a la base de datos Oracle de una organización mediante una vulnerabilidad de inyección SQL en una aplicación web pública. Posteriormente, instalaron un kit de herramientas de post-explotación sin escribir ningún ejecutable en el disco. Introdujeron código fuente Java en la base de datos, permitieron que Oracle lo compilara en objetos de esquema almacenados y ejecutaron comandos desde el motor de la base de datos.

Huntress, que rastrea el kit de herramientas como khunt, investigó tras las detecciones de robo de credenciales el 27 de julio de 2026 y rastreó la cadena hasta la ejecución de código a nivel de sistema en el servidor Windows subyacente.

![Imagen 01](/assets/282/282-01.png)

**Tras realizar una inyección SQL, el atacante logró subir a la base de datos un kit de herramientas de post-explotación llamado khunt.** Esta técnica ya se había comentado y descrito a lo largo de los años, incluso mediante una técnica denominada oraexec; sin embargo, su uso en la práctica rara vez se ha documentado.

La vulnerabilidad residía en la aplicación, donde un campo de búsqueda con autocompletado enviaba datos no validados a la base de datos a través de una conexión JDBC (Java Database Connectivity). La cuenta detrás de esa conexión tenía privilegios suficientes para crear objetos Java.

Ningún parche de Oracle corrige la vulnerabilidad de la aplicación ni los privilegios de la cuenta que la sustentaba. Encontrar el kit de herramientas requiere una búsqueda exhaustiva: se deben buscar en la instalación de Oracle nombres de objetos que comiencen con Khunt y en los registros SQL el término KHUNT%.

Una clase Java compilada en un objeto de esquema de base de datos no es un proceso, un binario ni un archivo en el sistema de archivos, y los productos de detección y respuesta de endpoints generalmente no inspeccionan los detalles internos de Oracle. Según Huntress, la base de datos deja de ser un objeto que los atacantes consultan y se convierte en una cabeza de playa desde la que atacan.

Oracle incluye una máquina virtual Java integrada, y la instrucción CREATE JAVA SOURCE permite al usuario proporcionarle código Java que la base de datos compila y almacena como un objeto de esquema. En el esquema del usuario, la documentación de Oracle establece que el requisito es un único privilegio del sistema: CREATE PROCEDURE. La creación de un proceso del sistema operativo a partir de ese código se realiza a través de Runtime.exec, que necesita su propio permiso de ejecución de archivos, y Oracle afirma que estos permisos solo los otorgan los administradores con privilegios.

Huntress no especifica qué permiso otorga la cuenta comprometida, ni si los atacantes tuvieron que añadir alguno. La cadena de ataques tuvo éxito, por lo que contaba con los permisos necesarios para ambos casos.

Esta técnica tiene al menos dos décadas de antigüedad. El archivo raptor_oraexec.sql de Marco Ivaldi, de 2006, crea un objeto fuente de Oracle con métodos de ejecución de comandos y lectura de archivos, y luego los publica en SQL mediante adaptadores PL/SQL. Los objetos khunt utilizan la misma arquitectura básica. "El uso de esta técnica en la práctica rara vez se ha documentado", afirmó Huntress.

El conjunto de herramientas estaba compuesto por seis objetos Java y varios adaptadores PL/SQL khunt_*:

- KhuntCmd cargaba cmd.exe y ejecutaba comandos arbitrarios del sistema operativo pasados ​​como SQL.
- KhuntHash leía nombres de usuario y hashes de contraseñas de la tabla interna de usuarios de Oracle y los escribía en un archivo.
- KhuntFS y KhuntFS2 listaban, leían, buscaban y medían el tamaño de los archivos.
- KhuntT confirmaba que el conjunto de herramientas era accesible, y KhuntUnzip descomprimía archivos comprimidos.

Al ejecutar cmd.exe /c whoami a través de KhuntCmd, se obtenía SYSTEM. Los atacantes utilizaron PowerShell y reg.exe para copiar los subárboles de registro SECURITY y SYSTEM en F:\Oracle, ejecutaron tasklist /svc en khunttasks.txt y copiaron los subárboles SAM y SECURITY con esentutl.exe.

Hunters observó que los archivos se almacenaban localmente, pero no pudo confirmar su exfiltración. La empresa no identificó al responsable de la amenaza y rastreó las solicitudes maliciosas hasta 178.162.151[.]229.

Estos indicadores son específicos de este conjunto de herramientas, por lo que ninguna búsqueda de Khunt o KHUNT% revelará la técnica subyacente. La solución consiste en consultas parametrizadas y validación de entrada en la aplicación, además del principio de mínimo privilegio: una cuenta que administra una aplicación pública no debería poder crear código fuente Java ni ejecutar procedimientos almacenados a los que no tenga motivos para acceder.


