# Nociones básicas de Git

## Repositorio

Un **repositorio Git** es una base de datos que almacena de forma eficiente diferentes versiones y configuraciones de una jerarquía de directorios y ficheros. Se puede inicializar un repositorio Git vacío (`git init`) y empezar a trabajar con él, o bien "clonar" (copiar o descargar) un repositorio Git remoto existente que ya contiene información (`git clone`). Esto nos crea un **directorio de trabajo&#x20;**_**(working directory)**_, que viene a ser una copia de una versión concreta del proyecto (en este caso, de la versión más reciente).&#x20;

Además de la propia estructura de directorios y los correspondientes ficheros, un repositorio Git gestiona el historial completo de cambios o confirmaciones (commits), las diferentes ramas del proyecto (branches), y las etiquetas manuales (tags).&#x20;

***

## Confirmaciones (_Commits_)

Una confirmación (commit) es una acción de un usuario sobre el repositorio Git para enviar a la base de datos las modificaciones realizadas sobre uno o varios archivos del proyecto  (`git commit`). Esto genera un registro en la base de datos que contiene las **diferencias de los archivos** modificados con respecto a su versión inmediatamente anterior, además de información sobre **quién hizo el commit**, **cuándo** lo hizo, y un **mensaje descriptivo** (escrito por el autor) de los cambios realizados. Los commits pueden considerarse instantáneas o hitos a lo largo de la línea temporal de un proyecto en Git, ya que capturan el estado de un proyecto en el momento en el que éste se realizó.&#x20;

El conjunto de commits realizados sobre un repositorio git ordenados en el tiempo es lo que se conoce como el **historial de commits** (`git log`). Este nos permite examinar el proceso de desarrollo del proyecto, y eventualmente, revertir cambios o restaurar versiones anteriores (`git checkout`, `git reset`, `git revert`).

***

## Ramas (_Branches_)

Una rama (branch) en Git representa una **línea de desarrollo independiente** al resto de ramas. La **rama principal** de un repositorio Git, por defecto, se denomina _**master**._ Generalmente, se crean ramas para realizar tareas muy específicas sobre el proyecto (`git branch`), como por ejemplo implementar una característica (feature) o funcionalidad nueva. Las ramas se suelen integrar en la rama _master_ una vez acabadas (`git merge`), aunque a veces se desechan, cuando no interesa incorporar los cambios realizados a la rama principal. Para conocer más detalles sobre el potente sistema de ramificación de git aplicado a proyectos software, se recomienda leer el siguiente artículo:

{% embed url="https://nvie.com/posts/a-successful-git-branching-model/" %}

***

## Etiquetas (Tags)

Las etiquetas (tags) son referencias que apuntan a puntos específicos en la historia de commits de Git. Se utilizan generalmente para capturar un punto en la historia del desarrollo que determina una versión del software o producto (`git tag`). Por ejemplo: `v1.0`, `1.1`, etc.&#x20;

<figure><img src="../.gitbook/assets/git-model@2x.png" alt="" width="563"><figcaption><p>Metodología de ramificación y etiquetado en Git aplicado a proyectos software (git-flow)</p></figcaption></figure>

***

## Estados de archivo

Git tiene tres estados principales en los que se pueden encontrar los archivos de nuestro directorio de trabajo:

* **Modificado&#x20;**_**(modified)**_**:** significa que hemos modificado el archivo pero que todavía no lo hemos confirmado en la base de datos de Git.
* **Preparado&#x20;**_**(staged)**_**:** significa que hemos marcado un archivo modificado para poder enviar las diferencias (cambios) a la base de datos en la próxima confirmación. Los ficheros se almacenan temporalmente en la denominada área de preparación _(stage area)_.
* **Confirmado&#x20;**_**(commited)**_**:** significa que el contenido del archivo está sincronizado con la base de datos del repositorio Git local.

***

## Flujo de trabajo básico en Git

&#x20;El flujo de trabajo básico en Git es:

1. **Modificar archivos** en el directorio de trabajo.
2. **Marcar los archivos** que queremos que se incluyan en la próxima confirmación (`git add`).
3. **Confirmar los cambios** a la base de datos (`git commit`), añadiendo un mensaje informativo/descriptivo de los cambios realizados.

