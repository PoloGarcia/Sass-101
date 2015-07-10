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

___RECUERDA QUE PARA VER REFLEJADOS TUS CAMBIOS NECESITARAS CORRER EL COMANDO ``` compass watch ``` O ```compass compile```.___

### Definiendo variables

Una de las caracteristicas más poderosas de Sass es la integracion de variables dentro de tu archivos, por lo cual a continuacion te damos las variables que vamos a utilizar a lo largo del ejercicio

``` scss
$deep-blue: #001656; 
$r_deep-blue: 0; //valor Red del color definido arriba
$g_deep-blue: 22; //valor Green
$b_deep-blue: 86; //valor Blue

$light-blue: #4D94FF;
$r_light-blue: 25;
$g_light-blue: 117;
$b_light-blue: 255;

$alpha_cover: .6; //Valor de transparencia de la imagen cover

$black: #333333;
$grey: #EAEAEA;
$pure-white: #FFF;
$almost-white: #FAFAFA;

$cover_picture: "../assets/img/cover-picture.png"; //Ruta de la imagen cover, note los ..

// Variables que representan los distintos pesos (font-weight) que tiene definida nuestra tipografia
$light: 100;
$regular: 300;
$semi-bold: 400;
$bold: 700;
$ultra-bold: 900;
```
Nota que no son todas las variables que se pueden incluir, a lo largo del ejercicio te daras cuenta de variables que se puden utilizar y que te incitamos a incluir para crear unos estilos más mantenible. 

### Definiendo los estilos base

En esta seccion vamos a estar modificando los archivos ``` _base.scss ``` y ``` _mixins.scss```.
La finalidad del archivo  ``` _base.scss ``` en este ejercicio es contener todos los estilos que son aplicables a todos nuestros archivos html, en este caso son estilos muy simples y vamos a comenzar por crear nuestro primer mixin. Para ello vamos a ir a ``` _mixins.scss``` y colocaremos el siguiente codigo SCSS

``` scss 
@mixin text-body{ //NOTA: El uso del prefijo @mixin es de suma importancia para despues poderlo mandar llamar
	font-family: 'Lato', sans-serif;
	font-size: 17px;
	color: $pure-white; //Aqui estamos haciendo uso de nuestra primer variable, la cual hace referencia al HEX de blanco
	font-weight: $light; //Usamos otra variable, que en nuestro archivo de variables esta definido como 100
}
```
Posteriormente vamos a ir a ```base.scss``` y vamos a añadir el siguiente scss 

``` scss
body{
	//Incluye aqui el mixin que acabas de crear (text-body)
	width: 100%;
	height: 100%;
	margin: 0;
}
```

###Estilos de la seccion 1

####La imagen de fondo
Como notaste en la imagen de lo que queremos conseguir, hay una imagen de fondo la cual tiene un tint de color azul. Para ello vamos a hacer uso de la magia de los mixins, el cual para nuestra conveniencia alguien más ya se tomo el tiempo de hacer. Entonces vamos a nuestro archivo ```_mixins.scss``` y colocamos el siguiente mixin: 

``` scss 
//Los parametros que tienen un :"valor" significa que son parametros opcionales y que ya tienen un valor definido por defecto
//en este caso $background-top es opcional y si no se envia nada tomara el valor de center

@mixin bg-covertint ($r-from, $g-from, $b-from, $r-to, $g-to, $b-to, $alpha, $imgurl, $background-top:"center", $background-left:"center", $background-attachment:"fixed") {
	background: -webkit-linear-gradient(rgba($r-from, $g-from, $b-from, $alpha), rgba($r-to, $g-to, $b-to, $alpha)), url($imgurl) no-repeat unquote($background-top) unquote($background-left) unquote($background-attachment); 
	background:    -moz-linear-gradient(rgba($r-from, $g-from, $b-from, $alpha), rgba($r-to, $g-to, $b-to, $alpha)), url($imgurl) no-repeat unquote($background-top) unquote($background-left) unquote($background-attachment); 
	background:      -o-linear-gradient(rgba($r-from, $g-from, $b-from, $alpha), rgba($r-to, $g-to, $b-to, $alpha)), url($imgurl) no-repeat unquote($background-top) unquote($background-left) unquote($background-attachment); 
	background:         linear-gradient(rgba($r-from, $g-from, $b-from, $alpha), rgba($r-to, $g-to, $b-to, $alpha)), url($imgurl) no-repeat unquote($background-top) unquote($background-left) unquote($background-attachment); 
	-webkit-background-size: cover;
	-moz-background-size: cover;
	-o-background-size: cover;
	background-size: cover;  
}
``` 
Ahora en ```_landing.scss``` mandamos llamar nuestro mixin, para esta primera seccion te vamos a dar mucha parte del scss para que te des una idea de como hacer uso de las jerarquias, etc. pero analiza muy bien lo que esta pasando. 

``` scss
#section-1{
	@include bg-covertint($r_deep-blue,$g_deep-blue,$b_deep-blue,$r_light-blue,$g_light-blue,$b_light-blue,$alpha_cover,$cover_picture);
	height: 100vh; //100% de altura del viewport. 
	color: $pure-white;
}
```

Despues de hacer esto vamos a dar de alta 2 mixins, el primero para centrar horizontalmente algun elemento html y el segundo para reciclar las propiedades de nuestros h1 en todas nuestras secciones

``` scss
@mixin center-horizontal{
	display: block;
	margin-left: auto;
	margin-right: auto;
}

@mixin headers{
	font-weight: $light;
	font-size: 70px;
	text-align: center;
	margin-bottom: 10px;
	width:50%;
	@include center-horizontal;

}
```

