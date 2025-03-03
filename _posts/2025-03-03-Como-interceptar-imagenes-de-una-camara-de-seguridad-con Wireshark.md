---
title: Cómo interceptar imágenes de una cámara de seguridad con Wireshark
date: 2025-03-03 09:00:00 
categories: [HACKING]
tags: [hacking, vulnerabilidad, ciberataques, ciberseguridad]
description: Cualquier persona con la contraseña de la red puede ver el tráfico que entra y sale de la cámara, lo que permite que un pirata informático intercepte las imágenes de la cámara de seguridad.
image: /assets/117/preview1.png
---

Es habitual que los dispositivos IoT, como las cámaras de seguridad Wi-Fi, alojen un sitio web para controlar o configurar la cámara que utiliza HTTP en lugar del protocolo HTTPS, que es más seguro. Esto significa que cualquier persona con la contraseña de la red puede ver el tráfico que entra y sale de la cámara, lo que permite que un pirata informático intercepte las imágenes de la cámara de seguridad si alguien está viendo la página de visualización HTTP de la cámara.

### Páginas de administración y dispositivos IoT

Una característica que los dispositivos de Internet de las cosas suelen tener en común es la falta de atención a la seguridad. La comodidad suele ser más importante, por lo que detalles como garantizar que la página de administración de un dispositivo sea segura pueden parecer una ocurrencia de último momento para algunos desarrolladores. Como resultado, es común ver que estos dispositivos aparecen en las búsquedas de Nmap con puertos inseguros abiertos. Peor aún, algunos de estos dispositivos están diseñados para estar expuestos directamente a Internet en lugar de solo a la red interna.

En el caso de las cámaras de seguridad, este problema se agrava si la cámara también aloja una página web insegura en la que el propietario puede ver la reproducción de vídeo directamente desde la cámara. Si este es el caso, cualquier otra persona que conozca la contraseña de Wi-Fi puede ver exactamente lo que el objetivo está viendo en la cámara de seguridad. Como la mayoría de las empresas o casas con una cámara tienen un monitor configurado para ver la cámara, esto puede ser una verdadera preocupación para los usuarios con contraseñas débiles u otras personas que comparten la red.

### Los puertos 80 y 81 no son seguros

Al escanear dispositivos con Wireshark , es muy probable que vea algunos puertos abiertos en dispositivos como enrutadores, cámaras de seguridad y otros dispositivos IoT habilitados para Wi-Fi. Si ve un puerto 80, 81, 8080 u 8081, es muy probable que esto signifique que hay un sitio web HTTP inseguro alojado en ese puerto. Si bien debe conocer la contraseña de una red Wi-Fi para escanear estos puertos, puede acceder a ellos a través de la red Wi-Fi para inspeccionar la aplicación web que alojan.

Si bien el puerto 443 se utiliza para el tráfico HTTPS seguro, que está cifrado y no presenta el mismo tipo de riesgo de interceptación, cualquier puerto que exponga un puerto HTTP inseguro en la red local es una invitación para que un atacante husmee en busca de más información sobre el dispositivo conectado. Esto puede significar intentar iniciar sesión, recopilar información sobre el firmware que ejecuta el dispositivo o atacarlo con un programa como RouterSploit para intentar entrar.

Un riesgo menos conocido implica que alguien intercepte contraseñas y otra información a medida que pasa a través de la aplicación web insegura . Si un objetivo ha iniciado sesión y está viendo imágenes de la cámara de seguridad desde una aplicación web insegura en vivo, es relativamente simple interceptar el tráfico web y decodificar los paquetes interceptados en archivos de imagen.

### Interceptar tráfico con Wireshark

Para que esto funcione, necesitaremos usar Wireshark para rastrear el tráfico de Wi-Fi entre nuestra computadora de destino y el enrutador. Nuestro objetivo será capturar el tráfico HTTP no cifrado que fluye hacia la computadora de nuestro objetivo mientras ve la señal de la cámara de seguridad. Sin embargo, para hacer esto, habrá algunas cosas de las que tendremos que ocuparnos primero.

Necesitaremos romper el cifrado de la red. Si conocemos la contraseña, siempre podemos conectarnos a la red nosotros mismos, pero esto abre un riesgo adicional de detección. En lugar de eso, podemos agregar las claves de Wi-Fi que conocemos a Wireshark y descifrar los datos que olemos sin siquiera conectarnos a la red. Esto significa que nuestro ataque será principalmente pasivo, lo que dejará pocas oportunidades de que nos detecten.

