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

# Controles de la terminal

En esta sección se proporcionan una serie de controles básicos asociados a la aplicación de la terminal y que debéis conocer. Especialmente la función de autocompletado :)

## Control de procesos

* **`CTRL + C`**: **Mata (kill) el proceso en ejecución**.
* **`CTRL + Z`**: **Detiene temporalmente (pausa) el proceso en ejecución**.
  * Para reanudarlo, debemos ejecutar el comando `fg #id` (_foreground_), donde el _id_ se puede visualizar ejecutando el comando `jobs`.

## Eficiencia y productividad

Dentro de la ventana de la terminal, hay diferentes controles que debéis hacer uso de ellos para lograr un uso más eficiente y productivo de ella. **El objetivo de ellos es teclear (escribir) lo menos posible.**

* **`TAB`**: **solicitud de la función de&#x20;**<mark style="background-color:green;">**auto-completado**</mark>.
  * Escribe un prefijo del elemento (fichero, directorio, o comando) que quieras escribir, pulsa `TAB`, y la terminal intentará completarlo por ti.
    * En caso de no poder completarlo, escribirá hasta el siguiente prefijo que esté compartido por dos o más elementos. Vuelve a pulsar TAB para que muestre por pantalla cuales son las opciones, escribe uno o varios caracteres más para desambiguar, y vuelve a pulsar TAB para que autocomplete de nuevo con más información.
    * Repite el paso anterior tantas veces como sea necesario hasta que hayas conseguido recuperar el nombre del elemento deseado.

{% hint style="success" %}
Dejad vuestro dedo meñique de la mano izquierda bien cerca de la tecla`TAB`.&#x20;

Os recomendamos encarecidamente que **abuséis** hasta límites insospechados de esta función! :)&#x20;
{% endhint %}

* **`↑ / ↓`** (cursores teclado): **recorrido secuencial del historial de comandos ejecutados previamente**.&#x20;

{% hint style="success" %}
Si ya has escrito un comando previamente y quieres volver a ejecutarlo, no lo escribas de nuevo, **búscalo**
{% endhint %}

* **`CTRL + R`**: **búsqueda dentro del historial de comandos ejecutados previamente**.&#x20;
  * Abre un modo de búsqueda para buscar contenido en el historial de comandos.
  * Pulsa `CTRL + r` sucesivas veces para ir recorriendo la lista de comandos que cumplen con el texto de búsqueda, hasta encontrar el comando deseado
  * Una vez encontrado el comando, pulsa `ESC` o cualquier tecla de cursor para salir del modo búsqueda.
* **`SHIFT + INSERT`** o **`CTRL + SHIFT + V`**: **pegar el contenido del portapapeles** del SO.
  * Útil para cuando queremos copiar texto del navegador, de un documento PDF, etc. y pegarlo en la terminal.&#x20;
* **`CTRL + W`**: **borra el token (palabra) anterior de la línea**.
  * Mantén pulsado `CTRL+W` para borrar toda la línea.
* **`CTRL + ←`** y **`CTRL + →`** (**`option`** en Mac): **saltar entre tokens (palabras) de la línea**.&#x20;

## Miscelánea

* **`CTRL + L`**: **limpia la ventana de la terminal** (equivalente a ejecutar el comando `clear`).
