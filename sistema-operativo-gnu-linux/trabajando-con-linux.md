# Trabajando con Linux

Se recomienda que trabajéis en aula con los PCs de los laboratorios del DSIC que permiten cargar máquinas virtuales remotas basadas en GNU/Linux. Desde casa es posible trabajar con las mismas máquinas remotas desde vuestros equipos de casa.

1. **Uso de escritorios remotos UPV**:
   * [**Polilabs**](https://polilabs.upv.es/uds/page/login): Seleccionar "DSIC-LINUX" (basado en CentOS).
     * Desde la red UPV se accede directamente
     * En caso de conectar desde casa, probablemente sea necesario [conectarse a la VPN de la UPV](http://www.upv.es/contenidos/INFOACCESO/infoweb/infoacceso/dat/697481normalc.html).

{% hint style="danger" %}
Nota: debéis tener la precaución de trabajar **siempre** en vuestra unidad W, de lo contrario, corréis el riesgo de perder ficheros e información.&#x20;
{% endhint %}

***

Como alternativa se puede disponer de un entorno de trabajo similar al de laboratorio que os permita trabajar, mediante un equipo propio que ya tenga instalado un sistema operativo basado en GNU/Linux, entonces podéis considerar las siguientes opciones:

1. **Virtualización del SO Linux en vuestro PC (portátil)**
   *   [**Windows Subsystem for Linux**](https://learn.microsoft.com/es-es/windows/wsl/install) **(WSL)**: herramienta oficial de Windows que permite instalar y ejecutar una máquina virtual sobre el que corre el sistema operativo GNU/Linux deseado (sin interfaz gráfica, solo terminal). **Esta es la opción más sencilla y rápida.**&#x20;

       * [Instrucciones de instalación aquí](https://learn.microsoft.com/es-es/training/modules/wsl-introduction/install-and-setup). Por defecto, instalará una Ubuntu 22.04 LTS (justo lo que recomendamos).  Esto os creará una aplicación del sistema denominada "Ubuntu".
       * En caso de tener problemas, consultad esta sección de [resolución de problemas frecuentes.](https://learn.microsoft.com/es-es/windows/wsl/troubleshooting)
       * Dentro de la terminal bash de Ubuntu, podeis encontrar el sistema de ficheros de Windows en el directorio `/mnt/c`. Si buscáis vuestro directorio personal de Windows, estará en `/mnt/c/Users/<MI_USUARIO>`(sustituye `<MI_USUARIO>` por tu nombre de usuario de Windows).&#x20;


   *   **Máquina virtual**: usando software de virtualización de sistemas operativos (p.ej., [Virtualbox](https://www.virtualbox.org/)), podemos instalar virtualmente cualquier SO (incluyendo interfaz gráfica) dentro de nuestro sistema operativo anfitrión, como si se tratara de una aplicación más del sistema.&#x20;

       * Esto nos abre un sinfín de posibilidades: ejecutar Linux dentro de Windows, ejecutar Windows dentro de Linux, ejecutar MacOS dentro de Windows, etc.&#x20;
       * Descargar Virtualbox [aquí](https://download.virtualbox.org/virtualbox/7.0.10/VirtualBox-7.0.10-158379-Win.exe).
       * Además, deberéis descargaros la imagen ISO del sistema operativo Ubuntu Desktop LTS.
         * [Ubuntu Desktop LTS](https://ubuntu.com/download/desktop), con interfaz gráfica. Requisitos mínimos:
           * 1 x CPU 2Ghz.
           * **4GB RAM.**
           * 25GB de espacio en disco.
       * [Tutorial de instalación de Ubuntu con Virtualbox](https://discourse.ubuntu.com/t/how-to-run-an-ubuntu-desktop-virtual-machine-using-virtualbox-7/25137).
       * Si decidís instalar la versión Desktop (con interfaz gráfica), recomendamos instalar las "Guest Additions" de Virtualbox, para una mejor integración del SO virtual con el SO real. Entre otras cosas, os permitrá montar el sistema de ficheros de Windows dentro de la Ubuntu virtualizada. [Aquí un](https://www.linuxtechi.com/install-virtualbox-guest-additions-on-ubuntu/)[ tutorial sobre cómo hacerlo](https://www.linuxtechi.com/install-virtualbox-guest-additions-on-ubuntu/).&#x20;


2. **Instalación física del SO Linux en vuestro PC (portátil)**
   * Si esta opción os resulta interesante, tened en cuenta que es posible [una instalación con arranque dual Windows + Linux](https://www.xataka.com/basics/como-instalar-gnu-linux-a-windows-11-ordenador).
   * La información sobre la descarga de las imágenes ISO de Ubuntu 22.04 LTS la tenéis en el ítem 2 (Virtualización del SO Linux en vuestro PC).

{% hint style="info" icon="thumbs-up" %}
Nuestra recomendación es virtualizar el sistema operativo Ubuntu 22.04 en vuestro sistema anfitrión Windows.&#x20;

* La opción más rápida y sencilla es apostar por WSL.&#x20;
* Si no, Virtualbox + Ubuntu XX LTS.
{% endhint %}