Una cosa fundamental que necesitaremos y que no sea pasiva es un protocolo de enlace de Wi-Fi para ver el tráfico. Debido a que Wireshark necesita observar un protocolo de enlace de Wi-Fi para descifrar el tráfico posterior, simplemente conocer la contraseña no es suficiente. Para tener éxito, necesitaremos aislar el tráfico del equipo que nos interesa con un filtro Wireshark, capturar un protocolo de enlace WPA de cuatro vías y luego descifrar los datos con la contraseña que conocemos.

### Lo que necesitarás y limitaciones prácticas

Las condiciones deben ser favorables para que este ataque tenga posibilidades de éxito. En particular, si la cámara no utiliza una interfaz insegura, los datos estarán cifrados y no podremos verlos.

Si nadie está mirando la señal de la cámara o no se muestra en un monitor, no habrá tráfico inseguro que interceptar, por lo que no veremos nada. Si no conocemos la contraseña de la red, no podemos interceptar el tráfico cifrado. Si no podemos expulsar a un cliente de la red momentáneamente para generar un protocolo de enlace de cuatro vías, entonces saber la contraseña no nos servirá de nada. Y, por último, si estamos fuera del alcance de la red, no podremos interceptar el tráfico que no podemos escuchar.

Si bien esto puede parecer una gran cantidad de requisitos, es bastante común poder hacerlo. Si el objetivo tiene una cámara de seguridad Wi-Fi y mantiene un monitor que ve la pantalla, la contraseña de Wi-Fi debería ser todo lo que realmente necesita, además de un adaptador de red inalámbrica compatible con Kali Linux .

Una vez que esté dentro del alcance y tenga Kali Linux cargado, debería estar listo. Conecte su adaptador de red inalámbrica y asegúrese de tener instalado Wireshark para comenzar. Si no tiene Wireshark, puede descargar el instalador desde su sitio web .

### Acceda a la cámara web en la interfaz insegura

Para comenzar, deberá acceder a la interfaz integrada en la cámara web o la cámara de seguridad Wi-Fi que desee interceptar. En una ventana del navegador de su computadora "objetivo", navegue hasta la interfaz HTTP, ingrese la contraseña que se le solicite y luego comience a ver la vista en vivo de la cámara web.

Si necesita encontrar su cámara en la red, puede ejecutar un escaneo Nmap para descubrir diferentes dispositivos en la red que ejecutan puertos HTTP inseguros.

Para este comando, necesitarás saber el rango de red. Puedes encontrarlo escribiendo ifconfig y copiando la dirección IP asignada a tu computadora. Luego, puedes escribir ipcalc y tu dirección IP para calcular el rango de red. Debería ser algo como 192.168.0.0/24. Ejecuta el siguiente comando, sustituyendo 192.168.0.0/24 por tu propio rango de red.

    sudo nmap -p 80,81,8080,8081 192.168.0.0/24

Busque dispositivos que tengan este puerto "abierto" y, cuando encuentre uno, puede navegar hasta él escribiendo la dirección IP y luego :81 para ir al puerto 81 en esa dirección IP. Si desea navegar hasta el puerto 8081 en 192.168.0.1, escriba 192.168.0.1:8081 en la ventana de su navegador.

### Identificar el canal y preparar la tarjeta inalámbrica

Necesitará conectar su adaptador de red inalámbrica compatible con Kali , como el Alfa AWUS036NHA . Deberá hacer dos cosas antes de iniciar Wireshark: la primera es poner la tarjeta en modo de monitor inalámbrico y la segunda es identificar el canal en el que está transmitiendo el enrutador al que apunta.

Para poner la tarjeta en modo de monitor inalámbrico, identifique el nombre de la tarjeta ejecutando ifconfig en una ventana de terminal. Debería tener un nombre similar a wlan0 .

Una vez que haya encontrado el nombre de su tarjeta inalámbrica, necesitaremos ponerla en modo de monitor. Ejecute el siguiente comando en una ventana de terminal, sustituyendo el nombre de su tarjeta por "wlan0".

    airmon-ng start wlan0
    airodump-ng start wlan0mon

Esto pondrá su tarjeta en modo de monitor inalámbrico, cambiando el nombre de la tarjeta para agregar "mon" al final. También iniciará Airodump-ng , que comenzará a escanear en busca de redes inalámbricas cercanas.

