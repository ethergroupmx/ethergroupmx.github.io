---
title: La vida útil de los certificados SSL/TLS se reducirá a 47 días para 2029
categories: [CIBESEGURIDAD]
tags: [ciberseguridad, news]
description: El Foro de Autoridades de Certificación/Navegadores ha votado a favor de reducir significativamente la vida útil de los certificados SSL/TLS.
image: /assets/126/preview1.png
---

El Foro de Autoridades de Certificación/Navegadores ha votado a favor de reducir significativamente la vida útil de los certificados SSL/TLS durante los próximos 4 años, con una duración final de tan solo 47 días a partir de 2029.

Este Foro es un grupo de autoridades de certificación (AC) y proveedores de software, incluyendo desarrolladores de navegadores, que trabajan juntos para establecer y mantener estándares de seguridad para los certificados digitales utilizados en las comunicaciones por Internet. Entre sus miembros se incluyen importantes AC como DigiCert y GlobalSign, así como proveedores de navegadores como Google, Apple, Mozilla y Microsoft.

A principios de este año, Apple propuso una moción para reducir la vida útil de los certificados, que Sectigo, el equipo de Google Chrome y Mozilla respaldaron.

Esta propuesta reduciría gradualmente la vida útil de los certificados durante los próximos cuatro años, pasando de los 398 días actuales a 47 días en marzo de 2029.

El objetivo es minimizar los riesgos derivados de datos de certificados obsoletos, algoritmos criptográficos obsoletos y la exposición prolongada a credenciales comprometidas. También anima a empresas y desarrolladores a utilizar la automatización para renovar y rotar los certificados TLS, reduciendo la probabilidad de que los sitios web funcionen con certificados caducados.

Los certificados SSL/TLS son archivos digitales que permiten la comunicación segura a través de internet (HTTPS) mediante el cifrado de datos y la autenticación de sitios web. Cifran la conexión para que los datos confidenciales, como las contraseñas y los datos de tarjetas de crédito introducidos en los formularios del sitio web, no puedan ser interceptados por atacantes.

Estos certificados también se utilizan para autenticar el sitio web y garantizar la integridad de los datos, lo que significa que la información intercambiada entre el usuario y el servidor no ha sido manipulada.

Cuando estos certificados caducan sin renovación, los usuarios ven una advertencia en su navegador que les informa que su conexión no es privada ni segura. Actualmente, la vida útil y la Validación de Control de Dominio (DCV) de estos certificados es de 398 días, pero la mayoría de las autoridades de certificación coincidieron en que es un plazo excesivo en el panorama de seguridad actual.

Con 25 votos a favor y ninguno en contra, el Foro de CA/Navegadores ha decidido acortar la vida útil de la siguiente manera:

- A partir del 15 de marzo de 2026, la vida útil de los certificados y la DCV se reducirán a 200 días.
- A partir del 15 de marzo de 2027, la vida útil de los certificados y la DCV se reducirán a 100 días.
- A partir del 15 de marzo de 2029, la vida útil de los certificados se reducirá a 47 días y la DCV a 10 días.

Acortar el ciclo de vida de los certificados seguramente generará una sobrecarga de gestión y una gran carga para quienes gestionan múltiples dominios. Sin embargo, se espera que obligue a las empresas que solicitan certificados a revalidarse con mayor frecuencia, fomente la automatización y, en última instancia, aumente la agilidad y la seguridad del ecosistema.

Este acortamiento gradual de la vida útil de los certificados brinda a las entidades afectadas tiempo suficiente para implementar y realizar la transición a sistemas de renovación automática de certificados, como los que ofrecen los proveedores de la nube, Let's Encrypt o los proveedores de certificados que admiten el protocolo ACME.


