# Nociones básicas de la Terminal

## Directorio de trabajo (working directory)

Una terminal tiene asociado un directorio de trabajo, que viene a ser básicamente el directorio del sistema de archivos en el que nos encontramos. Por defecto, cuando abrimos una nueva terminal Bash, el directorio de trabajo inicial es el directorio del usuario del sistema, o más comúnmente denominado directorio _home_ (casa) del usuario. Si, por ejemplo, nuestro nombre de usuario en el sistema es `maripili`, entonces el directorio de trabajo inicial es `/home/maripili` (variable de entorno `$HOME`). A partir de dicho directorio podemos realizar multitud de operaciones con ficheros, descargar archivos de internet, ejecutar programas, etc.

{% hint style="info" %}
En la terminal, podéis consultar en cualquier momento cuál es el directorio de trabajo actual, invocando el comando **`pwd`** (ver sección [Comandos básicos](comandos-basicos.md)).
{% endhint %}

## Rutas (_Paths_) de directorios y ficheros

Muchos de los comandos que vamos a utilizar requieren uno o varios directorios o ficheros como argumentos. En general, hablaremos de rutas (paths) a directorios o ficheros, que pueden ser:

* **Relativas** al directorio de trabajo actual: p.ej., `PRA/p0` (directorio), `PRA/README.txt` (fichero).
* **Absolutas** en el sistema de ficheros: p.ej., `/home/maripili/PRA/p0` (directorio), `/home/maripili/PRA/README.txt` (fichero).

Cuando especificamos rutas relativas, podemos hacer uso de las siguientes referencias:

* **Referencia `..`** al directorio superior. Por ejemplo:
  * `../test.cpp`: apunta al fichero `test.cpp` ubicado en el directorio superior.
  * `../../../`: apunta al directorio que se encuentra tres niveles por encima del directorio de trabajo actual.
  * `../../source/app.cpp` &#x20;
* Una **referencia `.`** al directorio actual. Por ejemplo:
  * `./test.cpp`: apunta al fichero **test.cpp** ubicado en el directorio actual.&#x20;
  * `./PRA`: apunta al subdirectorio `PRA` ubicado en el directorio actual.
  * `./main`: apunta al fichero `main` ubicado en el directorio actual. Si `main` es un fichero ejecutable, al escribir `./main` en la terminal se ejecuta dicho fichero.

{% hint style="warning" %}
**Evitad usar espacios en blanco para nombrar directorios y ficheros.** De lo contrario, tendréis que "escapar" los espacios en blanco, o bien usar comillas simples/dobles, lo cual es extremadamente engorroso y suele ser una fuente de errores absurdos evitables. Usad guión `-` _(dash)_ o guión bajo `_` _(underscore)_ como alternativas al espacio en blanco. P.ej., `"implementacion_super_eficiente.cpp"`.
{% endhint %}

{% hint style="info" %}
Como regla general, se recomienda usar el conjunto de caracteres: `{a-z, A-Z, 0-9, _, -} para nombrar ficheros y directorios.`
{% endhint %}

## Variables de entorno

La terminal bash proporciona una serie de variables de entorno globales y de usuario. Las variables de entorno son pares `nombre-variable = valor-variable` que tienen la capacidad de alterar el funcionamiento de los programas del sistema operativo que las consultan. Para acceder a ellas, se debe utilizar el carácter `$` (dólar) delante del identificador de la variable. Algunas variables de entorno relevantes y predefinidas en sistemas GNU/Linux son:

* **`$HOME`**: contiene la ruta absoluta al directorio home del usuario. P.e. `/home/maripili`.
* **`$SHELL`**: muestra el shell usado por el usuario (p.ej., bash, zsh...).
* **`$USER`**: contiene el nombre de usuario del usuario del sistema que está ejecutando la terminal o el proceso correspondiente, como podría ser `maripili`.
* **`$PATH`**: Esta variable contiene una lista de directorios separados por dos puntos (:) en los que el sistema busca ficheros ejecutables (programas). Cuando se invoca un comando en la terminal, el shell busca dicho comando en los diferentes directorios mencionados en la variable `$PATH`. Si se encuentra el comando, se ejecuta. De lo contrario, devuelve el error "comando no encontrado".

{% hint style="info" %}
En la terminal, podéis inspeccionar el contenido de estas variables de entorno usando el comando `echo`. Por ejemplo: **`echo $HOME`**
{% endhint %}
