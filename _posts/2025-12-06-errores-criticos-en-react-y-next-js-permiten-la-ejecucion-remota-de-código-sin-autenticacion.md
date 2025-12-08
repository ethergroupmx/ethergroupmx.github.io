---
title: "URGENTE: errores críticos en React y Next.js permiten la ejecución remota de código sin autenticación (PARCHEA!)"
date: 2025-12-06 09:00:00 
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, seguridad web, programación]
description: Se ha revelado un fallo de seguridad de máxima gravedad en el protocolo "Flight" de React Server Components (RSC) que, de explotarse con éxito, podría provocar la ejecución remota de código.
image: /assets/194/preview1.png
---

La vulnerabilidad, identificada como CVE-2025-55182, tiene una puntuación CVSS de 10.0.

Según declaró el equipo de React en una alerta emitida hoy, la vulnerabilidad permite la ejecución remota de código sin autenticación al explotar un fallo en la forma en que React decodifica las cargas útiles enviadas a los endpoints de React Server Function.

# TL;DR

- El investigador original la denominó React2Shell, ya que provoca la ejecución de código arbitrario por parte de atacantes remotos (posiblemente no autenticados).
- CVE-2025-55182 (React) y CVE-2025-66478 (Next.js) son vulnerabilidades críticas de RCE.
- Afectan al protocolo "Flight" de React Server Components (RSC).
- No es necesario autenticación para su ejecución.
- Las configuraciones predeterminadas son vulnerables: una aplicación estándar de Next.js creada con create-next-app puede ser explotada sin necesidad de que el desarrollador modifique el código.
- La explotación solo requiere una solicitud HTTP diseñada y ha demostrado una fiabilidad cercana al 100% en las pruebas.
- La falla se debe a una deserialización insegura en la lógica de gestión de la carga útil de RSC, lo que permite que los datos controlados por el atacante influyan en la ejecución del servidor.
- Se requiere la aplicación inmediata de parches.
- Los datos de Wiz Research muestran que el 39% de los entornos de nube contienen instancias vulnerables.

Incluso si su aplicación no implementa ningún endpoint de React Server Function, podría ser vulnerable si es compatible con React Server Components.

Si el código React de la aplicación no usa un servidor, esta vulnerabilidad no afecta a la aplicación. Si no se usa un framework, un bundler o un plugin de bundler compatible con los componentes de servidor de React, esta vulnerabilidad no afecta a la aplicación.

Según la empresa de seguridad en la nube Wiz, el problema se debe a una deserialización lógica derivada del procesamiento inseguro de las cargas útiles de RSC. Como resultado, un atacante no autenticado podría crear una solicitud HTTP maliciosa (PoC y PoC) a cualquier endpoint de función de servidor que, al ser deserializada por React, ejecute código JavaScript arbitrario en el servidor.

![Imagen 01](/assets/194/194-01.png)

### La vulnerabilidad afecta a las versiones 19.0, 19.1.0, 19.1.1 y 19.2.0 de los siguientes paquetes npm:

- react-server-dom-webpack
- react-server-dom-parcel
- react-server-dom-turbopack

Se ha solucionado en las versiones 19.0.1, 19.1.2, and 19.2.1. El investigador de seguridad neozelandés Lachlan Davidson fue el responsable del descubrimiento y reporte de la falla el 29 de noviembre de 2025. Lachlan también publicó el sitio React2Shell y su PoC.

### ¿Qué productos están afectados?

Cabe destacar que la vulnerabilidad también afecta a Next.js que utiliza App Router. El problema se ha identificado con el identificador CVE-2025-66478 (CVSS: 10.0). Afecta a las versiones ≥14.3.0-canary.77, ≥15 y ≥16. Las versiones parcheadas son 16.0.7, 15.5.7, 15.4.8, 15.3.6, 15.2.6, 15.1.9 y 15.0.5.
Es probable que cualquier framework o biblioteca que incluya la implementación de React-Server se vea afectado. Esto incluye, entre otros:

