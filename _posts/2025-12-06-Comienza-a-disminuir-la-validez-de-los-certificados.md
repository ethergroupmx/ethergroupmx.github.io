---
title: "Desde 2026 a 2029 comienza a disminuir la validez de los certificados (Are you ready?)"
date: 2025-12-06 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [seguridad web, web, ciberseguridad]
description: Apple propuso al CA/Browser Forum reducir la vigencia máxima de los certificados digitales de 398 a 45 días para mejorar la seguridad.
image: /assets/195/preview1.png
---

Apple envió anteriormente una propuesta al CA/Browser Forum —la entidad que supervisa a las autoridades de certificación y a los desarrolladores de navegadores— en la que sugirió disminuir el periodo máximo de validez de los certificados digitales. Su recomendación fue reducirlo de 398 días a únicamente 45, con el fin de reforzar la seguridad.

**Tras un debate, el foro acordó un límite ligeramente mayor, de 47 días, lo que significa que, en el futuro, todos los certificados de confianza pública (excepto los certificados raíz) estarán limitados a esa duración.**

Con 25 votos a favor y ninguno en contra, el Foro de CA/Navegadores ha decidido acortar la vida útil de la siguiente manera:

- A partir del 15 de marzo de 2026, la vida útil de los certificados y la DCV se reducirán a 200 días.
- A partir del 15 de marzo de 2027, la vida útil de los certificados y la DCV se reducirán a 100 días.
- A partir del 15 de marzo de 2029, la vida útil de los certificados se reducirá a 47 días y la DCV a 10 días.

En respuesta, Let's Encrypt ha anunciado que reducirá gradualmente la validez de sus certificados para cumplir con los requisitos básicos del Foro. Para 2028, todos los certificados emitidos por Let's Encrypt tendrán una duración máxima de 45 días.

La transición seguirá este calendario:

- A partir del 13 de mayo de 2026: Let's Encrypt cambiará el perfil ACME de TLSserver a una validez de certificado de 45 días. Esta fase es opcional y está destinada exclusivamente a pruebas.
- A partir del 10 de febrero de 2027: El perfil ACME "clásico" predeterminado pasará a una validez de certificado de 64 días, con un periodo de reutilización de la autorización de 10 días.
- A partir del 16 de febrero de 2028: El perfil ACME "clásico" predeterminado adoptará un periodo de validez de 45 días, lo que lo convierte en el periodo máximo de validez para todos los certificados recién emitidos.

Actualmente, una vez validado un dominio, se puede utilizar para obtener certificados por un máximo de 30 días. Para 2028, ese periodo se reducirá drásticamente a tan solo 7 horas. Si no se emite un certificado en esas siete horas, se deberá revalidar el control del dominio antes de proceder a la emisión.

**La mayoría de los usuarios que dependen de flujos de trabajo totalmente automatizados de emisión, renovación e implementación no necesitarán realizar cambios. Sin embargo, deben confirmar que su automatización sea compatible con una vida útil de los certificados significativamente más corta.**

Para garantizar que los clientes de ACME puedan renovar sus certificados a tiempo, se recomienda a los usuarios que adopten la Información de Renovación de ACME (ARI), una función diseñada para indicar cuándo es necesaria la renovación. Consulte la documentación de su cliente de ACME para obtener instrucciones sobre cómo habilitar ARI.

Si un cliente no es compatible con ARI, debe garantizar que su intervalo de renovación se ajuste a la validez de 45 días. Por ejemplo, un ciclo de renovación de 60 días haría que los certificados caduquen antes de que se realice la renovación. Una regla segura es renovar aproximadamente dos tercios de la vida útil del certificado (aproximadamente el día 30 para un certificado de 45 días).

**Let's Encrypt desaconseja encarecidamente las renovaciones manuales.** A medida que se reduce la vida útil de los certificados, aumenta la frecuencia de renovación, lo que aumenta la probabilidad de errores humanos, y cualquier descuido podría provocar interrupciones del servicio.



