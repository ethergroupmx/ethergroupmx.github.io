---
title: "Más de 35,000 aplicaciones creadas con Grok quedaron expuestas en internet"
date: 2026-11-11 11:00:00
categories: [CIBERSEGURIDAD]
tags: [IA, ciberseguridad, privacidad, cloud computing]
description: "Una investigación de Claroc identificó más de 35,000 aplicaciones creadas con Grok accesibles sin autenticación. Algunas exponían información confidencial, contraseñas y datos personales de distintas organizaciones."
image: /assets/314/preview1.png
---

La inteligencia artificial está facilitando la creación de aplicaciones web sin necesidad de contar con amplios conocimientos de programación. Sin embargo, esta facilidad también puede generar nuevos riesgos de seguridad cuando las aplicaciones se publican sin configurar correctamente sus controles de acceso.

Una investigación realizada por la empresa de ciberseguridad Claroc identificó **35,578 aplicaciones creadas con Grok que podían abrirse desde internet sin necesidad de iniciar sesión**. Algunas de ellas contenían información empresarial confidencial, datos personales e incluso contraseñas almacenadas en texto plano.

El hallazgo evidencia cómo una configuración inadecuada puede convertir herramientas diseñadas para agilizar el desarrollo tecnológico en una fuente de exposición de información.

## ¿Qué encontraron los investigadores?

Grok, el asistente de inteligencia artificial desarrollado por la empresa SpaceXSI (anteriormente xAI), cuenta con una función que permite crear aplicaciones web a partir de instrucciones escritas en lenguaje natural.

Al publicar una aplicación, esta recibe una dirección web propia bajo el dominio `grok.me`, y su creador puede establecer quién tiene permitido acceder.

Durante su investigación, Claroc identificó 37,571 aplicaciones que continuaban disponibles en internet. De ellas, 35,578 (94.7 %) permitían visualizar su contenido sin autenticación.

Aunque muchas eran juegos, calculadoras y páginas informativas, los investigadores encontraron aplicaciones que exponían información sensible de diferentes organizaciones.

Entre los datos identificados se encontraban:

- Planes internos de incorporación de nuevos empleados.
- Mapas comerciales con información de cientos de cuentas.
- Propuestas publicitarias confidenciales dirigidas a organismos gubernamentales.
- Directorios de empleados con nombres y datos personales.
- Información médica de pacientes hospitalizados.
- Contraseñas de empleados almacenadas directamente en el código de una aplicación.

Los investigadores también identificaron información interna perteneciente a 30 organizaciones de diferentes sectores, incluidos salud, construcción, energía, transporte y defensa.

## Información confidencial al alcance de cualquiera

Uno de los aspectos más preocupantes fue que algunas aplicaciones no solo permitían consultar información, sino que también presentaban debilidades en sus mecanismos de autenticación y autorización.

En una de sus pruebas, los investigadores crearon una aplicación de gestión de clientes utilizando Grok. La herramienta incorporó opciones de inicio de sesión con Google y X.

Sin embargo, detectaron un error en el código generado: cualquier cuenta de Google que iniciara sesión podía ser agregada al equipo antes de comprobar si realmente estaba autorizada.

Esto permitía que un usuario externo pudiera consultar, modificar e incluso eliminar registros.

Claroc realizó esta prueba exclusivamente sobre aplicaciones de prueba creadas por sus propios investigadores, no sobre las aplicaciones de terceros identificadas durante el análisis.

Otro hallazgo importante fue una aplicación de control de horarios cuyo código contenía contraseñas de empleados en texto plano. Debido a que los archivos de código podían descargarse desde el navegador, esta información quedaba expuesta a cualquier visitante.

## ¿Por qué ocurrió la exposición?

El problema está relacionado principalmente con las configuraciones de publicación y los controles de acceso.

Durante sus pruebas, Claroc observó que al publicar una aplicación, la opción de acceso "Anyone with the link" (Cualquier persona con el enlace) aparecía seleccionada de manera predeterminada en la cuenta utilizada para la investigación.

