---
title: "ViKing: la IA que puede convertirse en un atacante autónomo de Vishing"
date: 2025-09-16 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, hacking, vishing]
description: Imagina recibir una llamada de tu jefe, de un compañero de trabajo o incluso de un familiar, donde cada palabra parece verosímil, cada pausa natural, y cada argumento persuasivo perfectamente calculado para que reveles información sensible.
image: /assets/167/preview1.png
---

Ahora imagina que del otro lado no hay nadie, solo un agente conversacional autónomo, capaz de mantener una conversación coherente, adaptativa y manipuladora. Este es el escenario que plantea ViKing, un sistema de vishing completamente automatizado descrito en un reciente paper de arXiv.

![Imagen 01](/assets/167/167-01.png)

### ViKing combina tres componentes fundamentales:

- **Modelo de lenguaje grande (LLM):** el núcleo cognitivo que genera las respuestas en tiempo real, adaptándose al flujo de la conversación, interpretando la información de la víctima y ajustando la persuasión según las reacciones detectadas.
- **Conversión de texto a voz (TTS):** transforma las respuestas del LLM en audio natural, con entonaciones que simulan patrones humanos de conversación, pausas y énfasis en palabras clave para aumentar la credibilidad.
- **Reconocimiento de voz (STT):** transcribe las respuestas de la víctima para que el LLM pueda analizarlas y decidir la siguiente acción, cerrando así el ciclo de comunicación autónoma.

Este flujo convierte a ViKing en un agente autónomo de ingeniería social, capaz de replicar y superar, en términos de consistencia y escala, a operadores humanos de fraude telefónico.

![Imagen 01](/assets/167/167-02.png)

### Evaluación de efectividad: datos que asustan

El paper documenta un experimento con 240 participantes simulando empleados de una empresa ficticia, y los resultados son reveladores:

- Más de la mitad de los participantes (52%) compartieron información sensible.
- 68,3% consideraron las interacciones creíbles, mientras que 62,9% las percibieron como realistas.
- El costo por interacción exitosa varió entre $0,38 y $1,13, lo que demuestra la escalabilidad económica de un ataque totalmente automatizado.

Para un investigador en ciberseguridad, estos números representan una llamada de atención: los ataques de vishing automatizados no solo son posibles, sino que pueden ser eficaces, baratos y difíciles de detectar.

Además desde un punto de vista técnico, ViKing es especialmente preocupante por varias razones:

- **Escalabilidad:** a diferencia de los operadores humanos, un sistema automatizado puede realizar **miles de llamadas simultáneamente,** ajustando la narrativa de manera dinámica según la respuesta de la víctima.
- **Reducción de barreras de entrada:** con modelos LLM de acceso abierto, actores maliciosos con conocimientos básicos podrían replicar ataques sofisticados sin experiencia avanzada en ingeniería social.
- **Adaptabilidad y aprendizaje:** el modelo puede optimizar sus estrategias a partir de interacciones pasadas, refinando técnicas de persuasión y adaptando el guion al contexto de cada víctima.
- **Difícil detección:** la combinación de prosodia natural en TTS y respuestas contextualmente adaptativas hace que distinguir entre humano y bot sea extremadamente complicado, incluso para sistemas de detección avanzados.

Y ahora imagina un sistema autónomo como ViKing **combinado con las capacidades de clonación de voz (deepfake) actuales...** Ya existen casos de vishing con clonación de voz, y ya ha generado pérdidas significativas. Sin embargo, la combinación totalmente autónoma de clonación de voz + un agente conversacional adaptativo aún es incipiente, aunque ViKing demuestra que el siguiente paso (conversación totalmente adaptativa) es técnicamente viable.

En definitiva, ViKing demuestra por ende que los ataques de ingeniería social están entrando en una nueva era. La IA ya no es solo una herramienta de automatización pasiva; puede convertirse en un actor autónomo y persuasivo, capaz de escalar ataques con una eficacia y bajo coste que ningún operador humano podría igualar.
Para la comunidad de seguridad, esto plantea un desafío doble: comprender y anticipar el comportamiento de agentes maliciosos basados en IA, y desarrollar defensas que puedan proteger la información sensible de individuos y organizaciones antes de que estos ataques se vuelvan ubicuos.

En pocas palabras: la inteligencia artificial está empezando a atacar la inteligencia humana, y la seguridad tradicional podría no ser suficiente para detenerla...




