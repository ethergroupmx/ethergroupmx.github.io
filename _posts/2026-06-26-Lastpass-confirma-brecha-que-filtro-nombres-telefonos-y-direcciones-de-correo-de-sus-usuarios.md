---
title: "LastPass confirma (de nuevo) brecha que filtró nombres, teléfonos y direcciones de correo de sus usuarios"
date: 2026-06-25 11:00:00
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, phishing, privacidad, vulnerabilidad, news]
description: LastPass confirmó una nueva brecha de seguridad vinculada a un proveedor externo, que expuso datos de contacto e información de soporte de algunos usuarios. Aunque las bóvedas de contraseñas no fueron comprometidas, el incidente incrementa el riesgo de campañas de phishing e ingeniería social.
image: /assets/268/preview1.png
---

LastPass ha tenido un historial complicado en materia de seguridad durante los últimos años. De acuerdo con TechCrunch, la brecha no ocurrió directamente en LastPass, sino en Klue, una plataforma que la empresa utiliza en sus operaciones comerciales. Según el reporte, los atacantes aprovecharon el acceso a Klue para obtener tokens OAuth que la plataforma almacenaba en nombre de sus clientes, incluido LastPass.

LastPass se suma a una creciente lista de empresas de ciberseguridad que han reportado robos de datos como consecuencia de la brecha de seguridad en Klue, que la compañía reveló la semana pasada. Otras empresas afectadas incluyen Gong, Jamf, HackerOne, Insurity, OneTrust, Recorded Future, Snyk, Sprout Social, and Tanium.

Con esas credenciales, los atacantes lograron entrar en el entorno de Salesforce de LastPass y extraer datos de sus usuarios. La información comprometida incluye nombres, números de teléfono, direcciones de correo electrónico y direcciones físicas, junto con datos de casos de soporte al cliente y registros relacionados con ventas. Tras detectar la presencia de atacantes en su sistema, Klue notificó a LastPass sobre el incidente.

Lo que todavía no está claro es el contenido exacto de los tickets de soporte al cliente. Ese tipo de registros suele contener fragmentos de información sensible, ya que los usuarios generalmente contactan con soporte cuando tienen problemas de facturación o necesitan recuperar el acceso a sus cuentas. Incidentes anteriores con datos de tickets de soporte han llegado a exponer credenciales y documentos de identidad oficiales.

LastPass ha declarado que la brecha de Klue no afectó a sus sistemas en ningún momento. Las contraseñas almacenadas en las bóvedas de los usuarios permanecen seguras, y no hay evidencia de que los atacantes accedieran a datos relacionados con la plataforma Gong, otra herramienta integrada con Klue.

La reputación de LastPass lleva tiempo acumulando golpes. En 2022, la compañía sufrió una brecha mucho más grave en la que los atacantes se hicieron con todas las bóvedas cifradas de contraseñas de sus clientes. Aunque esos archivos estaban protegidos con las contraseñas maestras de cada usuario, los hackers consiguieron descifrar algunas de ellas que usaban claves débiles y las aprovecharon para acceder a billeteras de criptomonedas.

Este nuevo incidente es menos catastrófico en comparación, pero tiene sus propias implicaciones. Tener tu nombre, teléfono y dirección en manos de atacantes es suficiente para convertirte en objetivo de phishing o ingeniería social. LastPass lo reconoce en su comunicado oficial y recomienda a sus usuarios estar alerta ante cualquier contacto no solicitado, ya sea por email, teléfono u otros canales.

Otro detalle que vale la pena recordar es que nadie de LastPass te pedirá jamás tu contraseña maestra. Si recibes un mensaje solicitándola, independientemente de cómo esté redactado, es una señal de alarma.

Según el reporte, el responsable del ataque es un grupo de extorsión llamado Icarus, que también ha atacado a otras compañías a través de la brecha en Klue. El grupo ya amenazó con publicar los datos robados si no recibe un pago por rescate. Klue, por su parte, aún no ha confirmado cuántos clientes se han visto afectados ni si ha habido contacto con los atacantes.

LastPass confirmó que han remediado el problema y los tokens OAuth expuestos han sido rotados desde entonces. "Los productos, servicios e infraestructuras de LastPass no se vieron afectados de ninguna manera y las bóvedas de clientes siguen siendo seguros", mencionó.

