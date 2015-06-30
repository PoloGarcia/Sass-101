# Preparandote para hacer magia con Sass

A continuación se muestra de manera breve como instalar todos los componentes necesarios para empezar a definir estilos con Sass, compilarlo, etc. 

Primeramente recordar que los archivos que se van a escribir en Scss tienen que ser compilados para que se produzca un CSS comprensible por el explorador web. Para ello será necesario instalar compass la cual es una gema de ruby, así que asegurate de tener instalado Ruby antes de continuar. 

Entonces primeramente instalaras compass de la siguiente manera dentro de la terminal de tu sistema operativo: 

###### Mac OS X / Linux

``` bash
sudo gem install compass
``` 

###### Windows

``` bash
gem install compass
``` 

## Crea tu primer proyecto Sass

Ahora crearemos un proyecto de prueba, para asegurar que todo se hizo de manera correcta, para ello corre el siguiente comando dentro de la terminal:

``` bash
cd --la carpeta donde deseas crear el proyecto
compass create sass-test
cd sass-test 
``` 

Dentro de esta carpeta de sass-test veras que se crearon distintas carpetas y archivos por el momento las puedes dejar asi, para probar si todo funciona como debería corre el siguiente comando

``` bash
compass compile
``` 

Este comando compila todos tus archivos .scss (En este caso todos los que se encuentran en sass y los guarda en la carpeta css) a archivos .css , checa errores de sintaxis, etc. ahora ya puedes escribir un poco de scss, pero no tienes que compilar tus archivos cada vez que haces un cambio deja que compass se encargue de ello, para esto corre el comando 

``` bash
compass watch
``` 

Este comando observa por cambios dentro de tus .scss cada que guardes el archivo y lo compilara automáticamente, así que porqué no pruebas por ejemplo renombrar:

**ie.scss**  ->  **_ie.scss**

**print.scss**  ->  **_print.scss**

y despues modificar **screen.scss** añadiendo las siguientes lineas

``` scss

@import "print";
@import "ie";

``` 

Para observar los resultados de la acción pasada es recomendable que agregues un poco de Scss dentro de los archivos de ie y print para que veas como funcionan los parciales. Igualmente dentro de compass existen muchos mixins predefinidos de los que puedes hacer uso y los puedes consultar [aquí](http://compass-style.org/index/mixins/) para hacer uso de ellos solo tendrás que añadir 

``` scss

@import "compass";

``` 

##### Ya estas listo para iniciar con los ejercicios propuestos ¿Que esperas?
