# Automatización: Make

[Make](https://en.wikipedia.org/wiki/Make_\(software\)) es una **herramienta de automatización de procesos de compilación**, mediante la lectura de archivos llamados _Makefile_ que especifican objetivos (de compilación) y como se puede llegar a ellos. Su primera versión fue lanzada en 1976. Es una herramienta ampliamente utilizada, especialmente en proyectos de software libre escritos en C y C++.&#x20;

Entre sus bondades podemos destacar:

* Permite al usuario final **compilar e instalar el proyecto software sin conocer los detalles de cómo se hace**, porque estos detalles se registran en el archivo _Makefile_ proporcionado.&#x20;
* Make **determina automáticamente qué archivos binarios necesita actualizar**, en función de qué archivos de código fuente (p.ej., `.cpp`) han cambiado. Como resultado, si se cambian unos pocos archivos de código fuente y luego se ejecuta Make, solo se lanzará la compilación de los ficheros afectados; no se compilará el proyecto entero, por lo que ahorraremos tiempo.
* Make **no se limita a ningún lenguaje de programación en particular**. Para cada archivo que no sea origen o fuente, el archivo Makefile especifica los comandos que permiten generarlo. Estos comandos pueden ejecutar un compilador para producir un archivo binario, el enlazador para producir un ejecutable, para generar la documentación del proyecto en HTML, etc.&#x20;
