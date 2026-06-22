---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Ejercicio: primer proyecto con Makefile

## Instalación de Make

Antes de nada, por si no tienes instalada la herramienta Make en tu sistema operativo, aquí tienes las (breves) instrucciones de instalación:

{% hint style="info" %}
Puedes ejecutar el comando `which make` para comprobar si la herramienta está instalada en tu sistema.
{% endhint %}

{% tabs %}
{% tab title="Debian/Ubuntu" %}
<pre class="language-bash"><code class="lang-bash">sudo apt update
<strong>sudo apt install make
</strong></code></pre>
{% endtab %}

{% tab title="Fedora" %}
```bash
sudo dnf install make
```
{% endtab %}

{% tab title="MacOS" %}
1. Instalar XCode desde la App Store.
2. Abrir una terminal y ejecutar:&#x20;

```bash
xcode-select --install
```
{% endtab %}
{% endtabs %}

***

## Inicialización del proyecto&#x20;

Vamos a crear un proyecto sencillo tipo Hello World con un Makefile. Este proyecto constará, por un lado, de una librería denominada `helloPRA` con una función `std::string say()`, y por otro lado, de dos programas ejecutables `app1` y `app2`, los cuales se enlazarán con la librería `helloPRA`.&#x20;

Crea un directorio para el proyecto, accede a él, y crea con Vim los siguientes cuatro ficheros de código fuente (.cpp y .h):&#x20;

{% tabs %}
{% tab title="helloPRA.h" %}
```cpp
#include <string>

std::string say();
```
{% endtab %}

{% tab title="helloPRA.cpp" %}
```c++
#include "helloPRA.h"

std::string say(){
    return "Hello PRA!";
}
```
{% endtab %}

{% tab title="app1.cpp" %}
```cpp
#include <iostream>
#include "helloPRA.h"

int main(){
     std::cout << "(App1): " << say() << std::endl;
     return 0;
}
```
{% endtab %}

{% tab title="app2.cpp" %}
```cpp
#include <iostream>
#include "helloPRA.h"

int main(){
     std::cout << "(App2): " << say() << std::endl;
     return 0;
}
```
{% endtab %}
{% endtabs %}

***

## Diseño del Makefile

El siguiente paso es pensar cómo se debería compilar este proyecto por fases, para determinar todos los ficheros que se generarán, y con ello, establecer las reglas del _Makefile_ y sus dependencias. En concreto, se generarán 5 ficheros destino:

1. La compilación del fichero `helloPRA.cpp` generará un fichero de código objeto **`helloPRA.o`** :
   * `g++ -c helloPRA.cpp`
2. La compilación del fichero `app1.cpp` generará un fichero de código objeto **`app1.o`**:
   * `g++ -c app1.cpp`
3. La compilación del fichero `app2.cpp` generará un fichero de código objeto **`app2.o`**:
   * `g++ -c app2.cpp`
4. Enlazando los ficheros `app1.o` y `helloPRA.o` generaremos el ejecutable **`app1`**:
   * `g++ -o app1 app1.o helloPRA.o`
5. Enlazando los ficheros `app2.o` y `helloPRA.o` generaremos el ejecutable **`app2`**:
   * `g++ -o app2 app2.o helloPRA.o`

Por tanto, debemos implementar 5 reglas en el _Makefile_, tantas como ficheros destino se deben crear.&#x20;

***

## Implementación del Makefile

Empezamos implementando la regla del fichero destino **`helloPRA.o`**. Sus dependencias son el fichero de código fuente `helloPRA.cpp` y el fichero de cabecera `helloPRA.h`. Ambos son considerados archivos fuente: esto significa que cualquier modificación de alguno de estos dos ficheros dispararía necesariamente la regla. Por tanto, quedaría así:

```makefile
helloPRA.o: helloPRA.cpp helloPRA.h
    g++ -c helloPRA.cpp
```

{% hint style="warning" icon="face-sad-tear" %}
Recordad: los comandos deben aparecer indentados en el fichero _Makefile_ mediante un **tabulador (tecla TAB)**, en lugar de espacios en blanco. Si no usáis tabulador, o bien los comandos no estan indentados, os aparecerá el error _"missing separator"._
{% endhint %}

