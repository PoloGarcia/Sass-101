# Sass-101

*A continuacion presentamos una breve guia introductoria a Sass, asegurate de enteder todos los conceptos antes de iniciar los ejercicios propuestos*

## ¿Qué es Sass? 
Saas por sus siglas Syntactically Awesome Stylesheets, es un preprocesador de CSS con el cual se puede escribir estilos de manera más limpia y clara. Al tratarse de un preprocesador de CSS este se necesita compilar antes de enviar a producción.

## ¿Cuales son los beneficios sobre CSS? 
Saas posee distintas capacidades que permiten el desarrollo de estilos de manera más limpia, mantenible y comprensible. 

#### Partials

Los archivos CSS comúnmente son extensos y por lo tanto darles mantenimiento o encontrar un estilo en específico puede resultar costoso en tiempo. Para ello Sass presenta el concepto de partials, los cuales son archivos parciales como su nombre lo indica que son incluidos en el CSS principal al momento de la compilación. 

__Importante:__ Para que un archivo .scss se guarde como parcial se debe inculuir un guion bajo al inicio *“_ejemploDeParcial.scss”*

``` scss
//Ejemplo:

@import "formas";
@import "landing";
@import "seccion-1";

``` 
Estos imports haran que los estilos contenidos en esos 3 archivos se compilaron dentro del CSS principal. Es importante notar que aunque los archivos fueron nombrados con un “_” a la hora de incluirlos en el CSS principal no es necesario incluir dicho carácter dentro del nombre y tampoco la extensión .scss 

#### Variables

Uno de las funcionalidades más útiles que presenta Sass es el uso de variables, las cuales nos permiten reutilizar valores y sobre todo evitar redundancias innecesarias que a la hora del mantenimiento de código solamente entorpecen el desarrollo.
Un ejemplo muy bueno para ver el poder de nuestras variables es el uso de colores, tamaño de fuentes, márgenes, etc.

Las variables se definen con un simbolo "$" al inicio.

``` scss
//Ejemplo:

$color-ppal: #f2c74f;
$color-secundario: #333;

``` 
#### Mixins

Uno de los conceptos que más promueve Sass es la reutilización de estilos para ello presenta las herramientas de los mixins, los cuales son bloques reutilizables de código para así  ahorrar tiempo y esfuerzo en desarrollo.

``` scss
//Ejemplo:

@mixin large-text {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: $color-ppal;
}

``` 
En este caso se está declarando un mixin que contiene propiedades que se repiten bastante durante todo el proyecto, ahora revisemos como se agregaría este mixin dentro de los estilos

``` scss
.titulos {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}

