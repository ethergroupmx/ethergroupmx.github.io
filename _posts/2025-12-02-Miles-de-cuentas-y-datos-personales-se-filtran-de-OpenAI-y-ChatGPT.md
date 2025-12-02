---
title: "Miles de cuentas y datos personales se filtran de OpenAI y ChatGPT"
date: 2025-12-02 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, IA, news, hacking]
description: Tarde o temprano tenía que ocurrir. Sam Altman avisó hace unas semanas que ChatGPT no es lugar para ir confiando los datos más privados e informaciones personales que no se deben compartir, por lo que pudiera pasar.
image: /assets/191/preview1.png
---

Pues lo que tenía que ocurrir, ya ha ocurrido: un ataque informático ha logrado traspasar las barreras de seguridad de OpenAI y han quedado expuestas miles de cuentas privadas de usuarios. Todavía están evaluando el problema para sacar cuentas de la magnitud real del hackeo.

En un comunicado emitido este jueves, OpenAI reconoce el robo de datos, aunque aclara que no se trata de una intrusión en los sistemas de ChatGPT, sino de la API, el sistema que usan los desarrolladores para integrar servicios de OpenAI en sus productos informáticos.

Para descargarse de responsabilidades, el comunicado oficial deja claro en sus primeras líneas que no les han entrado a ellos, sino que los ciberdelincuentes se han colado en los sistemas de Mixpanel, la empresa con la que colaboran para analizar la ingente cantidad de datos que generan a diario.

*"No ha sido una vulneración de los sistemas de OpenAI. Ningún chat, solicitud de API, datos de uso de API, contraseñas, credenciales, claves de API, detalles de pago ni identificaciones gubernamentales se han visto comprometidos ni expuestos".*

Según el escrito, *"el 9 de noviembre de 2025, Mixpanel detectó que un atacante había obtenido acceso no autorizado a parte de sus sistemas y había exportado un conjunto de datos con información limitada de identificación de clientes e información analítica. Mixpanel notificó a OpenAI que estaban investigando y, el 25 de noviembre de 2025, compartió con nosotros el conjunto de datos afectado"*.

![Imagen 01](/assets/191/191-01.png)

### ¿Qué datos se han filtrado?

Los usuarios de la API son, principalmente, desarrolladores y programadores informáticos, así que los usuarios que se dediquen a otras cosas no tendrían por qué preocuparse. En este caso, estos son los datos que se han filtrado:

- Nombre del usuario de la cuenta de la API.
- Dirección de correo electrónico asociada a la cuenta API
- Ubicación aproximada según el navegador del usuario API (ciudad, estado, país)
- Sistema operativo y navegador utilizados para acceder a la cuenta API
- Sitios web de referencia
- ID de organización o usuario asociados a la cuenta API

OpenAI ha confirmado también que se ha desconectado totalmente de Mixpanel, acorde con los protocolos de investigación de la intrusión, hasta dilucidar el alcance exacto del ataque.


