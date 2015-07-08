# Creando una landing

En este ejercicio vamos a explorar las bondades de Sass mediante la creacion de una landing page.

### Introduccion

Aqui te presentamos la estructura de archivos inicial del ejercicio: 

``` bash
Ejercicio/
|
|-- assets/                       # El conjunto de imagenes, archivos utilizados en la landing
|   |-- img/                      # Imagenes que se utilizan en el proyecto
|       |-- favicon.ico           # Favicon a desplegar
|       |-- cover-picture.png     # Imagen utilizada como cover
|       |-- ...                   # etc
|
|-- landing.html                  #archivo html sobre el que trabajaremos

``` 
Puedes abrir el archivo de landing.html dentro de cualquier explorador web y podras notar que este no tiene ningun estilo, pero al final de nuestro ejercicio la idea es tener un sitio con un aspecto similar al que se muestra a continuacion: 

![alt text](https://lh6.googleusercontent.com/qKBZsccuzB08MGyB36hROnNI9hPANZ6-yFeBscauTogY4EBwXVICxBKbUzRwu9cPDqkF_hGorb2LR7E=w1256-h581-rw "Seccion 1")

![alt text](https://lh5.googleusercontent.com/H1PVXq_htRZAB21ToLJqxlR18avFk9wQxyMuF_Uszm-gyD-deBwsx3Cg4fnxLkfEZo_70XnrGvojvw8=w1256-h581-rw "Seccion 2")

![alt text](https://lh3.googleusercontent.com/--xDmZTtvqHK9POFFRXELyjXua6031Nf9t9CPN4hy5nWiy1BxMk8NrG_LrCzn9bfdhC44yUChj9wlvE=w1256-h581-rw "Seccion 3")

Como podras notar nuestro sitio va a estar divido en tres principales secciones, las cuales si ingresas el archivo de ``` landing.html ``` podras identificar de manera casi inmediata rodeadas por etiquetas ``` <div> </div> ``` que poseen id's con nombres: __section-1, section-2, section-3__, es importante que mantengas esto en mente para que le encuentres sentido al ejercicio conforme vayamos avanzando. 

#### Pasos iniciales

Como recordaras de haber leido __install.md__ para un proyecto de sass lo primero que tenemos que tenemos que hacer es crear la estructura inicial de archivos y el archivo de configuracion de nuestros archivos .scss, para ello vamos a correr el siguiente comando (dentro de la carpeta de ejercicio): 

``` bash
compass init 
```
Si todo funciono de manera correcta tu estructura de archivos ahora debe de parecerse a la siguiente: 

``` bash
Ejercicio/
|
|-- assets/                       # El conjunto de imagenes, archivos utilizados en la landing
|   |-- img/                      # Imagenes que se utilizan en el proyecto
|   |   |-- favicon.ico           # Favicon a desplegar
|   |   |-- cover-picture.png     # Imagen utilizada como cover
|   |   |-- ...                   # Etc
|
|-- sass/                         # Aqui es donde vas a crear tus archivos .scss
|   |-- ie.scss
|   |-- print.scss
|   |-- screen.scss
|
|-- stylesheets/                  # Aqui es donde se van a guardar tus archivos .css, generados al compilar tus .scss
|   |-- ie.css
|   |-- print.css
|   |-- screen.css
|
|-- config.rb                     # Archivo ruby con las configuraciones de compilacion para .scss
|-- landing.html                  # Archivo html sobre el que trabajaremos

```

Los archivos que genera este comando dentro de sass y stylesheets, en este caso no son de utilidad por lo cual vamos a proceder a borrar todo el contenido de estas dos carpetas y en su lugar crear archivos que sean relevantes para nuestro ejercicio. 

*__replica la siguiente estructura de archivos:__*

``` bash
Ejercicio/
|
|-- assets/                       # El conjunto de imagenes, archivos utilizados en la landing
|   |-- img/                      # Imagenes que se utilizan en el proyecto
|   |   |-- favicon.ico           # Favicon a desplegar
|   |   |-- cover-picture.png     # Imagen utilizada como cover
|   |   |-- ...                   # Etc
|
|-- sass/                         # Aqui es donde vas a crear tus archivos .scss
|   |-- main.scss
|   |-- _landing.scss
|   |-- _mixins.scss
|   |-- _base.scss
|   |-- _variables.scss
|
|-- stylesheets/                  # Aqui es donde se van a guardar tus archivos .css, generados al compilar tus .scss
|
|-- config.rb                     # Archivo ruby con las configuraciones de compilacion para .scss
|-- landing.html                  # Archivo html sobre el que trabajaremos

```
**¿porque se utiliza un " _ " antes de nombrar algunos de los archivos dentro de sass?**
Si recuerdas del archivo README.md, los " _ " representan un archivo parcial, es decir un archivo que se va a incluir dentro de otro para asi poder dividir nuestros estilos en bloques más legibles y mantenibles. Para el caso de nuestro ejercicio propusimos una estrucutura de parciales simples:

``` 
_landing.scss -> Contiene todos los estilos exclusivos a la landing
_mixins.scss -> Contiene todos los mixins de los cuales haremos uso en este ejercicio
_base.scss -> Define estilos basicos para todos nuestros archivos html
_variables.scss -> Definicion de todas las variables a usar
```

###### Incluyendo los parciales dentro del archivo principal 

El siguiente paso es añadir nuestros parciales y algunas librerias de mixins como compass (que se menciona anteriormente). Para lo cual vamos a abrir nuestro ``` main.scss ``` y agregaremos las lineas necesarias para añadir nuestros parciales:

``` scss 
@import "compass";
@import "mixins";
@import "variables";
//Añade los parciales restantes, recuerda que no es necesario incluir el _ ni la extension .scss
// Tampoco olvides añadir el ; al final de cada linea
```
Despues de realizar estos cambios puedes correr el comando ``` compass compile ``` y notar que dentro de la carpeta ``` stylesheets ``` se genero un archivo llamado ``` main.css ``` que hasta ahora se encuentra vacio.

### Definiendo variables