Esto significa que una aplicación podía quedar accesible para cualquier persona que conociera su dirección, sin requerir autenticación.

Aunque las direcciones generadas pueden parecer difíciles de adivinar, no representan una medida de seguridad suficiente. Los investigadores utilizaron técnicas de descubrimiento de subdominios y registros DNS para localizar aplicaciones disponibles públicamente.

Por su parte, SpaceXSI indicó que las aplicaciones permanecen privadas hasta que sus creadores deciden compartirlas y que las cuentas de sus empleados tienen configurado el acceso privado de forma predeterminada.

Después de recibir el reporte, la compañía retiró las 24 aplicaciones expuestas que habían sido creadas por empleados de SpaceXSI y X. Sin embargo, la investigación señaló que otras aplicaciones de usuarios y organizaciones continuaban disponibles.

## Los riesgos de utilizar inteligencia artificial sin supervisión

La creación de aplicaciones mediante inteligencia artificial representa una oportunidad para agilizar procesos empresariales, desarrollar herramientas internas y reducir tiempos de implementación.

Sin embargo, generar una aplicación funcional no significa que sea segura.

Cuando las herramientas de IA producen código sin una revisión adecuada, pueden introducir errores relacionados con:

- **Autenticación:** permitir el acceso sin verificar correctamente la identidad.
- **Autorización:** no comprobar si un usuario tiene permisos para consultar o modificar información.
- **Exposición de datos:** publicar información confidencial dentro del código o archivos accesibles.
- **Gestión de credenciales:** almacenar contraseñas, claves o tokens sin protección.
- **Configuraciones inseguras:** mantener aplicaciones públicas cuando deberían estar restringidas.

Estos riesgos forman parte de un problema cada vez más relevante: el desarrollo de aplicaciones mediante inteligencia artificial sin la participación o supervisión de los equipos de TI y ciberseguridad.

## ¿Cómo pueden protegerse las organizaciones?

Las empresas que utilizan herramientas de inteligencia artificial para crear aplicaciones deben establecer controles de seguridad antes de permitir que estas se integren a sus operaciones.

Estas son algunas medidas recomendadas:

**1. Identificar las aplicaciones creadas con IA**

Mantener un inventario de las herramientas utilizadas por los colaboradores y de las aplicaciones que se han desarrollado y publicado fuera de los procesos tradicionales de TI.

**2. Revisar los permisos de acceso**

Configurar las aplicaciones como privadas o restringidas a usuarios autorizados. No utilizar enlaces públicos como mecanismo de protección para información empresarial.

**3. Implementar controles de autenticación y autorización**

Verificar que cada usuario esté correctamente identificado y que sus permisos correspondan exclusivamente a las funciones que necesita realizar.

**4. Evitar almacenar información sensible en el código**

Las contraseñas, claves API, tokens y credenciales deben mantenerse en mecanismos seguros de administración de secretos, nunca directamente en archivos accesibles desde el navegador.

**5. Realizar auditorías de seguridad**

Revisar el código generado por herramientas de IA, evaluar las configuraciones de las aplicaciones y realizar pruebas de vulnerabilidad antes de utilizarlas en ambientes productivos.

**6. Establecer políticas para el uso de inteligencia artificial**

Definir qué información puede utilizarse en herramientas externas, qué aplicaciones pueden publicarse y cuáles requieren autorización del departamento de TI.

## Conclusión

El caso de las aplicaciones creadas con Grok demuestra que la rapidez del desarrollo tecnológico no debe estar por encima de la seguridad de la información.

La inteligencia artificial puede simplificar la creación de soluciones digitales, pero también puede generar aplicaciones con permisos inadecuados, errores de autenticación y exposición de información confidencial.

**La seguridad debe formar parte del desarrollo desde el primer momento, no ser una revisión posterior a la publicación.**