Busca la red Wi-Fi que deseas rastrear y toma nota del canal en el que se encuentra. Necesitaremos cambiar nuestra tarjeta a ese canal para interceptar las imágenes en Wireshark.

    CH  4 ][ Elapsed: 0 s ][ 2018-12-24 02:42

     BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
    
     C0:8A:DE:39:CD:D9  -46        2        0    0   1  130  WPA2 CCMP   MGT  TWCWiFi-Passpoint
     C0:8A:DE:F9:CD:D8  -47        2        0    0   1  130  OPN              TWCWiFi
     C0:8A:DE:B9:CD:D8  -46        2        0    0   1  130  OPN              SpectrumWiFi
     C0:8A:DE:39:CD:D8  -47        2        0    0   1  130  OPN              CableWiFi
     78:96:84:00:B5:B0  -42        2        0    0   1  130  WPA2 CCMP   PSK  The Daily Planet
     00:9C:02:D2:5E:B9  -60        3        0    0   1  54e. WPA2 CCMP   PSK  HP-Print-B9-Officejet Pro 8600
     20:10:7A:92:76:43  -51        2        0    0   1  130  WPA2 CCMP   PSK  SBG6580E8
     DE:F2:86:EC:CA:A0  -45        1        0    0  11  195  WPA2 CCMP   PSK  Bourgeois Pig Guest
     D6:04:CD:BD:33:A1  -55        1        0    0  11  130  WPA2 CCMP   PSK  DirtyLittleBirdyFeet
    
     BSSID              STATION            PWR   Rate    Lost    Frames  Probe
    
    root@kali:~/Desktop#

Si nuestro objetivo está en el canal 11, ejecutaremos el siguiente comando para configurar nuestra tarjeta en el canal 11.

    airmon-ng start wlan0mon 11

### Iniciar Wireshark

Ahora que nuestro adaptador de red inalámbrica está escuchando en el mismo canal que el tráfico que queremos interceptar, es momento de iniciar Wireshark. Cuando Wireshark se abra, haga doble clic en la tarjeta que puso en modo de monitor para iniciar la captura.

![Imagen 01](/assets/117/117-01.png)

Nuestra tarjeta debería estar escaneando en el canal correcto, pero sin la contraseña de red, no podremos ver nada. Para solucionarlo, necesitaremos agregar algunas claves de cifrado a Wireshark.

### Agregue la contraseña de red para descifrar el tráfico

Para agregar claves de cifrado a Wireshark, haga clic en "Editar" en la barra de menú y luego en "Preferencias" para mostrar el menú de preferencias. A continuación, seleccione "Protocolos" en la barra lateral para ver una lista de protocolos que Wireshark puede traducir.

![Imagen 01](/assets/117/117-02.png)

En el menú desplegable Protocolos que acaba de abrir, deberá seleccionar "IEEE 802.11" para mostrar las opciones para descifrar el Wi-Fi. Asegúrese de que la casilla "Habilitar descifrado" esté marcada y, luego, haga clic en el botón "Editar" junto a "Claves de descifrado" para abrir la lista de claves que Wireshark intentará usar para descifrar el tráfico.

![Imagen 01](/assets/117/117-03.png)

Una vez abierto el menú de claves de descifrado WEP y WPA, haga clic en el campo de la izquierda y seleccione "wpa-psw" para agregar. Si bien también podemos agregar aquí un "wpa-psk", tendríamos que calcularlo nosotros mismos, lo que es más complicado que simplemente ingresar la contraseña.

![Imagen 01](/assets/117/117-04.png)

Para que el descifrado funcione, debe agregar la clave haciendo clic en el ícono más (+) y luego ingresar la clave en el formato contraseña:nombredered para agregarla a la lista.

![Imagen 01](/assets/117/117-05.png)

Haga clic en "Aceptar" para guardar la clave y ahora deberíamos poder descifrar el tráfico de esta red, si podemos lograr un protocolo de enlace Wi-Fi de cuatro vías.

### Crea un filtro para capturar el tráfico entre dispositivos

En nuestra captura de Wireshark, seguramente veremos mucho tráfico. Si bien aún no podemos descifrarlo porque no tenemos un protocolo de enlace, podemos crear un filtro para asegurarnos de que solo veamos tráfico hacia el dispositivo que estamos rastreando.

La mejor manera de hacer esto en una red Wi-Fi es encontrar un segmento de tráfico hacia la computadora que estamos buscando y luego crear un filtro de visualización para mostrar solo los paquetes que se dirigen a esa dirección MAC. Eso significa que se mostrará todo el tráfico dirigido a la computadora de destino y se ignorará cualquier otro tráfico de red.

En la información del paquete, haga clic con el botón derecho en la "Dirección del receptor" del paquete que se va a enviar al dispositivo de destino, seleccione "Aplicar como filtro" y, luego, "Seleccionado". Ahora, deberíamos ver solo los paquetes destinados al destino.

![Imagen 01](/assets/117/117-06.png)


### Desacredita al objetivo para conseguir un apretón de manos

Ahora que hemos aislado el tráfico de nuestro dispositivo de destino, necesitamos generar un protocolo de enlace de cuatro vías expulsando la computadora de destino de la red momentáneamente mientras Wireshark está escuchando. Para hacer esto, podemos usar una herramienta de una guía anterior llamada MDK3 , que puede expulsar cualquier dispositivo conectado a Wi-Fi y generar un protocolo de enlace.

Como ya conocemos el canal en el que se encuentra nuestra red Wi-Fi, podemos usar MDK3 para eliminar cualquier dispositivo que opere en ese canal. No debería llevar mucho tiempo generar un protocolo de enlace WPA. Con "wlan0mon" intercambiado por el nombre de su tarjeta inalámbrica y "11" intercambiado por el canal que está atacando, ejecute el siguiente comando en una ventana de terminal para comenzar a bloquear la red.

    mdk3 wlan0mon d -c 11

Después de unos momentos, los dispositivos cercanos en la red deberían reconectarse automáticamente, lo que te permitirá interceptar el protocolo de enlace WPA de cuatro vías. Si quieres asegurarte de que lo tienes, puedes abrir una nueva ventana de terminal y ejecutar Airodump-ng para ver cuándo recibes un protocolo de enlace WPA.

Para ello, escriba airodump-ng wlan0mon 11 (sustituyendo "wlan0mon y "11" por los valores reales) para observar los protocolos de enlace WPA mientras ejecuta MDK3.

![Imagen 01](/assets/117/117-07.png)

Una vez que veas el resultado anterior, habrás capturado un protocolo de enlace de cuatro vías WPA. Asegúrate de que la dirección MAC que se muestra coincida con la red inalámbrica a la que te diriges para evitar obtener un protocolo de enlace para la red incorrecta.

Ahora que tenemos un protocolo de enlace de cuatro vías y hemos ingresado la clave de red, deberíamos tener acceso total a los datos que fluyen por la red. Si bien el protocolo HTTPS aún no está disponible, deberíamos poder ver el protocolo HTTP sin procesar sin problemas.

### Filtrar el tráfico para encontrar tráfico HTTP

Si bien obtuvimos acceso al tráfico de red y lo redujimos al equipo de destino, puede haber otro tráfico que no esté relacionado y que dificulte enfocarnos en lo que estamos buscando. Para evitarlo, agregaremos otro filtro de red para mostrar solo el tráfico HTTP que fluye en la red.

En la vista principal de Wireshark, escriba http en la barra de filtro de visualización.

![Imagen 01](/assets/117/117-08.png)

Esto solo permitirá que se muestre el tráfico HTTP que se envía a la computadora que estamos monitoreando, lo que filtrará aún más nuestra vista hasta que solo veamos el tráfico hacia nuestra aplicación web insegura. Ahora, necesitaremos decodificar los paquetes interceptados en imágenes para poder ver lo que nuestro objetivo está viendo desde la cámara de seguridad.

### Decodificar, exportar y visualizar los archivos JPEG interceptados

Ahora que podemos ver el tráfico HTTP desde la aplicación web, tendremos que seleccionar los archivos JPEG codificados para convertirlos en algo con lo que podamos trabajar. Detenga la captura y haga clic en "Archivo" y, luego, en "Exportar objetos". Exportaremos los objetos HTTP que encontramos, así que haga clic en "HTTP" para abrir la lista de objetos.

![Imagen 01](/assets/117/117-09.png)

En la lista de objetos HTTP, veremos una lista de los objetos HTTP que hemos interceptado. Aquí podemos ver las imágenes JPEG que queremos decodificar. Puedes seleccionar una o todas ellas y, a continuación, hacer clic en "Guardar" o "Guardar todo" y elegir una ubicación a la que exportar los archivos.

![Imagen 01](/assets/117/117-10.png)

Haga clic en "Cerrar" y luego navegue hasta la carpeta a la que exportó las imágenes. Debería ver una lista de archivos que Wireshark exportó de nuestra captura. Esto será más o menos así según el tiempo durante el que haya ejecutado la captura.

![Imagen 01](/assets/117/117-11.png)

Por último, haz clic en una de las imágenes para ver la imagen que fue interceptada en el camino hacia la computadora de destino. ¡Deberías ver un fotograma de la transmisión de video!

![Imagen 01](/assets/117/117-12.png)

### Defendiendose del ataque

La mejor manera de asegurarse de que nadie esté espiando la señal de su cámara de seguridad es asegurarse de que su cámara esté usando HTTPS, tenga una contraseña segura configurada y esté en una red con la que no comparta abiertamente la contraseña. Debido a que una contraseña de Wi-Fi débil puede dar a un atacante acceso directo a la aplicación web, es fundamental que proteja su red Wi-Fi con una contraseña segura y desactive opciones como la configuración de WPS en su enrutador que permite eludir otras funciones de seguridad.

Espero que hayas disfrutado de esta guía para interceptar imágenes de cámaras de seguridad con Wireshark.