***

## Sincronización con repositorios remotos y trabajo colaborativo

Los repositorios remotos son otros repositorios Git que almacenan (versiones de) el mismo proyecto, y que están hospedados:

* en la misma máquina, o
* en otra(s) máquina(s) de la red local, o&#x20;
* en Internet, lo que incluye servicios como [Github](https://github.com/) o [Gitlab](https://about.gitlab.com/).&#x20;

Un repositorio Git local puede interactuar con uno o varios repositorios remotos (`git remote`). Colaborar con otras personas implica, por lo general, interactuar con repositorios remotos, **enviando** (`git push`) y **recibiendo** (`git pull` / `git fetch`) cambios de ellos cada vez que se necesite compartir el trabajo.

La figura siguiente muestra de forma visual este proceso de trabajo colaborativo a través de un repositorio remoto:

<figure><img src="../.gitbook/assets/https___content.gitbook.com_content_KCglCYAzIkqjjsArrX0I_blobs_Fxp6k1lGBZ4RU3jJewNk_basic-remote-workflow.png" alt="" width="563"><figcaption><p>Sincronización de los repositorios git locales de dos desarrolladores distintos a través de un repositorio remoto.</p></figcaption></figure>

Hay dos desarrolladores, A y B, cada uno con su repositorio git local en su propio dispositivo (PC, portátil, ...). Ambos repositorios locales están "enlazados" con un repositorio git remoto (p.ej., en [GitHub](https://github.com/)), el cual centraliza todas las transacciones (enfoque _bottom-up_).

{% hint style="info" %}
Dicho de otra manera (enfoque _top-down_): existe un repositorio remoto "oficial" que almacena el proyecto. Los dos desarrolladores han clonado (`git clone`) este repositorio en sus respectivos dispositivos, de modo que A y B tienen sendas copias locales.&#x20;
{% endhint %}

Asumimos que los tres repositorios git (A, B, y remoto) estan sincronizados (misma base de datos, con los mismos ficheros y el mismo historial de commits). En la figura se puede intuir que:

1. El desarrollador "A" ha realizado cambios en su directorio de trabajo.
2. "A" añade dichos cambios al área de intercambio (`git add`), y los confirma (`git commit`).
3. "A" envia al repositorio remoto todos los cambios realizados localmente (`git push`).
4. Eventualmente, "B" actualiza/sincroniza su copia local con el repositorio remoto (`git pull`) para obtener la última versión del proyecto.&#x20;
5. "B" puede realizar los pasos 1-3.&#x20;

La naturaleza distribuida de git permite que cada desarrollador pueda trabajar con su repositorio local con total autonomía, a su ritmo. Eventualmente, puede sincronizarse con el repositorio remoto para "ponerse al día", con `git push` (enviar) y `git pull` (recibir).&#x20;

{% hint style="info" %}
Notad que los desarrolladores "A" y "B" pueden ser la misma persona. Por ejemplo, un desarrollador que mantiene sendas copias locales del repositorio en su PC de sobremesa ("A") y en su PC portátil ("B"). En este caso, el repositorio remoto se puede ver como una especie de "[Dropbox](https://www.dropbox.com/)", que permite sincronizar ficheros y directorios entre dos (o más) dispositivos propios (además del repositorio en sí: historial de commits, ramas, etiquetas).
{% endhint %}

{% hint style="warning" %}
Cuando se desarrolla un proyecto de forma colaborativa, pueden existir **conflictos** de modificación de ficheros. Por ejemplo, A y B modifican localmente (por separado) el mismo fichero, y a continuación desean sincronizar dichos cambios con el repositorio remoto. El último de los dos en hacerlo (con `git push`) recibirá un mensaje de advertencia de que su copia local no está actualizada, ya que no se permite enviar cambios a un remoto sin tener la copia local "al día". Tras hacer `git pull`, su git local detectará que hay un conflicto entre dos ficheros: uno modificado localmente, y otro modificado remotamente, por lo que debe resolverse. Afortunadamente, git facilita mucho las cosas en la resolución de este tipo de conflictos.&#x20;

Para más información sobre conflictos, podéis consultar [este enlace](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts).
{% endhint %}
