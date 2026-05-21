# Editor de código: Vim

<figure><img src="../.gitbook/assets/Vimlogo.svg.png" alt="" width="188"><figcaption></figcaption></figure>

Como IDE _(Integrated Development Environment)_, usaremos [_Vim_](https://www.vim.org/). Es un **editor de textos de consola (sin interfaz gráfica), de código abierto, ligero, rápido, potente, versatil, y altamente configurable**, que viene instalado por defecto en la gran mayoría de los sistemas GNU/Linux. Su primera versión fue lanzada en 1991, y [sigue desarrollándose en la actualidad](https://github.com/vim/vim). Según el [_2022 Development Survey_ de _Stack Overflow_](https://survey.stackoverflow.co/2022), _**Vim**_**&#x20;está entre los 5 primeros IDEs más utilizado** en el sector profesional de la programación informática.

_Vim_ es un acrónimo de _"Vi Improved",_ una versión vitaminada de _Vi ("Visual")_, el editor original. No obstante, _Vim_ se ha impuesto sobre _Vi_ en las distribuciones modernas de GNU/Linux. Si _Vim_ no se encuentra instalado por defecto en el sistema, es bastante posible que _Vi_ sí lo esté. No existen grandes diferencias entre ambos, al menos, al nivel de lo que esperamos en este tutorial. En cualquier caso, aquí tenéis las instrucciones de instalación de Vim:

{% hint style="warning" %}
Ejecutad antes de nada el comando `vim`  en vuestra terminal, porque seguramente ya esté instalado por defecto.
{% endhint %}

{% tabs %}
{% tab title="Debian/Ubuntu" %}
```bash
sudo apt update 
sudo apt install vim
```
{% endtab %}

{% tab title="Fedora" %}
```bash
sudo dnf install vim
```
{% endtab %}

{% tab title="MacOS" %}
[https://formulae.brew.sh/formula/vim](https://formulae.brew.sh/formula/vim)
{% endtab %}
{% endtabs %}

Con _Vim_ disponemos de multitud de comandos y atajos predefinidos que nos permiten **aumentar nuestra productividad hasta límites insospechados**. Como contrapartida derivada de estas virtudes, _Vim_ tiene una **curva de aprendizaje** que debemos superar inicialmente para poder ser productivos. Aprender a usar Vim es como aprender a conducir un coche: hay que realizar los primeros pasos con paciencia, sin correr, poco a poco, y practicar. Con el tiempo, al igual como cuando aprendemos a conducir, automatizaremos, sin darnos cuenta, la ejecución de las diferentes operaciones y comandos que realizaremos con la herramienta.
