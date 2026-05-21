# Practicando con git

Antes de nada, por si no tienes instalado git en tu sistema operativo, aqui tienes las (breves) instrucciones de instalación:

{% hint style="info" %}
Ejecuta el comando `git --version` o `which git` para verificar si ya está instalado en tu sistema.
{% endhint %}

{% tabs %}
{% tab title="Debian/Ubuntu" %}
```bash
sudo apt update
sudo apt install git
```
{% endtab %}

{% tab title="Fedora" %}
Con dnf:

```bash
sudo dnf install git
```

Con yum:

```bash
sudo yum install git
```
{% endtab %}

{% tab title="MacOS" %}
Se instala con el gestor de paquetes [Homebrew](https://brew.sh/) (es necesario instalar el gestor) ([https://git-scm.com/install/mac](https://git-scm.com/install/mac))
{% endtab %}
{% endtabs %}

Empezaremos con la configuración básica git de manera global en el sistema.

```bash
git config --global user.name "TU NOMBRE"      # Configura tu nombre para los commits
git config --global user.email tuemaildela@upv.es   # Configura tu correo asociado a Git
git config --global init.defaultBranch main    # Establece "main" como rama principal por defecto
```

***

Una vez configurado, puedes realizar los ejercicios guiados en las secciones siguientes:

1. [Uso básico de git](ejercicio-1-uso-basico-de-git.md)
2. [Sincronización de un repositorio local con uno remoto](ejercicio-2-sincronizando-un-repositorio-local-con-un-repositorio-remoto.md)
3. [Clonación de un repositorio remoto](ejercicio-3-clonando-un-repositorio-remoto.md)
