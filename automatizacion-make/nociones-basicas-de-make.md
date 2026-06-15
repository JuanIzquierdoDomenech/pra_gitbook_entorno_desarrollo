# Nociones básicas de Make

La herramienta Make se fundamenta en los denominados ficheros _Makefile_, que contienen, principalmente, una serie de reglas u objetivos compilación, las cuales especifican cómo se debe compilar el proyecto para poder instalarlo, distribuirlo, o simplemente ejecutarlo.&#x20;

## Reglas / objetivos

Una regla u objetivo en el archivo _Makefile_ indica a Make **qué comandos debe ejecutar para crear un archivo de destino (compilado) a partir de una serie de archivos de entrada**. Estos archivos de entrada se denominan **dependencias**, y pueden ser archivos fuente (p.ej., ficheros `.cpp`, `.c`, `.h`, etc.), o archivos de destino generados por otras reglas (p.ej., ficheros de código objeto `.o`).&#x20;

Una regla Make tiene el siguiente aspecto:&#x20;

```make
<OBJETIVO>: [<DEPENDENCIA1>, <DEPENDENCIA2>, ... ]
    <COMANDO1>
    <COMANDO2>
    ....
```

Donde `<OBJETIVO>` es el fichero de destino (fichero binario o compilado), y `<DEPENDENCIA1>`, `<DEPENDENCIA2>`, etc. son el conjunto de ficheros de entrada necesarios para generar el fichero de destino.&#x20;

{% hint style="warning" %}
Los comandos deben aparecer "indentados" en el fichero _Makefile_ mediante un **tabulador (tecla TAB)**, en lugar de espacios en blanco. Si no usáis tabulador, o bien los comandos no están indentados, os aparecerá el error _"missing separator"._
{% endhint %}

Un ejemplo sencillo de regla Make sería el siguiente:

```makefile
a.out: main.cpp
    g++ main.cpp
```

Definimos como objetivo la generación de un ejecutable binario `a.out`. Este depende de un fichero fuente denominado `main.cpp`, que contiene el código de una función `main()` ejecutable. Para poder generarlo, se debe invocar el comando `g++ main.cpp`, el cual genera por defecto, como sabemos, el fichero binario ejecutable `a.out`.&#x20;

## Selección y ejecución de reglas

La herramienta Make se lanza mediante la invocación, en la terminal, del comando `make`, sobre un directorio en el que existe un fichero `Makefile`. En su invocación, se pueden especificar objetivos particulares para actualizar (en el ejemplo anterior, podría ser: `make a.out`). Si no se especifica, Make actualiza el primer objetivo que aparece en el archivo _Makefile_. En general, el primer objetivo suele implicar la compilación todo el proyecto (ver [convención `all`](nociones-basicas-de-make.md#convenciones)).

Una vez seleccionado el objetivo inicial, Make evalúa la lista de dependencias para determinar si debe actualizar el archivo de destino o no.&#x20;

1. En primer lugar, para cada una de las dependencias que sean un fichero destino (compilado), comprueba si es necesario regenerarlas, examinando su regla correspondiente, y ejecuta los comandos pertinentes en caso necesario.
2. A continuación, comprueba la fecha de modificación del fichero destino de la regla. Si el archivo de destino es más reciente que todas sus dependencias, entonces significa que está actualizado y por tanto no es necesario volver a generarlo. Si es más antiguo que alguna de las dependencias, o bien no existe, entonces se deben ejecutar los comandos de la regla para actualizarlo.

## Convenciones

Típicamente, por convención, se utilizan los siguientes objetivos que no estan asociados a ficheros del proyecto, para los fines correspondientes:

* **`all`**: compila todo el proyecto. De hecho, una de las formas más comunes de invocar make es: `make all`. Si regla de destino `all`, si está presente, se suele proporcionar como la primera regla en el archivo _Makefile_. Entonces, si se invoca el comando `make` sin ningún objetivo, ejecutará la regla `all`.
* **`clean`**: elimina (limpia) los ficheros destion (binarios), así como archivos temporales o intermedios del proceso de compilación del proyecto, dejando únicamente los ficheros fuente del proyecto.
* **`install`**: en los programas que deben "instalarse" colocándolos en directorios especiales del sistema, este objetivo controla los comandos necesarios para realizar esa instalación.&#x20;
* **`test`**: lanza un conjunto de pruebas para comprobar que el software compilado funciona correctamente. Suele tener el objetivo `all` como dependencia.