Las reglas de los ficheros destino **`app1.o`** y **`app2.o`** son muy similares. Ambas requieren el fichero de cabeceras `helloPRA.h`, además de sus respectivos ficheros de código fuente. Quedarían así:

```makefile
app1.o: app1.cpp helloPRA.h
        g++ -c app1.cpp

app2.o: app2.cpp helloPRA.h
        g++ -c app2.cpp
```

Nos faltarían las reglas de los ficheros destino **`app1`** y **`app2`**, es decir, los binarios ejecutables. Estos dependen única y exclusivamente de los ficheros de código objeto `app1.o`/`app2.o` y `helloPRA.o` cuyas reglas acabamos de definir. Esto significa, por transitividad, que cualquier modificación de los ficheros fuente `helloPRA.h` y/o `helloPRA.cpp`, o bien de `app1.cpp` o `app2.cpp`, dispararía necesariamente estas reglas. Por tanto:

```makefile
app1: app1.o helloPRA.o
        g++ -o app1 app1.o helloPRA.o

app2: app2.o helloPRA.o
        g++ -o app2 app2.o helloPRA.o
```

Para terminar, añadiremos tres reglas que nos pueden resultar útiles, siguiendo las [convenciones](nociones-basicas-de-make.md#convenciones):&#x20;

* **`all`**: para compilar todo el proyecto. Dependerá de los objetivos `app1` y `app2`, sin más. La situaremos arriba del todo, para que sea el objetivo/regla por defecto.
* **`clean`**: para eliminar código objeto y binarios ejecutables. No tendrá dependencias, y simplemente invocará al [comando `rm` de Linux](../uso-de-la-terminal-de-comandos/comandos-basicos.md#comandos-importantes).
* **`test`**: simplemente ejecutará, uno tras otro, los dos binarios ejecutables, `app1` y `app2`. Dependerá de ambos, como es obvio. Ponemos el objetivo `all` como dependencia, por simplicidad.

```makefile
all: app1 app2 # En la parte superior del fichero

### Resto de reglas ###

# En la parte inferior del fichero
clean: 
        rm -f *.o app1 app2

test: all
        ./app1
        ./app2
```

***

## Makefile completo

Así quedaría, por tanto, el _Makefile_ completo para nuestro proyecto (desplegar para ver):

<details>

<summary>Makefile</summary>

```make
all: app1 app2

helloPRA.o: helloPRA.cpp helloPRA.h
        g++ -c helloPRA.cpp

app1.o: app1.cpp helloPRA.h
        g++ -c app1.cpp

app2.o: app2.cpp helloPRA.h
        g++ -c app2.cpp

app1: app1.o helloPRA.o
        g++ -o app1 app1.o helloPRA.o

app2: app2.o helloPRA.o
        g++ -o app2 app2.o helloPRA.o

clean: 
        rm -f *.o app1 app2

test: all
        ./app1
        ./app2
```

</details>

***

## Uso de Make

Crea con Vim el fichero _Makefile_ del apartado anterior en el mismo directorio donde se encuentran los ficheros de código fuente. En el directorio, por tanto, quedarán estos ficheros:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.24.31.png" alt=""><figcaption></figcaption></figure>

A continuación, ejecuta:

```bash
make
```

Esto invocará la regla **`all`**, ya que es la primera que está definida en el fichero _Makefile_. La herramienta `make` mostrará, para nuestra información, una línia por cada comando ejecutado:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.28.11.png" alt="" width="563"><figcaption></figcaption></figure>

Podemos comprobar que se han generado todos los ficheros de código objeto y binarios ejecutables previstos:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.28.42.png" alt=""><figcaption></figcaption></figure>

Ahora, ejecuta la regla **`test`**, para lanzar los dos binarios ejecutables:

```bash
make test
```

La salida es la esperada. De hecho, conviene destacar que no se ha vuelto a compilar ni enlazar ningún fichero, pues no es necesario:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.29.36.png" alt="" width="344"><figcaption></figcaption></figure>

Ahora vamos a comprobar de primera mano las ventajas de Make. Modifica con Vim el fichero `app1.cpp` para que imprima el string `Adiós!` a continuación de la invocación a `say()`. A continuación, vuelve a ejecutar `make test`. Obtendrás una salida similar a esta:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.30.55.png" alt="" width="371"><figcaption></figcaption></figure>

Como veis, Make ha detectado que el fichero `app1.cpp`, que es prerequisito del fichero `app1.o`, y este a su vez prerequisito del fichero `app`, ha sido modificado a posteriori. Es por ello que lanza automáticamente, primero, la regla `app1.o`, y luego la regla `app1`. El resto de reglas no las lanza porque no hace falta.&#x20;

Ahora probaremos a modificar la librería `helloPRA`, ya que tal acción tiene impacto en ambos objetivos finales, `app1` y `app2`. Abre `helloPRA.cpp` con Vim, y modifica la función `say()` para que devuelva `"Hello PRA-UPV!"`. A continuación, vuelve a lanzar `make test`:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.31.56.png" alt="" width="375"><figcaption></figcaption></figure>

Como cabía esperar, ha ejecutado la regla `helloPRA.o`, y consecuentemente, las reglas `app1` y `app2`, dejando de lado las reglas `app1.o` y `app2.o`, pues no hay ninguna necesidad de volver a ejecutarlas. En un proyecto de juguete como este no tiene demasiado impacto, pero en un proyecto grande como, por ejemplo, el Kernel de Linux, esta medida resulta imprescindible. De lo contrario, el proceso de compilación tardaría varios minutos para llevarse a cabo.

Por último, ejecuta la regla clean, para dejar el directorio limpio de ficheros destino:

```bash
make clean
```

Podemos comprobar como el directorio ha quedado bien limpio y reluciente:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-21 a las 13.32.40.png" alt=""><figcaption></figcaption></figure>

***

## Mejoras en el Makefile

Aunque, por simplicidad, no vamos a tratar aspectos avanzados sobre la herramienta Make, sí mencionaremos la posibilidad de simplificar un poco las reglas de Make, ya que son un tanto repetitivas. Por ejemplo, los comandos a ejecutar para generar los ficheros `.o` siguen el mismo patrón: `g++ -c <CPPFILE>`.&#x20;

Pues bien, con Make se pueden definir fácilmente **reglas automáticas de generación de cierto tipo de ficheros destino a partir de sus dependencias&#x20;**_**(suffix rules)**_:

```makefile
.SUFFIXES: .cpp .h .o # definimos sufijos válidos
.cpp.o:
    g++ -c $*.cpp # regla para generar archivos de .cpp a .o
```

Con esta regla automática, ya no es necesario especificar comandos en los objetivos correspondientes a ficheros `.o`, pues Make los infiere. Únicamente especificamos las dependencias:

```makefile
helloPRA.o: helloPRA.cpp helloPRA.h

app1.o: app1.cpp helloPRA.h

app2.o: app2.cpp helloPRA.h
```

Con ello, simplificamos bastante el _Makefile_ y evitamos posibles errores. El _Makefile_ resultante quedaría así:

<details>

<summary>Makefile simplificado con reglas automáticas</summary>

```make
# Desactiva las reglas implícitas por defecto y define
# qué extensiones se usarán en las transformaciones
.SUFFIXES: .cpp .h .o

# Regla de compilación:
# cualquier archivo .cpp puede convertirse en .o
.cpp.o:
	g++ -c $*.cpp

# Regla principal por defecto.
# Al ejecutar "make", se construirán app1 y app2
all: app1 app2

# helloPRA.o depende de estos archivos.
# Si cambia cualquiera de ellos, se recompila
helloPRA.o: helloPRA.cpp helloPRA.h

# app1.o depende del fuente y del header
app1.o: app1.cpp helloPRA.h

# app2.o depende del fuente y del header
app2.o: app2.cpp helloPRA.h

# Para generar el ejecutable app1
# primero deben existir app1.o y helloPRA.o
app1: app1.o helloPRA.o
	g++ -o app1 app1.o helloPRA.o

# Para generar el ejecutable app2
# primero deben existir app2.o y helloPRA.o
app2: app2.o helloPRA.o
	g++ -o app2 app2.o helloPRA.o

# Elimina archivos generados automáticamente
clean:
	rm -f *.o app1 app2

# Ejecuta ambos programas después de compilar
test: all
	./app1
	./app2
```

</details>
