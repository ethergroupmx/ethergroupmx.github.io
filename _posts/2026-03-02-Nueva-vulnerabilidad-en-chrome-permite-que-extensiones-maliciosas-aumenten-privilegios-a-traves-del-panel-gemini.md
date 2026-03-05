---
title: "Nueva vulnerabilidad en Chrome permite que extensiones maliciosas aumenten privilegios a través del panel Gemini"
date: 2026-03-02 09:00:00 
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, ciberseguridad, IA]
description: Investigadores de ciberseguridad han revelado detalles de una falla de seguridad ahora parcheada en Google Chrome que podría haber permitido a los atacantes aumentar los privilegios y obtener acceso a archivos locales en el sistema.
image: /assets/226/preview1.png
---

La vulnerabilidad, identificada como CVE-2026-0628 (puntuación CVSS: 8,8), se ha descrito como un caso de aplicación insuficiente de políticas en la etiqueta WebView. Google la parcheó a principios de enero de 2026 en las versiones 143.0.7499.192/.193 para Windows/Mac y 143.0.7499.192 para Linux.

"La aplicación insuficiente de políticas en la etiqueta WebView en Google Chrome anterior a la versión 143.0.7499.192 permitió que un atacante que convenciera a un usuario para que instalara una extensión maliciosa inyectara scripts o HTML en una página privilegiada a través de una extensión de Chrome diseñada", según una descripción en la Base de Datos Nacional de Vulnerabilidades (NVD) del NIST.

Gal Weizman, investigador de la Unidad 42 de Palo Alto Networks, quien descubrió e informó la falla el 23 de noviembre de 2025, dijo que el problema podría haber permitido que extensiones maliciosas con permisos básicos tomaran el control del nuevo panel Gemini Live en Chrome.

El panel lateral, que utiliza la nueva URL "chrome://glic" que usa un componente WebView para cargar la aplicación web "gemini.google[.]com", se puede abrir haciendo clic en el icono de Gemini, ubicado en la esquina superior derecha de la barra de herramientas de Chrome. Google añadió la integración de Gemini a Chrome en septiembre de 2025.

Un atacante podría haber abusado de este ataque para lograr una escalada de privilegios, lo que le permitiría acceder a la cámara y al micrófono de la víctima sin su permiso, tomar capturas de pantalla de cualquier sitio web y acceder a archivos locales. El problema se conoce como Glic Jack , abreviatura de Gemini Live en Chrome.

Los hallazgos resaltan un vector de ataque emergente que surge de la integración de inteligencia artificial (IA) y capacidades de agencia directamente en los navegadores web para facilitar el resumen de contenido en tiempo real, la traducción y la ejecución automatizada de tareas, ya que las mismas capacidades podrían usarse de forma abusiva para realizar acciones privilegiadas.

El problema, en esencia, es la necesidad de otorgar a estos agentes de IA acceso privilegiado al entorno de navegación para realizar operaciones de varios pasos, lo que se convierte en un arma de doble filo cuando un atacante incorpora mensajes ocultos en una página web maliciosa y un usuario víctima es engañado para acceder a ella a través de ingeniería social o algún otro medio.

El mensaje podría indicar al asistente de IA que realice acciones que, de otro modo, el navegador bloquearía, lo que provocaría la exfiltración de datos o la ejecución de código. Peor aún, la página web podría manipular al agente para que almacene las instrucciones en memoria , lo que provocaría su persistencia entre sesiones.

![Imagen 01](/assets/226/226-01.png)

Además de la superficie de ataque ampliada, Unit 42 dijo que la integración de un panel lateral de IA en los navegadores agentic trae de vuelta los riesgos de seguridad clásicos del navegador.

"Al colocar este nuevo componente en el contexto de privilegios elevados del navegador, los desarrolladores podrían crear inadvertidamente nuevas fallas lógicas y debilidades de implementación", afirmó Weizman. "Esto podría incluir vulnerabilidades relacionadas con secuencias de comandos entre sitios (XSS), escalada de privilegios y ataques de canal lateral que pueden ser explotados por sitios web o extensiones del navegador con menos privilegios".

Si bien las extensiones del navegador funcionan según un conjunto definido de permisos, la explotación exitosa de CVE-2026-0628 socava el modelo de seguridad del navegador y permite a un atacante ejecutar código arbitrario en "gemini.google[.]com/app" a través del panel del navegador y obtener acceso a datos confidenciales.

"Una extensión con acceso a un conjunto de permisos básicos a través de la API declarativeNetRequest otorgó permisos que podrían haber permitido a un atacante inyectar código JavaScript en el nuevo panel de Gemini", añadió Weizman. "Cuando la aplicación de Gemini se carga dentro de este nuevo componente del panel, Chrome la conecta con acceso a potentes funciones".

Cabe destacar que la API declarativeNetRequest permite que las extensiones intercepten y modifiquen las propiedades de las solicitudes y respuestas web HTTPS. Las extensiones de bloqueo de anuncios la utilizan para impedir la emisión de solicitudes de carga de anuncios en páginas web.

"La interpretación de Chromium de lo que salió mal aquí es que los componentes WebView (con los que 'chrome://glic' integra la aplicación web de Gemini) se olvidaron de ser rechazados al considerar la aplicación de la regla [declarativeNetRequest]", dijo Weizman en X.

En otras palabras, todo lo que necesita un atacante es engañar a un usuario desprevenido para que instale una extensión especialmente diseñada, que luego podría inyectar código JavaScript arbitrario en el panel lateral de Gemini para interactuar con el sistema de archivos, tomar capturas de pantalla, acceder a la cámara, encender el micrófono: todas las funciones necesarias para que el asistente de IA realice sus tareas.

"Esta diferencia en el tipo de componente que carga la aplicación Gemini marca la diferencia entre un comportamiento predeterminado y una falla de seguridad", afirmó Unit 42. Es normal que una extensión influya en un sitio web. Sin embargo, una extensión que influya en un componente integrado en el navegador supone un grave riesgo de seguridad.







