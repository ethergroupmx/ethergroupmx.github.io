---
title: "eBPF: observabilidad sin sobrecarga en Linux"
date: 2026-02-06 09:00:00 
categories: [LINUX]
tags: [linux, servidores, software libre]
description: La monitorización con eBPF está revolucionando la seguridad y gestión en servidores Linux. eBPF permite que se puedan ejecutar programas seguros dentro del kernel de Linux para obtener una visibilidad profunda y en tiempo real. 
image: /assets/217/preview1.png
---

**eBPF es una tecnología que permite ejecutar programas personalizados de forma segura dentro del kernel de Linux sin necesidad de modificar el código fuente o reiniciar el sistema.** Se utiliza principalmente para observar el rendimiento, filtrar tráfico de red y fortalecer la seguridad del sistema mediante el análisis de eventos en tiempo real. En la actualidad, los sysadmins usan eBPF para optimizar la observabilidad, seguridad y rendimiento operativo.

---

### Por qué eBPF cambia las reglas del juego

Si llevas tiempo en esto, sabes que la monitorización siempre ha sido un compromiso. O instalabas agentes pesados que te daban mucha información pero consumían CPU y memoria como si no hubiera un mañana, o te conformabas con métricas superficiales para no lastrar el rendimiento. Con eBPF, esta dicotomía empieza a difuminarse. La idea de poder engancharse directamente al kernel y observar lo que pasa, sin intermediarios, es simplemente revolucionaria.

Ya no hablamos de un agente que se ejecuta como un proceso más, compitiendo por recursos. Hablamos de pequeños programas verificados que se ejecutan en un entorno seguro dentro del propio kernel, como una extensión nativa del sistema operativo. Es pasar de tener un espía siguiendo a un objetivo (con el riesgo de que lo descubran y de que haga ruido) a ser el propio suelo que pisa el objetivo, sintiendo cada uno de sus pasos.

Los agentes de monitorización tradicionales, ya sean para APM (Application Performance Monitoring) o para métricas de sistema, funcionan en el espacio de usuario. Esto significa que, para obtener datos del kernel (como llamadas al sistema, operaciones de red o accesos a disco), necesitan realizar constantes cambios de contexto (de espacio de usuario a espacio de kernel y viceversa). Cada uno de estos saltos, aunque pequeños, suma y genera una sobrecarga. Si lo multiplicas por miles de eventos por segundo en un servidor concurrido, el overhead se vuelve tangible.

eBPF invierte este modelo. En lugar de un agente pesado, cargas «sondas» o programas eBPF extremadamente ligeros y específicos para lo que necesitas.

- ¿Solo quieres ver la latencia de las consultas DNS? Cargas un programa eBPF que se engancha a las funciones sendto y recvfrom en el socket correspondiente.
- ¿Necesitas rastrear qué proceso está abriendo un fichero de configuración específico? Enganchas una sonda a la llamada al sistema openat.

Estos programas se compilan a un bytecode que es verificado por el kernel antes de cargarse. Este verificador es como un portero de discoteca extremadamente estricto: se asegura de que el programa no pueda caer en bucles infinitos, no acceda a memoria no autorizada ni pueda, en definitiva, colgar el sistema. Una vez aprobado, el JIT (Just-In-Time) compiler del kernel lo traduce a código máquina nativo, haciéndolo increíblemente rápido. El resultado es una monitorización con un impacto en el rendimiento casi nulo, a veces estimado en menos del 1%.

eBPF soluciona esto con el Verificador. Antes de que un programa eBPF se cargue y se enganche a un evento del kernel, pasa por un proceso de análisis estático extremadamente riguroso.

Si has investigado sobre eBPF antes de, digamos, 2020, probablemente leíste sobre la pesadilla de tener que recompilar tus programas eBPF para cada versión específica del kernel. Ese infierno se acabó gracias a una cosa llamada BTF (BPF Type Format) y el concepto que habilita: CO-RE (Compile Once – Run Everywhere).

La buena noticia es que, a día de hoy, en 2026, eBPF ya no es una rareza exótica. Es una tecnología madura y soportada por todas las distribuciones Linux serias. Sin embargo, no todas las «experiencias eBPF» son iguales, y el diablo, como siempre, está en los detalles de la versión.

- **Kernel Linux**: El soporte sólido para BTF empezó a tomar forma alrededor del kernel 5.2, pero se ha ido puliendo mucho desde entonces. Para una experiencia sin sobresaltos, cualquier kernel 5.8 o superior es una apuesta segura.
- **Ubuntu**: Desde la versión 20.10 en adelante, Ubuntu incluye BTF por defecto. En la última LTS, Ubuntu 24.04, el soporte es de primera clase.
- **RHEL** y derivados (CentOS Stream, Rocky Linux, AlmaLinux): A partir de RHEL 8.2, se empezó a incluir el soporte BTF. En RHEL 9 y sus clones, es una característica estándar y robusta.
- **Debian**: Debian habilitó BTF por defecto a partir de la versión 11 («Bullseye»).
- **SLES** (SUSE Linux Enterprise Server): SLES 15 SP3 y versiones posteriores también vienen con soporte BTF de serie.

Ya hemos visto el «porqué», ahora vamos a meternos en el fango y ver el «cómo» funciona esto por dentro. Para usar eBPF de verdad y no solo recitar conceptos, hay que entender sus piezas fundamentales.

Te dejamos un link con más información a detalle: [eBPF revoluciona la monitorización: Observabilidad sin overhead en servidores Linux](https://www.sysadminok.es/blog/ciberseguridad/ebpf-revoluciona-la-monitorizacion-observabilidad-sin-overhead-en-servidores-linux/)


