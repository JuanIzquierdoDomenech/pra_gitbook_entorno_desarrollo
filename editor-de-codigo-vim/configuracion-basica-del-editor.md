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

# Configuración básica del editor

**Opcionalmente**, podemos crear un pequeño fichero de configuración para que Vim arranque siempre con algunas opciones activadas. Este fichero se llama `.vimrc` y debe estar ubicado en el directorio _home_ (\~) del usuario:

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-28 a las 19.47.31.png" alt="" width="267"><figcaption></figcaption></figure>

Podemos crearlo o editarlo ejecutando:

```bash
vim ~/.vimrc
```

Dentro de este fichero, podemos escribir la siguiente configuración básica:

```vim
set title
syntax on
filetype on
filetype indent on
set tabstop=4 softtabstop=4 shiftwidth=4 expandtab autoindent smartindent
set number relativenumber
colo desert
```

Debemos guardar el fichero, salir (`:wq`) y volver a entrar para que haga efecto la configuración.

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-28 a las 20.04.49.png" alt="" width="563"><figcaption></figcaption></figure>

A continuación se describe brevemente qué hace cada una de estas opciones:

***

#### `set title`

Hace que Vim actualice el título de la ventana del terminal, normalmente mostrando el nombre del fichero que estamos editando.

#### `syntax on`

Activa el resaltado de sintaxis. Esto permite que Vim muestre con colores diferentes algunos elementos del código fuente, como palabras reservadas, comentarios, cadenas de texto o constantes numéricas.

#### `filetype on`

Activa la detección automática del tipo de fichero. Por ejemplo, si abrimos un fichero llamado test.cpp, Vim reconocerá que se trata de un fichero C++.

#### `filetype indent on`

Activa las reglas de indentación propias de cada tipo de fichero. En el caso de C++, Vim puede aplicar una indentación más adecuada al escribir bloques delimitados por llaves.

#### `set tabstop=4 softtabstop=4 shiftwidth=4 expandtab autoindent smartindent`

Esta línea configura la indentación del editor.

* `tabstop=4` indica que un tabulador se mostrará con una anchura equivalente a 4 espacios.
* `softtabstop=4` hace que, al pulsar la tecla TAB en modo inserción, Vim avance como si se hubiesen introducido 4 espacios.
* `shiftwidth=4` indica que las operaciones de indentación automática o manual usarán 4 espacios.
* `expandtab` hace que Vim inserte espacios en lugar de caracteres de tabulación reales (<mark style="background-color:$warning;">no recomendado para editar ficheros Make</mark>, ya que Make es sensible a la indentación).
* `autoindent` mantiene en la línea nueva la misma indentación que tenía la línea anterior.
* `smartindent` aplica algunas reglas básicas adicionales de indentación, útiles en lenguajes como C y C++.

#### `set number relativenumber`

Muestra números de línea. La línea actual aparece con su número absoluto, mientras que el resto de líneas aparecen numeradas de forma relativa respecto a la posición actual del cursor.

Esto facilita el uso de comandos de movimiento. Por ejemplo, si una línea aparece marcada con el número relativo 5, podemos movernos hasta ella escribiendo `5j` (hacia abajo) o `5k` (hacia arriba) desde el modo comando, según esté por debajo o por encima de la línea actual.

{% hint style="info" icon="lightbulb" %}
También podemos usar las flechas tradicionales.
{% endhint %}

<figure><img src="../.gitbook/assets/ChatGPT Image 28 may 2026, 20_05_45.png" alt="" width="563"><figcaption><p>Atajos para moverse entre líneas (modo comando)</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Grabación de pantalla 2026-05-28 a las 20.01.30.gif" alt=""><figcaption></figcaption></figure>

#### `colo desert`

Selecciona el esquema de color _desert_, que viene incluido por defecto en Vim. No requiere instalar plugins y proporciona un contraste razonable para editar programas en C++.

Puedes visualizar todos los temas disponible (sin instalación) si escribes el comando `:colorscheme` seguido de un espacio y `Ctrl + D` (mostrar opciones disponibles):

<figure><img src="../.gitbook/assets/Captura de pantalla 2026-05-28 a las 19.51.35.png" alt=""><figcaption></figcaption></figure>
