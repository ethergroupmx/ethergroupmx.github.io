---
title: "Los hackers utilizan un registro falso de Microsoft Entra Passkey para obtener acceso a Microsoft 365"
date: 2026-07-13 09:00:00 
categories: [CIBERATAQUES]
tags: [phishing, ingeniería social, ciberataques, ciberseguridad]
description: Una nueva campaña de ingeniería social utiliza llamadas de voz para engañar a usuarios de Microsoft 365 y registrar claves de acceso maliciosas en Entra, facilitando el robo de datos y posteriores ataques de extorsión.
image: /assets/274/preview1.png
---

El ciberdelincuente, identificado por Okta con el nombre de usuario O-UNC-066 , ha desplegado un kit de phishing controlado por panel capaz de atacar el proceso de registro de claves de acceso . La actividad se ha centrado en los sectores de alimentación y bebidas, tecnología, sanidad, automoción, construcción y aviación.

"El atacante registra dominios que incorporan la palabra 'passkey' como parte de una estafa de phishing por voz ('vishing')", explicó Houssem Eddine Bordjiba, investigador de Okta . "Luego, llama por teléfono a los usuarios objetivo para intentar convencerlos de que deben registrar una nueva contraseña".

Posteriormente, se redirige a los usuarios a un kit de phishing idéntico al proceso de registro de clave de acceso de Microsoft, dando la impresión de que están añadiendo una clave de acceso con Microsoft, cuando, en realidad, el atacante registra su propia clave de acceso en su cuenta de Microsoft, otorgándoles acceso no autorizado.

Este desarrollo coincide con la decisión de Microsoft de permitir a los administradores configurar campañas de registro para incentivar a los usuarios a registrar sus claves de acceso durante el inicio de sesión, con el objetivo de ayudar a las organizaciones a impulsar la adopción masiva de estas claves. En otras palabras, los ciberdelincuentes están abusando del proceso de actualización de seguridad, resistente al phishing, como señuelo para registrar sus propias claves de acceso en las cuentas de las víctimas y facilitar actividades posteriores.

A diferencia de las páginas de destino de tipo adversario-en-el-medio ( AitM ), que son frecuentes en las campañas de phishing diseñadas para robar credenciales y tokens de autenticación multifactor (MFA), el kit de phishing utilizado en estos ataques es un panel PHP controlado por un operador en el que se guía a la víctima a través del proceso de registro de la clave de acceso prácticamente en tiempo real.

«El operador puede usar el kit para adaptar la experiencia del usuario a los requisitos de autenticación multifactor (MFA) de cada víctima (TOTP, notificaciones push con coincidencia de números, OTP por SMS) durante la sesión», explicó la empresa de seguridad de identidad. «Quien realiza la llamada puede controlar y ajustar en tiempo real las páginas de phishing y las notificaciones que ve el usuario objetivo».

Se sospecha que el atacante está utilizando el kit para tomar el control de la cuenta de la víctima y engañarla para que apruebe el registro de una clave de acceso iniciado por el atacante. Por el momento, no hay indicios de que el kit esté redirigiendo a los usuarios a proveedores de identidad de terceros como Okta.

La secuencia completa de acciones se muestra a continuación:

- La primera página del kit de phishing (/gate) muestra un icono de carga de página mientras el kit realiza comprobaciones anti-análisis en segundo plano.
- La segunda página (/identify) solicita un nombre de usuario.
- La siguiente página (/password) le pide al usuario que ingrese una contraseña.
- Las credenciales recopiladas se envían en una solicitud POST a un panel de operador en "/backend.php".
- El operador del kit de phishing (probablemente diferente de la persona que llama a la víctima) introduce las credenciales robadas en la página de inicio de sesión legítima de Microsoft para el inquilino objetivo.
- La víctima ve una página "/processing" que muestra otra pantalla de carga mientras espera las instrucciones del operador en función de los desafíos de autenticación multifactor (MFA) que se le presentan en el flujo legítimo.
- La siguiente página del kit de phishing se presenta al usuario: "/submit-otp" para un desafío de contraseña de un solo uso (OTP) basado en SMS, "/submit-authenticator" para un desafío OTP basado en tiempo o "/approve-authenticator" para un desafío MFA push .
- La contraseña de un solo uso (OTP) capturada se envía en una solicitud POST a "/backend.php".

En este punto, la víctima ha sido engañada por teléfono para que apruebe el acceso del atacante a su cuenta de Microsoft 365. La cadena de ataque inicia entonces otro conjunto de acciones centradas en el pretexto de la clave de acceso.

- La víctima es redirigida a la página "/passkey/register", que le indica al usuario que cree una clave de acceso.
- La página "/passkey" de Microsoft solicita al usuario que guarde su clave de recuperación para confirmar su contraseña.
- La página "/passkey/check" solicita al usuario que verifique la última palabra utilizada en la frase semilla.
- La página "/done" confirma que el registro de la clave de acceso se realizó correctamente.

La clave de recuperación contiene una serie de 12 palabras similar a una frase secreta o mnemotécnica, típica de las carteras de criptomonedas. Se considera que este paso es una estrategia de distracción para mantener a la víctima ocupada mientras registra su propia clave de acceso en la cuenta de Microsoft.

«El kit de phishing parece aprovecharse de la falta de familiaridad del usuario con la autenticación mediante clave de acceso», explicó Okta. «En un proceso real de registro de clave de acceso, el usuario esperaría que apareciera un cuadro de diálogo del sistema para registrar una clave en su dispositivo. Las páginas de clave de acceso de este kit de phishing parecen imitar este proceso sin registrar ninguna clave».

Okta señaló que un actor malicioso vinculado a O-UNC-066 ha estado operando un sitio de filtración de datos desde abril de 2026 bajo el nombre de Pink. Palo Alto Networks Unit 42 está rastreando este grupo como CL-CRI-1147, describiéndolo como afiliado a un colectivo descentralizado de ciberdelincuencia conocido como The Com , del cual forman parte Scattered Spider, ShinyHunters y LAPSUS$.

