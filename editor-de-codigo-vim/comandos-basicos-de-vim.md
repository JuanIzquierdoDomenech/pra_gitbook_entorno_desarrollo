# Comandos básicos de Vim

A continuación se proporciona un listado de comandos básicos que se pueden ejecutar desde los modos comando y/o visual de Vim, y que deberéis aprender para la realización de las prácticas.&#x20;

## Guardar cambios y salir del programa

**`:w`** -> _(write)_ guardar el contenido del buffer en disco, en el fichero correspondiente.

**`:wq`** -> _(write and quit)_ guarda y sale de la aplicación.

**`:q`** -> _(quit)_ salir de la aplicación; no se permite si hay cambios en el buffer pendientes de guardar en disco.

**`:q!`** -> _(quit now)_ fuerza la salida de la aplicación (aunque haya cambios en el buffer sin guardar en disco).

***

## Manipulación de los contenidos del buffer

**`dd`** -> _**(delete)**_**&#x20;borrar contenidos del buffer.**

* Estando en modo comando: borra la línea actual del buffer, y la copia al portapapeles de Vim (por si queremos pegarla luego).
  * Podemos pedir que se repita el comando tantas veces como deseemos, anteponiendo un entero positivo antes de `dd`.&#x20;
  * `33 dd` -> borra la línea actual + las 32 siguientes (33 en total, y se copian en el portapapeles).
* Estando en modo visual: borra el contenido seleccionado (y lo copia al portapapeles).

**`yy`** -> _**(yank)**_**&#x20;copiar contenidos del buffer al portapapeles de Vim.**&#x20;

* Estando en modo comando: copia la línea (completa) sobre la que se encuentra el cursor.
  * `20 yy`-> copia la línea actual + las 19 siguientes (20 en total).
* Estando en modo visual: copia el contenido seleccionado.

**`p`** -> _**(paste)**_**&#x20;pega el contenido del portapapeles de Vim en el buffer (después del cursor).**

* `5 p` -> pega 5 veces el mismo contenido.
* `P` -> (p mayúscula) pega el contenido antes del cursor.

**`:s/<PATTERN>/<REPLACEMENT>/g`** -> **buscar y reemplazar**.

* Este comando (del modo comando) es muy poderoso, pero aquí simplemente lo introducimos de manera muy básica.
* Sustituye toda ocurrencia del patrón `<PATTERN>` por la cadena `<REPLACEMENT>`.
  * Por ejemplo: `:s/int/double/g` reemplaza toda ocurrencia de la cadena `int` por la cadena `double` en la línea actual.
* Para extender la búsqueda a todo el buffer, debemos anteponer el símbolo `%` al comando (es decir, `:%s/<PATTERN>/<REPLACEMENT>/g`).
* La `g` del final indica global dentro de cada línea afectada. Sin ella, solo se reemplaza la primera ocurrencia de cada línea afectada.
  *   `:s/int/double/`

      reemplaza solo la primera aparición de int en la línea actual.
  *   `:%s/int/double/`

      reemplaza solo la primera aparición de int en cada línea del documento.
  *   `:%s/int/double/g`

      reemplaza todas las apariciones de int en cada línea del documento.

<figure><img src="../.gitbook/assets/ChatGPT Image 29 may 2026, 11_17_25.png" alt=""><figcaption></figcaption></figure>

***

## Gestión de cambios del buffer

**`u`** -> _**(undo)**_**&#x20;deshace el último cambio realizado sobre el buffer.**

* **`5 u`** -> deshace los últimos 5 cambios realizados.

{% hint style="warning" icon="face-tongue-sweat" %}
A veces, estando en modo comando, pulsamos teclas pensándonos que estamos en modo inserción. El resultado típico de este descuido es la ejecución involuntaria de diversos comandos de Vim que acaban modificando el buffer de manera significativa. Entonces, cuando "no sepamos qué hemos hecho", **evitad entrar en pánico**: pulsad `u` _(undo)_ en modo comando, poco a poco, para "retroceder en el tiempo", hasta recuperar la versión del buffer que teníamos antes del "incidente".&#x20;
{% endhint %}

**`CTRL + r`** -> _**(redo)**_**&#x20;rehace el último cambio acumulado.**

* **`5 CTRL + r`** -> rehace los últimos 5 cambios acumulados.

***

## Navegación y búsqueda

**`w`** de _word_-> avanzar al principio de la siguiente palabra (**`25 w`** -> avanzar 25 palabras).

**`gg`** de _go_-> Posicionar el cursor en la primera línea del buffer.

**`G`** -> Posicionar el cursor en la última línea del buffer.

**`<NUM> gg`** -> Posicionar el cursor en la línea `<NUM>` del buffer (`5 gg` -> ir a la línea 5).

**`/<STRING>`** -> busca ocurrencias del string `<STRING>` en el buffer. El cursor se posicionará en la primera coincidencia encontrada.&#x20;

* `n`-> saltar a la siguiente ocurrencia
* `N` -> saltar a la anterior ocurrencia
* `ESC` -> volver al modo comando.