- Next.js
- Plugin RSC de Vite
- Plugin RSC de Parcel
- Vista previa de React Router RSC
- RedwoodSDK
- Waku

No obstante, cualquier biblioteca que incluya RSC probablemente se vea afectada por la falla. Esto incluye, entre otros, el complemento Vite RSC, el complemento Parcel RSC, la vista previa de React Router RSC, RedwoodJS y Waku.

- CVE-2025-55182 en React.js
- CVE-2025-66478 específicamente para Next.js framework

Los datos de Wiz indican que el 39% de los entornos en la nube contienen instancias de Next.js o React en versiones vulnerables a CVE-2025-55182 o CVE-2025-66478. En cuanto a Next.js, el framework está presente en el 69% de los entornos. Cabe destacar que el 61% de estos entornos tienen aplicaciones públicas que ejecutan Next.js, lo que significa que el 44% de todos los entornos en la nube tienen instancias de Next.js expuestas públicamente.

**Dada la gravedad de la vulnerabilidad, se recomienda a los usuarios aplicar las correcciones lo antes posible para una protección óptima.**

### Actualización 18.50hs

Cloudflare ha implementado una nueva regla WAF para proteger a sus clientes de esta vulnerabilidad. No es necesario realizar ninguna acción; la regla está habilitada por defecto. 

Vercel ha creamos reglas para abordar esta vulnerabilidad, brindando protección a nivel de plataforma a todos los proyectos alojados.

Google ha actualizado su scanner Tsunami para detectar la vulnerabilidad.

### Actualización 04/12

De acuerdo a datos de FOFA, hay más de 20.000 aplicaciones React expuestas en línea.

        body="react.production.min.js"
        body="React.createElement("

De acuerdo a datos de Shodan, hay más de 30.000 aplicaciones React expuestas en línea.

      http.html:"react.production.min.js"
        http.title:"React App"
        http.html:"React.createElement"

Y, de acuerdo a ZoomEye hay más de 3,1 milllones.

      http.body="react.production.min.js" ||
        http.body="React.createElement(" || 
        app="React Router" ||
        app="React.js"


**En este repositorio de Neurolint-CLI se puede encontrar una herramienta para verificar versiones vulnerables y actualizar. Detecta React 19 + Next.js 15-16 vulnerable, actualiza a versiones parcheadas y crea copias de seguridad automáticas.**

### Actualización 05/12

**Vercel ha publicado un paquete NPM para actualizar aplicaciones Next.js afectada. Usa npx fix-react2shell-next o visita la página de GitHub para obtener más información.**

El análisis de los intentos de explotación en la infraestructura del honeypot de AWS MadPot ha identificado actividad de explotación desde direcciones IP e infraestructura históricamente vinculadas a actores de amenazas con vínculos con China.

En concreto, el gigante tecnológico afirmó haber identificado infraestructura asociada con Earth Lamia, un grupo con vínculos con China, al que se atribuyó la explotación de una falla crítica de SAP NetWeaver (CVE-2025-31324) a principios de este año.

Los ataques también se han originado en la infraestructura relacionada con otro actor de ciberamenazas con vínculos con China, conocido como Jackpot Panda, que ha atacado principalmente a entidades que participan o apoyan operaciones de juegos de azar en línea en el Este y Sudeste Asiático.

Según CrowdStrike, Jackpot Panda está activo desde al menos 2020 y ha atacado relaciones de confianza con terceros para intentar implementar implantes maliciosos y obtener acceso inicial. Cabe destacar que el actor de amenazas estuvo vinculado a la vulneración de la cadena de suministro de una aplicación de chat conocida como Comm100 en septiembre de 2022. ESET rastrea la actividad como Operación ChattyGoblin.

Desde entonces, se ha descubierto que un contratista chino de hacking, I-Soon, podría haber estado involucrado en el ataque a la cadena de suministro, alegando solapamientos de infraestructura. Curiosamente, los ataques perpetrados por el grupo en 2023 se han centrado principalmente en víctimas de habla china, lo que indica una posible vigilancia a nivel nacional.