Una vez definidos estos mixins, aqui te damos el scss faltante para la seccion 1

```scss
h1{
		@include headers;
		margin-bottom: 30px;
	}

	img{
		height: 30vh;
		@include center-horizontal;
	}

	.logo{
		font-size: 50px;
		width: 100%;
		text-align: center;
		color: $pure-white;

		.bold{
			font-weight: $ultra-bold;
		}

		.thin{
			font-weight: $light;
		}
	}

	p{
		margin-top: 20px;
		font-weight: $regular;
		width: 60%;
		text-align: center;
		font-size: 20px;
		@include center-horizontal;
		font-weight: $light;
	}
```

Recuerda analizar el codigo que te estamos dando, pues la finalidad de este ejercicio no es en si saber css sino reconocer las bondades y la utilidad de Sass. Por ejemplo analiza cual seria el css generado para .thin . 

###Seccion 2 

Para la seccion 2, el proceso es bastante parecido, una de las diferencias es que hay ```<form></form>``` y para ello vamos a dar de alta otro mixin:

``` scss
@mixin placeholder ($color,$font-weight){
	::-webkit-input-placeholder {
		color: $color;
		font-weight: $font-weight;
	}

	:-moz-placeholder { /* Firefox 18- */
		color: $color;
		font-weight: $font-weight;
	}

	::-moz-placeholder {  /* Firefox 19+ */
		color: $color;
		font-weight: $font-weight;
	}

	:-ms-input-placeholder {  
		color: $color; 
		font-weight: $font-weight;
	}
}
```
Este mixin lo que hace es repetir los estilos de form, para los distintos navegadores que existen (creeme te esta salvando bastante trabajo). 
Ahora en ```_landing.scss``` vamos a colocar la estructura basica para que tu termines de dar los estilos. 

``` scss
#section-2{
	height: 100vh;
	background-color: $almost-white;
	color: $light-blue;
	
	//--------------------------------------------------
	//Agrega el codigo necesario para que H1:
	//haga uso del mixin que definimos anteriormente
	//tenga un peso de fuente de 300
	//un margin-top de 0 y un margin-bottom de 40px
	//--------------------------------------------------
	
	//Aqui esta el codigo de form, te lo damos por que puede resultar un poco pesado, pero de nuevo recuerda analizar lo que esta pasando, con las anidaciones, etc. 
	form{
		.form-element{
			display: block;
			input[type=text]{
				border-style: none;
				background: none;
				outline: none;
				border-bottom: solid 2px darken($almost-white,20%); // esta funcion -> darken(color,porcentaje), obscurece un color en cierto porcentaje
				font-size: 50px;
				font-weight: $light;
				font-family: 'Lato', sans-serif;
				width: 60%;
				margin-left: 20%;
				text-align: center;
				margin-top: 15px;
				margin-bottom: 30px;
				color: $light-blue;
				transition: all 0.3s ease 0s;
				padding-bottom: 20px;

				&:focus{
					border-bottom: solid 2px $light-blue;
				}
			}
			button{
				font-size: 50px;
				font-weight: $light;
				font-family: 'Lato', sans-serif;
				background: $light-blue;
				border: 1px solid $light-blue;
				color: $pure-white;
				width: 60%;
				outline: none;
				margin-left: 20%;
				margin-top: 30px;
				margin-bottom: 30px;
				transition: all 0.3s ease 0s;
				padding: 20px 20px 20px 20px;

				&:hover{
					background: none;
					//background: $light-blue;
					color: $light-blue;
					border: 1px solid $light-blue;
				}
			}
		}
	}
	
	//Manda llamar el mixin que creamos al inicio de esta subseccion (placeholder) con el parametro, $color con valor de $almost-white obscurecido en un 20% (si revisaste el codigo anterior sabras como hacerlo)  y el parametro $font-weight de 100. 
	
}
```

### Seccion 3 

Para la seccion 3 el proceso es bastante parecido al de la seccion 1. Incluso el codigo scss es tambien bastante igual, aqui te damos el esqueleto basico para esta seccion:

``` scss
#section-3{
	background-color: $light-blue;
	height: 100vh;
	
	//Dale estilos a H1 con: 
	//el mixin de headers
	//color $pure-white
	//margin-top de 0
	
	//Dale estilos a .pricing-table con:
	// width: 100%
	
	//Si analizas el html notaras que pricing-table tiene anidados price y dentro de este estan anidados otros elementos como,
	//img, p, etc. aqui te vamos a colocar lo que esperamos de cada elemento y ya a ti te toca generar el scss 
	//que permita estilizar estas anidaciones. 
	
	//.price:
	// color $almost-white
	// texto alineado al centro
	// tamaño de fuente de 30px
	// ancho de 30%
	// display como inline-block
	// padding de 20px para todos los lados
	//
	//    img:
	//        width de 15%
	//
	//    h2: 
	//        peso de fuente de $300
	// 
	//    .description:
	//        tamaño de fuente de 2vh
	//
	//    .money:
	//        peso de fuente bold
	//        tamaño de fuente de 50px
	//
	
	// Finalmente al primer hijo de la clase (investiga el operador first-child) .price dale los siguientes estilos:
	// border-right: solid 1px $pure-white;
	// margin-left: 18%;
	
}
```
Con eso termina nuestro ejercicio, pero estoy seguro de que viste oportunidades de mixins, variables, etc. ¿Cuales agregarias tu? 
