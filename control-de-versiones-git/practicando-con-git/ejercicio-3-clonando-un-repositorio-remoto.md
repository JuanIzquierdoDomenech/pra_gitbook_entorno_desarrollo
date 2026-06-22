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

# Ejercicio 3: clonando un repositorio remoto

En este último ejercicio vamos a clonar un repositorio Git remoto existente. Concretamente, el repositorio Github de [yt-dlp](https://github.com/yt-dlp/yt-dlp), una popular herramienta que permite descargar vídeos y audios de Youtube.&#x20;

Hemos escogido este repositorio porque tiene un tamaño comedido y el proceso de clonado es relativamente rápido (1 minuto aproximadamente).&#x20;

```bash
git clone https://github.com/yt-dlp/yt-dlp.git
```

Esto generará una salida como la que sigue:

<figure><img src="../../.gitbook/assets/Captura de pantalla 2026-05-21 a las 18.52.03.png" alt=""><figcaption></figcaption></figure>

Como curiosidad, podemos examinar el historial de commits con `git log`. En él podemos apreciar la componente colaborativa del desarrollo de software abierto.&#x20;

En nuestra copia local del repositorio, poder realizar los commits que queramos. Ahora bien, si intentamos enviar dichos cambios al repositorio remoto, no podremos, ya que no tenemos permisos.&#x20;

Si el repositorio fuese vuestro, si podríais haber subido los cambios.

{% hint style="info" %}
En el contexto de esta asignatura no aplica, pero, si en el futuro queréis contribuir de manera voluntaria en el desarrollo de un proyecto de software abierto en Github, primero deberéis crear una bifurcación _**("fork")**_ del repositorio oficial en vuestra cuenta Github.&#x20;

Un _fork_ viene a ser una copia independiente del repositorio oficial, con sus propias ramas independientes.&#x20;

A continuación, trabajaríais con vuestro _fork_, introduciendo los cambios pertinentes.&#x20;

Finalmente, se debe crear una solicitud de incorporación de cambios _**("pull request")**_, que es revisada y discutida por los desarrolladores principales del proyecto, tras observar las diferencias entre la rama oficial y la rama que se aporta.&#x20;

* Si la _pull request_ resulta interesante y se aprueba, esta se integra en la rama correspondiente del repositorio oficial.&#x20;
* Si no, se descarta.&#x20;

Tenéis más información [aquí](https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).
{% endhint %}

<div align="center"><figure><img src="../../.gitbook/assets/ChatGPT Image 21 may 2026, 18_59_53.png" alt="" width="563"><figcaption><p>El repositorio superior ha sido 'bifurcado' (cada copia evoluciona de manera independiente)</p></figcaption></figure></div>

<figure><img src="../../.gitbook/assets/https___content.gitbook.com_content_KCglCYAzIkqjjsArrX0I_blobs_D2tAwJENgOv2G4w9Xwol_ITDO-githubflow.avif" alt=""><figcaption><p>Flujo de trabajo cooperativo</p></figcaption></figure>
