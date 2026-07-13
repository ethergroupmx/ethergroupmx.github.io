---
title: "Atacante utiliza un script de PowerShell generado por IA para mapear Active Directory"
date: 2026-07-13 09:00:00 
categories: [CIBERATAQUES]
tags: [malware, ingeniería social, ciberataques, ciberseguridad, phishing]
description: Investigadores de ciberseguridad han detectado una intrusión en la que un atacante desconocido utilizó un script de PowerShell codificado con Vibe para la enumeración de Active Directory (AD).
image: /assets/275/preview1.png
---

> "El script buscó el controlador de dominio (DC) y mapeó usuarios, equipos y dominios, antes de crear un directorio y exportar varios archivos, y finalmente crear AD_Report.html para medir el éxito del intento de enumeración", explicaron los investigadores de Huntress, Jevon Ang y Dray Agha.

La cadena de ataque consistió en que el atacante estableciera acceso mediante el Protocolo de Escritorio Remoto (RDP) a un servidor Windows unido al dominio con credenciales previamente comprometidas, para luego instalar las herramientas en la carpeta "C:\ProgramData\". El incidente tuvo lugar a principios de junio de 2026.

Esto incluyó una carga útil generada por inteligencia artificial (IA) para mapear el entorno de Active Directory. La evaluación se basa en varias señales reveladoras, como el título de la iteración de la solicitud, cadenas de texto de marcador de posición, código excesivamente complejo con múltiples métodos para encontrar un controlador de dominio y una salida de consola con formato de color cian, verde, rojo y amarillo.

Huntress describió el script de PowerShell personalizado como "muy agresivo" y "ruidoso", utilizando un "mecanismo de reserva en cascada de cinco pasos" para facilitar el reconocimiento y el descubrimiento. Su título es "100% Working AD Information Gathering Script - FULLY FIXED" lo que sugiere una interacción constante con un modelo de lenguaje extenso (LLM).

Una vez localizado el controlador de dominio principal, inicia una rutina de recopilación de datos para obtener sistemáticamente usuarios, equipos, grupos, unidades organizativas (OU) y relaciones de confianza de Active Directory, y almacenar los detalles en un directorio temporal.

Aproximadamente 30 minutos después, el atacante procedió a desplegar s5cmd, una herramienta legítima para operaciones masivas de archivos, junto con SharpShares, una utilidad de enumeración de recursos compartidos de red basada en C#, para buscar repositorios de datos accesibles para los usuarios.

En la etapa final, los datos se guardan en archivos CSV, se archivan y se extraen a un servidor remoto, no sin antes crear un archivo HTML que resume el robo de datos en forma de informe de inventario de Active Directory.

Este desarrollo es una señal más de que los ciberdelincuentes están ampliando su arsenal con malware codificado mediante inteligencia artificial, generado con la ayuda de modelos de IA, aunque la tecnología no se esté utilizando de formas nunca antes vistas. Lo que sí cambia es que reduce las barreras de entrada para el cibercrimen, permitiendo que actores menos experimentados desarrollen herramientas altamente sofisticadas y evasivas con un mínimo esfuerzo.

En un informe publicado la semana pasada, Sygnia reveló que los atacantes con IA no necesariamente necesitan malware novedoso ni vulnerabilidades de día cero, sino que el verdadero cambio radica en que las intrusiones cibernéticas se pueden orquestar a una velocidad y escala mayores de las que los defensores pueden contener.

La empresa de respuesta a incidentes informó haber detectado un ataque en la nube asistido por IA que, en aproximadamente 72 horas, se propagó desde el acceso inicial hasta una vulneración generalizada de un entorno de gran tamaño basado en Amazon Web Services (AWS). Se estima que el objetivo final de la actividad fue económico, utilizando el acceso a la infraestructura en la nube de la víctima como herramienta de extorsión.

Para ejercer mayor presión sobre las víctimas, el atacante llevó a cabo una serie de acciones:

- Denegar el acceso a los buckets de S3
- Limitar los servicios o contenedores de ECS a una capacidad máxima de cero
- Crear reglas ACL para bloquear el acceso a la red
- Vaciar las colas de SQS

> "La importancia no radicaba en que la IA introdujera nuevas técnicas de ataque, ya que cada acción observada se correspondía con comportamientos adversarios ya conocidos, sino en que redujo el tiempo y el esfuerzo necesarios para implementar dichas técnicas en un entorno complejo", señaló Sygnia.

