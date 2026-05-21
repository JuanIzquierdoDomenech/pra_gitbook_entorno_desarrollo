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
{% tab title="helloPRA.cpp" %}
```c++
#include "helloPRA.h"

std::string say(){
    return "Hello PRA!";
}
```
{% endtab %}

{% tab title="helloPRA.h" %}
```cpp
#include <string>

std::string say();
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
