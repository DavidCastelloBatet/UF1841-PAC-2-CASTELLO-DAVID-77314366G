/_ CSS3 _/

/_ Ejemplo de comentario _/

/_
Podemos insertar el CSS en un documento de HTML de tres formas distintas:
En línea:
<element style="[declaració css]"></element>
Un ejemplo: <p style="color:blue"></p>
Declaración de estilos en la cabecera del documento:
<!Doctype>
<html>
<head>
<style>
p { color: red; text-align: center; }
</style>
</head>
<body>
</body>
</html>
Declaración de estilos en un archivo enlazado:
<!Doctype>
<html>
<head>
<link rel="stylesheet" href="" type="text/css">
</head>
<body>
</body>
</html>
_/

/\* SINTAXI CSS

    Las hojas de estilo definen las reglas que se van a aplicar a los elementos HTML.

    Las reglas se componen de:
    	Selector { Declaración; Declaración; }
    donde una "Declaración" está compuesta por "propietat:valor;"
    	Un ejemplo:
    	p { color: red; text-align: center; }

    También hay la posibilidad de escribir diferentes propiedades en una sola línea. Son lo que se llaman propiedades taquigráficas:
    Por ejemplo:
    	background-color: #ffffff;
    	background-image: url("img_tree.png");
    	background-repeat: no-repeat;
    	background-position: right top;
    Taquigráficamente se podria escribir como:
    	background: #ffffff url("img_tree.png") no-repeat right top;
    	Siguiendo el orden:
    		background-color
    		background-image
    		background-repeat
    		background-attachment
    		background-position

\*/

/\* Páginas de referencia
https://www.w3schools.com/css/default.asp
https://developer.mozilla.org/es/docs/Web/CSS
Relación de instrucciones
https://www.w3schools.com/cssref/default.asp
https://developer.mozilla.org/es/docs/Web/CSS/Referencia_CSS

    Valores predeterminados
    	https://www.w3schools.com/cssref/css_default_values.asp

\*/

/\*
ÍNDICE
Tipos de selectores
Prioridad en la ejecución
Unidades de medida
Los colores
Contenidos
Fuente
Imágenes
Contenedores
Párrafos
Enlaces
Listas
Tablas
Capas
Contenidos funcionando como agrupaciones
Relación del contenido y el contenedor
Propiedades de los contenedores
Tamaños
Bordes y márgenes
Formatos de fondo
Posición
Addición de información
Efectos
Visibilidad
Cambiar el tamaño
Cambiar el cursor
Transformaciones 2D
Transformaciones 3D
Transiciones
Transición + Transformación
Animaciones
Condicionales
NO SE EXPLICAN

    Variables CSS

\*/

/\* TIPOS DE SELECTORES
ordenados de más genéricos a más concretos
La lista completa en: https://www.w3schools.com/cssref/css_selectors.asp

    Únicos
    	Universal, para todos los elementos
    		*

    	Por classe
    		.nombreDeLaClase { }
    		ejemplo:
    			HTML	<div class="hola"> contenido </div>
    			CSS		.hola{ }

    	Por nombre de elemento
    		nombreDelElemento { }
    		ejemplo:
    			HTML	<div>Contenido</div>
    			CSS		div{ }

    	Por atributo
    		[atributo='valor']
    		ejemplo:
    			HTML	<input type="text" required>
    			CSS		[required]{ }

    		[atributo~="value"]
    		Para seleccionar elementos con un valor de atributo que contiene una palabra específica.
    		ejemplo:
    			CSS		[title~="flower"]{ }

    		[atributo|="value"]
    		Seleccionar elementos con el atributo especificado comenzando con el valor especificado.
    		ejemplo:
    			CSS		[class|="top"]{ }

    		[atributo^="value"]
    		Seleccionar elementos cuyo valor de atributo comienza con un valor especificado.
    		ejemplo:
    			CSS		[class^="top"]{ }

    		[atributo$ = "valor"]
    		Seleccionar elementos cuyo valor de atributo termina con un valor especificado.
    		ejemplo:
    			CSS		[class$="test"]{ }

    		[atributo* = "valor"]
    		Seleccionar elementos cuyo valor de atributo contiene un valor especificado.
    		ejemplo:
    			CSS		[class*="test"]{ }


    	Pseudoclases dinámicas
    		referencia:comportamiento
    		ejemplos:
    			a:link		Enlaces normales. No han sido visitados.
    			a:visited	Visitados.
    			a:hover		Mientras el cursor pasa por encima.
    			a:active	Cuando está siendo clicado.
    		A veces hay reglas de orden:
    			a: hover DEBE ir después de un: enlace y un: visitado
    			a: active DEBE venir después de a: hover
    		ejemplo:
    			HTML	<a></a>
    			CSS		a:visited{}

    	Pseudoelementos
    		elemento ::posicion { }
    		ejemplo:
    			HTML	<article></article>
    			CSS		article ::first-letter{}

    	Pseudoclases estructurales
    		[referencia]:posicion { }
    		ejemplo:
    			HTML	<div><p></p></div>
    			CSS		:first-child{}
    					p:nth-child(2){}
    					p:nth-child(3n+0){}
    					p:nth-child(odd){}
    					p:nth-child(even){}

    	Por ID
    		#nombreDelId { }
    		ejemplo:
    			HTML	<div id="hola"> contenido </div>
    			CSS		#hola{ }



    Combinaciones

    	Selectores descendientes
    		Selecciona todos los elementos que son descendientes de un elemento especificado.
    		El separador de las referencias es un espacio " ".
    		ejemplo:
    			HTML
    				<div>
    					<p></p>					   <-- Es un descendiente a la vez que hijo.
    					<section><p></p></section> <-- Es un descendiente, no un hijo.
    				</div>
    			CSS
    				div p {}

    	Selector de hijos
    		Selecciona todos los elementos que son hijos de un elemento especificado.
    		El separador de las referencias es un símbolo ">".
    		ejemplo:
    			HTML
    				<div>
    					<p></p>					   <-- Es un descendiente a la vez que hijo.
    					<section><p></p></section> <-- Es un descendiente, no un hijo.
    				</div>
    			CSS
    				div > p {}

    	Selector de hermanos adyacentes
    		Selecciona un elemento que está directamente después de otro elemento específico.
    		Los elementos hermanos deben tener el mismo elemento padre.
    		"Adyacente" significa "inmediatamente siguiente".
    		El separador de las referencias es un símbolo "+".
    		ejemplo:
    			HTML
    				<div></div>
    				<p></p>					   <-- Es un elemento adyacente, en este caso de un "div".
    			CSS
    				div + p {}

    	Selector general de hermanos
    		Selecciona todos los elementos que son hermanos de un elemento especificado.
    		El separador de las referencias es un símbolo "~" (Se corresponde al carácter Alt 126 de la tabla ASCII)
    		ejemplo:
    			HTML
    				<div></div>
    				<p></p>					   <-- Son elementos hermanos.
    				<p></p>					   <-- Son elementos hermanos.
    			CSS
    				div ~ p {}

    	Selector múltiple
    		Permite seleccionar varios elementos.
    			HTML
    				<div></div>
    				<input>
    				<p></p>
    			CSS
    				div, input, p {}


    Reglas de selección
    	La jerarquía de especifidad.

    		Cada selector tiene su lugar en la jerarquía de especificidad. Hay cuatro categorías que definen el nivel de especificidad de un selector:

    			Estilos en línea
    				Un estilo en línea se adjunta directamente al elemento que se va a diseñar. Ejemplo: <h1 style = "color: #ffffff;">.
    				Especifidad = 1000 (binário)

    			ID
    				Una ID es un identificador único para los elementos de la página, como #navbar.
    				Especifidad = 0100 (binário)

    			Clases, atributos y pseudoclases
    				Esta categoría incluye .classes, [atributos] y pseudoclases como: hover,: focus, etc.
    				Especifidad = 0010 (binário)

    			Elementos y pseudoelementos
    				Esta categoría incluye nombres de elementos y pseudoelementos, como h1, div,: before y: after.
    				Especifidad = 0001 (binário)

    		Teniendo en cuenta que:
    			0	0	0	0	=	0
    			0	0	0	1	=	1
    			0	0	1	0	=	2
    			0	0	1	1	=	3
    			0	1	0	0	=	4
    			0	1	0	1	=	5
    			0	1	1	0	=	6
    			0	1	1	1	=	7
    			1	0	0	0	=	8
    			1	0	0	1	=	9
    			1	0	1	0	=	10
    			1	0	1	1	=	11
    			1	1	0	0	=	12
    			1	1	0	1	=	13
    			1	1	1	0	=	14
    			1	1	1	1	=	15

    		Podemos calcular cuál elemento será el que tenga más peso.
    		Y, ante un empate (Igual especificidad), la última regla será la que se aplique.

    		El selector universal y los valores heredados tienen una especificidad de 0.

\*/

/\* PRIORIDAD EN LA EJECUCIÓN

    En función de dónde se encuentra la instrucción
    	Las reglas en línea (atributo style),
    	tienen prioridad sobre las hojas de estilo internas (elemento style),
    	estas, a su vez, sobre las externas
    	y, finalmente, los parámetros predeterminados del navegador.


    Segun el tipo:
    	Declaraciones importantes del navegador.
    	Declaraciones importantes del usuario.
    	Declaraciones importantes del autor.
    	Declaraciones normales del autor.
    	Declaraciones normales del usuario.
    	Declaraciones normales del navegador.

    	Siendo el tipo !important un tipo de comodín.
    	Permite declarar un atributo de forma que este tenga prevalencia sobre otras declaraciones posteriores.
    	Desactiva las reglas de cascada.


    Y dentro de la regla:
    	Para ordenar las reglas de cada categoría las reglas se ordenan de más a menos específicas.
    	Se asigna a cada regla un número según los selectores que contenga.
    	Para cada regla, hay que contar:
    		• El número de selectores por id. Llamaremos a ese número A.
    		• El número de selectores por clase, por atributos y por pseudoclase. Lla-
    		maremos a ese número B.
    		• El número de selectores por tipo elemento y por pseudoelemento. Llama-
    		remos a ese número C.
    	La prioridad de la regla (specificity) se obtiene concatenando los números A, B y C.

\*/

/\* UNIDADES DE MEDIDA

    ABSOLUTAS

    	Longitud

    		cm 		centimeters
    		mm 		millimeters
    		in 		inches (1in = 96px = 2.54cm)
    		px * 	pixels (1px = 1/96th of 1in)
    		pt 		points (1pt = 1/72 of 1in)
    		pc 		picas (1pc = 12 pt)

    	Puntos de pantalla (Píxeles)
    		div{
    			height: 100px;
    		}

    RELATIVAS

% Relativo al elemento padre

    	em
    		Relativo al tamaño de fuente del elemento (2em significa 2 veces el tamaño de la fuente actual)
    		Ejemplo
    			footer {
    				width : 5em;
    				height : 3em;
    			}

    	ex
    		Relativo a la altura x de la fuente actual (rara vez se usa).

    	ch
    		Relativo al ancho del "0" (cero).

    	porcentajes
    		Ejemplo:
    			section {
    				width : 80%;
    				height : 20%;
    			}
    	rem
    		Relativo al tamaño de fuente del elemento raíz.

    	vh
    		Relativo al 1% de la altura de la ventana gráfica *

    	ViewPort
    		Relativo al 1% del ancho de la ventana gráfica *
    		Ejemplo:
    			font-size:10vw;

    	vmin
    		Relativo al 1% de la dimensión más pequeña de la ventana gráfica *

    	vmax
    		Relativo al 1% de la dimensión más grande de la ventana gráfica *

\*/

/\* LOS COLORES

    Por nombre
    	background-color: Tomato;

    Por referencia RGB
    	background-color: rgb(255, 99, 71);

    Por referencia RGB en HEXadecimal
    	background-color: #ff6347;

    Por referencia HSL
    	background-color: hsl(9, 100%, 64%);

\*/

/\* CONTENIDOS: FUENTES
TIPOGRAFÍA
Familia de la fuente
Única
font-family: sans-serif;
Primera con alternativas
font-family: Tahoma, Verdana, sans-serif;
Nota:
Fuentes comunes a todos los ordenadores (web safe fonts):
Arial (sans-serif)
Verdana (sans-serif)
Helvetica (sans-serif)
Tahoma (sans-serif)
Trebuchet MS (sans-serif)
Times New Roman (serif)
Georgia (serif)
Garamond (serif)
Courier New (monospace)
Brush Script MT (cursive)
Externas
Primero linkamos en HTML: <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Sofia">
Después la usamos: font-family: "Sofia", sans-serif;

    	Transformación de fuentes: Mayúsculas y minúsculas

    		text-transform: uppercase;	Todo en mayúsculas.
    		text-transform: lowercase;	Todo en minúsculas.
    		text-transform: capitalize;	Primera letra de cada palabra en mayúscula el resto en minúsculas.

    		font-variant: small-caps;	Todo en mayúsculas, pero la primera letra más grande.

    	Tamaño
    		font-size: 10px;
    		font-size: 2.4em;
    		font-size:10vw; (Versión responsive: viewport width)

    	Distancias

    		Entre letras
    		(Puede ser con valor positivo o negativo)
    			letter-spacing: 3px;

    		Espacio entre palabras
    		word-spacing: 10px;

    ESTILO / ASPECTO
    	Color
    		color:Tomato;

    	Estándar
    		font-style: normal;
    		font-variant: normal;

    	Cursiva
    		font-style: italic;
    		font-style: oblique;

    	Grosor / "Negrita"
    		font-weight:100;
    		font-weight: bold;
    		font-style: black;

    	Texto y líneas
    		Línea encima de los carácteres
    			text-decoration: overline;

    		Línea tachando los carácteres
    			text-decoration: line-through;

    		Línea debajo de los carácteres (Subrayados)
    			text-decoration: underline;

    		Sin decoración
    			text-decoration: none;
    			ejemplo:
    				a{
    					text-decoration: none;
    				}
    			Para practicar:
    			https://www.w3schools.com/css/tryit.asp?filename=trycss_text-decoration

    	Sombras
    		text-shadow:
    			DesplazamientoHorizontal
    			DesplazamientoVertical
    			CantidadDifuminado
    			ColorDeLaSombra;
    		Por ejemplo:
    			text-shadow: 2px 2px 1px grey;


    Taquigrafia
    	Orden:
    		font-style
    		font-variant
    		font-weight
    		font-size/line-height (obligatorio)
    		font-family (obligatorio)
    	Por ejemplo:
    		font: italic small-caps bold 12px/30px Georgia, serif;

\*/

/_ CONTENIDOS: IMAGENES
POSICIONAR IMAGEN
Para centrar una imagen, establezca el margen izquierdo y derecho en auto y conviértalo en un blockelemento:
display: block;
margin-left: auto;
margin-right: auto
ICONOS
Externos
Origenes:
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<script src="https://kit.fontawesome.com/a076d05399.js"></script>
<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
Ejemplo
Añadir origen en HTML: <script src="https://kit.fontawesome.com/a076d05399.js"></script>
Asignar el estilo: <i class="fas fa-cloud">
_/

/_ CONTENEDORES
Todos los elementos HTML se pueden considerar como cuadros.
En CSS, el término "modelo de caja" se usa cuando se habla de diseño y maquetación.
El modelo de caja CSS es esencialmente una caja que envuelve cada elemento HTML.
De dentro hacia fuera, consiste en:
Contenido: El contenido del cuadro, donde aparecen el texto y las imágenes.
Relleno: Limpia un área alrededor del contenido.
El acolchado es transparente
Borde: un borde que rodea el relleno y el contenido.
Margen: borra un área fuera del borde.
El margen es transparente
_/

/\* CONTENEDORES: PÁRRAFOS

    Dirección del texto

    	direction: rtl;
    	(ltr: Izquierda a derecha)
    	(rtl: Derecha a izquierda)


\*/

/\* CONTENEDORES: ENLACES

    "Decoración"
    	La misma que usamos para text:
    	text-decoration: none;
    	text-decoration: underline;
    	background-color: yellow;
    	...

Trucos:
Haciendo pasar un link por un enlace:
a:link, a:visited {
background-color: #f44336;
color: white;
padding: 14px 25px;
text-align: center;
text-decoration: none;
display: inline-block;
border-radius: 50px;
}

a:hover, a:active {
background-color: red;
}

Hacer que el link "reaccione" al paso del cursor:
a: link {color:#ff0000;}
a: visited {color:#0000ff;}
a: hover {color:#ffcc00;}
a: hover {font-size:150%;}
\*/

/\* CONTENEDORES: LISTAS

    Círculo
    	list-style-type: circle;

    Cuadrado
    	list-style-type: square;

    Números romanos
    	list-style-type: upper-roman;

    Letras
    	list-style-type: lower-alpha;

    Una imagen
    	list-style-image: url('sqpurple.gif');

    Sin marca
    	list-style-type: none;

    Sin sangria (Por defecto)
    	list-style-position: outside;

    Con sangria
    	list-style-position: inside;




Nota:
Las propiedades que se pueden definir son:
list-style-image (Para establecer una imagen al punto.)
list-style-position (Para establecer la posición del marcador.)
list-style-type (Para establecer el tipo de marcador.)
Declarando todas las propiedades en unsa sola línea:
El orden siempre debe ser:
list-style-type
list-style-position
list-style-image
Un ejemplo:
list-style: square inside url("sqpurple.gif");
Trucos:
Le podéis añadir márgenes con colores y otros efectos.
Por ejemplo:
ol li {
background: #ffe5e5;
padding: 5px;
margin-left: 35px;
}

    ul li {
      background: #cce5ff;
      margin: 5px;
    }

Para quitar la sangria:
Sin sangria
margin: 0;
padding: 0;
\*/

/\* CONTENEDORES: TABLAS

    Referencias: table, tr, th, td


    Ancho de tabla, celdas, ...
    	width: 400px;
    	width: 100%;

    Altura de las celdas, ...
    (No se puede aplicar a Tabla)
    	height: 700px;

    Mostrar o esconder las celdas vacías
    	https://www.w3schools.com/cssref/pr_tab_empty-cells.asp
    	Valores: show, hide, initial, inherit
    	empty-cells: hide;

    Fondo
    	background-color: #4CAF50;

    Contorno
    	https://www.w3schools.com/cssref/pr_border.asp
    	border: 1px solid black;
    	border-bottom: 1px solid #ddd;

    Entre bordes
    	Mantener una distancia
    		https://www.w3schools.com/cssref/pr_border-spacing.asp
    		border-spacing

    	Colapsar bordes
    		Los bordes de la tabla se fusionan en un solo borde
    		https://www.w3schools.com/cssref/pr_border-collapse.asp
    		border-collapse: collapse;

    Maquetación
    	Cómo se reparte el ancho de la tabla entre las columnas.
    	Valores: auto, fixed, initial, inherit
    	table-layout: auto;


    Posición del pie de la tabla
    	caption-side: bottom;

\*/

/\* CONTENEDORES: CAPAS

\*/

/\* CONTENIDOS FUNCIONANDO COMO AGRUPACIONES

    En bloque
    	Tratar el contenido cómo bloques.
    		diplay: valor

    		Posibles valores

    			inline 				Muestra un elemento como un elemento en línea (como <span>).
    								Las propiedades de altura y ancho no tendrán efecto.
    			block 				Muestra un elemento como un elemento de bloque (como <p>).
    								Comienza en una nueva línea y ocupa todo el ancho.
    			contents 			Hace que el contenedor desaparezca,
    								haciendo que los elementos secundarios del elemento
    								pasen al siguiente nivel en el DOM.
    			flex 				Muestra un elemento como un contenedor flexible a nivel de bloque.
    			grid 				Muestra un elemento como un contenedor de grid a nivel de bloque.
    			inline-block 		Muestra un elemento como un contenedor de bloques a nivel de línea.
    								El elemento en sí tiene el formato de un elemento en línea, pero puede aplicar valores de alto y ancho.
    			inline-flex 		Muestra un elemento como un contenedor flexible de nivel en línea.
    			inline-grid 		Muestra un elemento como un contenedor de cuadrícula a nivel de línea.
    			inline-table 		El elemento se muestra como una tabla de nivel en línea.
    			list-item			Deja que el elemento se comporte como un elemento <li>
    			run-in 				Muestra un elemento como bloque o en línea, según el contexto.
    			table 				Deja que el elemento se comporte como un elemento <table>.
    			table-caption		Deja que el elemento se comporte como un elemento <caption>.
    			table-column-group 	Deja que el elemento se comporte como un elemento <colgroup>.
    			table-header-group 	Deja que el elemento se comporte como un elemento <thead>.
    			table-footer-group 	Deja que el elemento se comporte como un elemento <tfoot>.
    			table-row-group 	Deja que el elemento se comporte como un elemento <tbody>.
    			table-cell 			Deja que el elemento se comporte como un elemento <td>.
    			table-column 		Deja que el elemento se comporte como un elemento <col>.
    			table-row 			Deja que el elemento se comporte como un elemento <tr>
    			initial 			Establece esta propiedad en su valor predeterminado.
    			inherit 			Hereda esta propiedad de su elemento padre.

    		Ejemplo:
    			display: block;		Trata el contenido cómo un bloque.

    	Para saver más de display:
    		https://www.w3schools.com/cssref/pr_class_display.asp
    		https://www.w3schools.com/cssref/playit.asp?filename=playcss_display&preval=inline

    En columnas
    	Para crear automáticamente columnas tenemos:

    		columns 			Establece el ancho de columna y el recuento de columnas de forma abreviada.

    		column-count 		Especifica el número de columnas en las que debe dividirse un elemento.
    		column-fill 		Especifica cómo llenar las columnas.
    		column-gap 			Especifica el espacio entre las columnas
    		column-rule 		Establece todas las propiedades de column-rule-(propiedad).
    		column-rule-color 	Especifica el color de la regla entre columnas.
    		column-rule-style 	Especifica el estilo de la regla entre columnas.
    		column-rule-width 	Especifica el ancho de la regla entre columnas.
    		column-span 		Especifica cuántas columnas debe abarcar un elemento.
    		column-width 		Especifica un ancho óptimo sugerido para las columnas.


    	Por ejemplo:
    		column-count: 3;	Crea tres columnas.

    Distancias
    	Entre filas
    		line-height: 0.8;

\*/

/\* RELACIÓN DEL CONTENIDO Y EL CONTENEDOR

    	Alienación del texto

    		Horizontal
    			text-align: left;		A la izquierda
    			text-align: right;		A la derecha
    			text-align: center;		Centrado
    			text-align: justify;	Justificado

    		Alineación vertical
    			vertical-align: top;	Arriba
    			vertical-align: middle;	Medio
    			vertical-align: bottom;	Inferior

    	Sangria
    		text-indent: 20px;


    	Ancho del margen
    		Propiedades
    			margin			Margen para todos los lados.
    			margin-top		Margen superior.
    			margin-right	Margen derecho.
    			margin-bottom	Margen inferior.
    			margin-left		Margen izquierdo.

    		Posibles valores:
    			auto:		el navegador calcula el margen
    			longitud:	Un margen en px, pt, cm, etc.
    			%:			Un margen en% del ancho del elemento contenedor.
    			heredar:	El margen debe heredarse del elemento principal.

    		Ejemplos:
    			margin: 5px;
    			margin-top:    10px;
    			margin-bottom: 10px;
    			margin-right:  10px;
    			margin-left:   inherit;
    			margin:        auto;

    	Fusionar márgenes
    		Los márgenes superior e inferior de los elementos a veces se contraen en un único margen que es igual al mayor de los dos márgenes.
    		¡Esto no sucede en los márgenes izquierdo y derecho! ¡Solo márgenes superior e inferior!

    		margin: 20px 0 0 0;

    		Por ejemplo:
    			h1 { margin: 0 0 50px 0; }
    			h2 { margin: 20px 0 0 0; }

    	Cómo manejar los espacios
    		La white-spacepropiedad especifica cómo se maneja el espacio en blanco dentro de un elemento.
    		white-space: nowrap;

    	Desbordamiento

    		Los valores permitidos son:

    			visible	El desbordamiento no está recortado.
    					El contenido se renderiza fuera de la caja del elemento.
    					Opción por defecto.
    			hidden	El desbordamiento se recorta y el resto del contenido será invisible
    			scroll	Se recorta el desbordamiento y se agrega una barra de desplazamiento para ver el resto del contenido
    			auto	Similar a scroll, pero agrega barras de desplazamiento solo cuando es necesario

    			Ejemplos:
    				overflow: scroll;
    				overflow-x:auto;	Evita que el contenido se expanda al contenedor y en su lugar aparezca una barra de desplazamiento dentro del contenedor.

    	Flotar
    		Float
    			La float propiedad CSS especifica cómo debe flotar un elemento.
    			Los valores permitidos son:
    				left:		el elemento flota a la izquierda de su contenedor
    				right:		el elemento flota a la derecha de su contenedor
    				none:		el elemento no flota (se mostrará justo donde aparece en el texto). Esto es predeterminado
    				heredar:	el elemento hereda el valor flotante de su padre
    			Ejemplo:
    				float: right;
    		Clear
    			La propiedad clear especifica qué elementos pueden flotar junto al elemento borrado y en qué lado.
    			Los valores permitidos son:
    				none:		Permite elementos flotantes en ambos lados. Esto es predeterminado
    				left:		No se permiten elementos flotantes en el lado izquierdo
    				right:		No se permiten elementos flotantes en el lado derecho
    				ambos:		No se permiten elementos flotantes ni en el lado izquierdo ni en el derecho
    				heredar:	El elemento hereda el valor claro de su padre

    			Ejemplo:
    				clear: left;


    	Acolchamiento
    		Distancia del contenido respecto a los márgenes
    			padding:20px;

    		Propiedades:
    			padding:	Propiedad abreviada.
    			padding-top: 	Acolchado superior de un elemento.
    			padding-right:	Acolchado derecho de un elemento.
    			padding-bottom: Acolchado inferior de un elemento.
    			padding-left: 	Acolchado izquierdo de un elemento.

    		Valores permitidos:

    			longitud : En px, pt, cm, etc.
    			%        : En % del ancho del elemento contenedor.
    			heredar  : El relleno se hereda del elemento principal.

    			No se permiten valores negativos.


    	Flexbox
    		Es un contenedor flexible con elementos.
    		Las propiedades del contenedor flexible son:

    			flex-direction
    				Define en qué dirección el contenedor quiere apilar los elementos flexibles.
    				Ejemplo
    					El valor de la columna apila los elementos flexibles verticalmente (de arriba a abajo).
    					.contenedorFlex {
    						display: flex;
    						flex-direction: column;
    					}

    			flex-wrap
    				Especifica si los elementos flexibles deben ajustarse o no.
    				Ejemplo
    					Los elementos flexibles se ajustarán si es necesario, en orden inverso.
    					.contenedorFlex {
    						display: flex;
    						flex-wrap: wrap-reverse;
    					}

    			flex-flow
    				Propiedad abreviada para establecer las propiedades flex-direction y flex-wrap.
    				Ejemplo
    					.contenedorFlex {
    						display: flex;
    						flex-flow: row wrap;
    					}

    			justify-content
    				Alinea los elementos flexibles.
    				Ejemplo
    					El valor central alinea los elementos flexibles en el centro del contenedor.
    					.contenedorFlex {
    						display: flex;
    						ustify-content: center;
    					}


    			align-items
    				Alinea los elementos flexibles.
    				Ejemplo
    					Alinea a las líneas de base de los elementos flexibles.
    					.contenedorFlex {
    						display: flex;
    						height: 200px;
    						align-items: baseline;
    					}


    			align-content
    				Alinea las líneas flexibles.
    				Ejemplo
    					Muestra las líneas flexibles al inicio del contenedor.
    					.contenedorFlex {
    						  display: flex;
    						  height: 600px;
    						  flex-wrap: wrap;
    						  align-content: flex-start;
    					}

    		Ejemplo	de centrado perfecto
    			.contenedorFlex
    			{
    				display: flex;
    				height: 300px;
    				justify-content: center;
    				align-items: center;
    			}

    		Elementos secundarios (elementos)
    			Los elementos secundarios directos de un contenedor flexible se convierten automáticamente en elementos flexibles (flex).

    			Las propiedades del elemento flexible son:

    				order
    					Especifica el orden de los elementos flexibles.
    					Ejemplo
    						Cambia el orden de los elementos flexibles.
    						<div class="flex-container">
    							<div style="order: 3">1</div>
    							<div style="order: 2">2</div>
    							<div style="order: 4">3</div>
    							<div style="order: 1">4</div>
    						</div>

    				flex-grow
    					Especifica cuánto crecerá un elemento flexible en relación con el resto de los elementos flexibles.
    					Ejemplo
    						El tercer elemento flexible crezca ocho veces más rápido que los otros elementos flexibles.
    						<div class="flex-container">
    							<div style="flex-grow: 1">1</div>
    							<div style="flex-grow: 1">2</div>
    							<div style="flex-grow: 8">3</div>
    						</div>

    				flex-shrink
    					Especifica cuánto se encogerá un elemento flexible en relación con el resto de los elementos flexibles.
    					Ejemplo
    						<div class="flex-container">
    							<div>1</div>
    							<div>2</div>
    							<div style="flex-shrink: 0">3</div>
    							<div>4</div>
    							<div>5</div>
    							<div>6</div>
    							<div>7</div>
    							<div>8</div>
    							<div>9</div>
    							<div>10</div>
    						</div>

    				flex-basis
    					Especifica la longitud inicial de un elemento flexible.
    					Ejemplo
    						<div class="flex-container">
    							<div>1</div>
    							<div>2</div>
    							<div style="flex-basis: 200px">3</div>
    							<div>4</div>
    						</div>

    				flex
    					Propiedad es una propiedad abreviada para las propiedades flex-grow, flex-shrinky flex-basis.
    					Ejemplo
    						<div class="flex-container">
    							<div>1</div>
    							<div>2</div>
    							<div style="flex: 0 0 200px">3</div>
    							<div>4</div>
    						</div>

    				align-self
    					Especifica la alineación del elemento seleccionado dentro del contenedor flexible.
    					Anula la alineación predeterminada establecida por la align-itemspropiedad del contenedor .
    					Ejemplo
    						<div class="flex-container">
    							<div>1</div>
    							<div>2</div>
    							<div style="align-self: center">3</div>
    							<div>4</div>
    						</div>

    		Flex Responsive
    			(Mirar la página https://www.w3schools.com/css/css3_flexbox_responsive.asp)


    	Sintaxi taquigráfica
    		margin-top
    		margin-right
    		margin-bottom
    		margin-left

    		margin: 25px 50px 75px 100px;
    		padding: 25px 50px 75px 100px;

    */

/\* CONTENEDORES: PROPIEDADES: POSICIÓN
Posición
Position
Especifica el tipo de método de posicionamiento utilizado para un elemento.
Posibles valores:
static No se posiciona de ninguna manera especial.
Siempre se posiciona de acuerdo con el flujo normal de la página.
Los elementos de posición estática no se ven afectados por las propiedades superior, inferior, izquierda y derecha.
relative Posicionado en relación con su posición normal.
Establecer las propiedades superior, derecha, inferior e izquierda de un elemento en una posición relativa hará que se ajuste lejos de su posición normal. El resto del contenido no se ajustará para encajar en ningún espacio dejado por el elemento.
fixed Posicionado en relación con la ventana gráfica.
Siempre permanece en el mismo lugar incluso si se desplaza la página.
Las propiedades superior, derecha, inferior e izquierda se utilizan para colocar el elemento.
absolute Posicionado en relación con el antecesor posicionado más cercano
(en lugar de posicionado en relación con la ventana gráfica, como fijo).
Sin embargo; si un elemento de posición absoluta no tiene antepasados ​​de posición, utiliza el cuerpo del documento y se mueve junto con el desplazamiento de página.
sticky Se posiciona según la posición de desplazamiento del usuario.
Se pega en la parte superior de la ventana.
Ejemplo
Position: absolute;
Alineación
left: 0px; Alineación izquierda
float: left; Flotando a la izquierda
right: 0px; Alineación derecha
float: right; Flotando a la derecha
Centrar
Para centrar horizontalmente un elemento de bloque (como <div>), use margin: auto;
Establecer el ancho del elemento evitará que se estire hasta los bordes de su contenedor.
El elemento ocupará el ancho especificado y el espacio restante se dividirá en partes iguales entre los dos márgenes.
Ejemplo
margin: auto;
width: 50%;

    Profundidad
    	Especifica si un elemento está más cerca de nosotros o más al fondo (apilamiento).
    	Un elemento con un orden de pila mayor siempre está delante de un elemento con un orden de pila menor.

    	Valores permitidos:
    		auto 		Establece el orden de la pila igual a sus padres.
    					Este valor es predeterminado.
    		number 		Establece el orden de pila del elemento.
    					Se permiten números negativos
    		initial 	Establece esta propiedad en su valor predeterminado.
    		inherit 	Hereda esta propiedad de su elemento padre.

    	Ejemplo
    		z-index: -1;

\*/

/\* CONTENEDORES: PROPIEDADES: TAMAÑO

    ancho + relleno + borde = ancho real de un elemento
    alto  + relleno + borde = alto real de un elemento

    Valores permitidos:

    	auto	El navegador calcula la altura y el ancho.
    			Es el valor predeterminado
    	length	Define la altura / ancho en px, cm, etc.
    	%		Define la altura / ancho en porcentaje del bloque contenedor
    	initial	Establece la altura / ancho a su valor predeterminado
    	inherit	La altura / ancho se heredará de su valor principal.

    Ancho:
    	width: 500px;

    	Ancho máximo
    		Establece un ancho máximo de un elemento impidiendo que el valor utilizando por la propiedad width lo supere.
    		max-width: 500px;
    	Ancho máximo
    		Establece el ancho mínimo de un elemento.
    		min-width: 100px;

    Alto:
    	height: 200px

    	Alto máximo
    		Establece la altura máxima de un elemento.
    		max-width: 500px;
    	Alto máximo
    		Establece la altura mínima de un elemento.
    		min-width: 100px;

    Box-Sizing
    	La propiedad box-sizing nos permite incluir el relleno y el borde en el ancho y alto total de un elemento.
    	Si establece "box-sizing: border-box;" un elemento, el relleno y el borde se incluyen en el ancho y el alto.
    	Dado que el resultado de usar "box-sizing: border-box;" es mucho mejor, muchos desarrolladores quieren que todos los elementos de sus páginas funcionen de esta manera.

\*/

/\* CONTENEDORES: PROPIEDADES: BORDES

    Ancho/grossor del borde
    	border-width: 10px;
    	border-width: medium;

    Estilo de borde
    	border-style: dotted;
    	Posibles valores
    		dotted		: Borde punteado.
    		dashed		: Borde punteado.
    		double		: Borde doble.
    		groove		: Borde acanalado en 3D.
    					  El efecto depende del valor del color del borde.
    					  El efecto depende del valor del color del borde.
    		inset		: Borde borde insertado en 3D.
    					  El efecto depende del valor del color del borde.
    		outset		: Borde inicial 3D.
    		ridge		: Borde estriado en 3D.
    		solid		: Borde sólido.
    					  El efecto depende del valor del color del borde.

    		none		: No define ningún borde.
    		hidden		: Borde oculto.

    Color del borde CSS
    	border-color: red;

    Contornos
    	Límite de los márgenes, fuera de los bordes.

    	Tienen las siguientes propiedades de esquema:
    		outline-style
    		outline-color
    		outline-width
    		outline-offset
    		outline

    	A nivel de estilo podemos definir:
    		dotted - Define un contorno punteado
    		dashed - Define un contorno punteado
    		solid - Define un contorno sólido
    		double - Define un doble contorno
    		groove - Define un contorno acanalado en 3D
    		ridge - Define un contorno estriado en 3D
    		inset - Define un contorno de inserción 3D
    		outset - Define un contorno inicial 3D
    		none - No define ningún contorno
    		hidden - Define un contorno oculto.

    		Ejemplo:
    			outline-style: dotted;

    	El ancho del contorno y puede tener uno de los siguientes valores:
    		delgado (normalmente 1 px)
    		medio (normalmente 3px)
    		grueso (normalmente 5px)
    		Un tamaño específico (en px, pt, cm, em, etc.)

    		Ejemplo:
    			outline-width: thin;

    	El color se puede establecer mediante:

    		nombre: Nombre de color, como "rojo"
    		HEX:	Valor hexadecimal, como "# ff0000"
    		RGB:	Valor RGB, como "rgb (255,0,0)"
    		HSL:	Valor HSL, como "hsl (0, 100%, 50%)"
    		invert: Realiza una inversión de color.
    				Así se garantiza que el contorno sea visible, independientemente del color de fondo.

    	Desplazamiento de contorno
    		outline-offset: 15px;

    	Redondeados
    		border-radius: 5px;



    Sintaxi taquigráfica:
    	Orden de la sintaxi taquigráfica
    		border-width
    		border-style (necesario)
    		border-color

    	Ejemplos:
    		margin: 5px 10px 15px 20px;
    		border:2px solid Tomato;
    		border-style: dotted solid;
    		border-color: red green blue yellow;
    		border-radius: 5px 10px 15px 20px;


\*/

/\* CONTENEDORES: PROPIEDADES: FONDO

    Color de fondo CSS
    	background-color:DodgerBlue;
    	background: rgba(0, 128, 0, 0.3)

    Imagen de fondo CSS
    	background-image: url("paper.gif");

    Repetición de fondo CSS

    	background-image: url("gradient_bg.png");		background-repeat: repeat-x;

    	No repetición
    	background-image: url("gradient_bg.png");		background-repeat: no-repeat;

    Posición de fondo CSS
    	background-image: url("img_tree.png");
    	background-repeat: no-repeat;
    	background-position: right top;

    Fondo desplazándose o fijo
    (no se desplazará con el resto de la página)
      background-image: url("img_tree.png");
      background-repeat: no-repeat;
      background-position: right top;
      background-attachment: fixed;


    Todas las propiedades de fondo de CSS
    	background
    	background-attachment
    	background-clip
    	background-color
    	background-image
    	background-origin
    	background-position
    	background image
    	background-repeat
    	background-size

\*/

/\* ADDICIÓN DE INFORMACIÓN
Contadores
Los contadores CSS son como "variables". Los valores de las variables se pueden incrementar mediante reglas CSS (que rastrearán cuántas veces se usan).

    	Para trabajar con contadores CSS usaremos las siguientes propiedades:

    		counter-reset - Crea o reinicia un contador
    		counter-increment - Incrementa un valor de contador
    		content - Inserta contenido generado
    		counter()o counters()función: agrega el valor de un contador a un elemento

    	Para utilizar un contador CSS, primero debe crearse con counter-reset.

    	Ejemplo
    	  counter-reset: section;
    	  counter-increment: section;
    	  content: "Section " counter(section) ": ";

    Contadores de anidación
    	Se aprovechan las herramientas anteriores para crear subcontadores.

    	Ejemplo
    		body { counter-reset: section; }
    		h1 { counter-reset: subsection; }
    		h1::before {
    			counter-increment: section;
    			content: "Section " counter(section) ". ";
    		}
    		h2::before {
    		  counter-increment: subsection;
    		  content: counter(section) "." counter(subsection) " ";
    		}

\*/

/\* EFECTOS

    Visibilidad
    	Anular el valor de visualización predeterminado
    		https://www.w3schools.com/css/css_display_visibility.asp
    		https://www.w3schools.com/cssref/pr_class_display.asp
    		https://developer.mozilla.org/es/docs/Web/CSS/display
    		Opciones:
    		inline, block, contents, flex, grid, inline-block, inline-flex, inline-grid, inline-table, list-item, run-in, table, table-caption, table-column-group, table-header-group, table-footer-group, table-row-group, table-cell, table-column, table-row, none, initial, inherit

    			display: inline;

    	No mostrar
    			display: none;

    	Ocultar
    		Para ocultar un elemento. Este seguirá ocupando el mismo espacio que antes. El elemento estará oculto, pero aún afectará el diseño.

    			visibility: hidden;

    		Diferencias entre no mostrar y ocultar
    		https://www.w3schools.com/css/tryit.asp?filename=trycss_display

    	Opacidad
    		La propiedad opacity puede tomar un valor de 0,0 a 1,0.
    		Cuanto menor sea el valor, más transparente.

    		img {
    			  opacity: 0.5;
    		}

    	Transparencias
    		Para establecer la transparencia por color se hace usando el atributo alfa de la definición de color en RGBA.
    		Un valor de color RGBA se especifica con: rgba (rojo, verde, azul, alfa ).
    		El parámetro alfa es un número entre 0.0 (completamente transparente) y 1.0 (completamente opaco).


    Cambiar el tamaño
    	Cambia el tamaño de un elemento.
    		resize: horizontal
    		resize: vertical
    		resize: both
    		resize: none
    	Ejemplo:
    		resize: horizontal;


    Cambiar el cursor

    	por defecto
    		cursor:default
    	automático
    		cursor:auto

    	Cruz
    		cursor:crosshair
    	Cambiar tamaño
    		cursor:e-resize
    	Ayuda
    		cursor:help
    	Mover
    		cursor:move
    	n-resize
    		cursor:n-resize
    	ne-resize
    		cursor:ne-resize
    	nw-resize
    		cursor:nw-resize
    	Mano
    		cursor:pointer
    	progress
    		cursor:progress
    	s-resize
    		cursor:s-resize
    	se-resize
    		cursor:se-resize
    	sw-resize
    		cursor:sw-resize
    	text
    		cursor:text
    	w-resize
    		cursor:w-resize
    	Esperar
    		cursor:wait


    Transformaciones

    	Transformaciones 2D

    		transform: propiedad

    		Propiedades CSS que se pueden utilizar con los métodos de transformación 2D:

    			rotate()
    				Rota un elemento en sentido horario o antihorario según un grado dado.
    				Sintaxi
    					rotate(angle)
    				Ejemplo
    					transform: rotate(-20deg);
    					Rota el elemento en sentido antihorario con 20 grados.

    			scale()
    				Aumenta o disminuye el tamaño de un elemento (según los parámetros dados para el ancho y el alto).
    				Sintaxi
    					scale(x,y)
    					scaleX(n)
    					scaleY(n)
    				Ejemplo
    					transform: scale(2, 3);
    					Aumenta el elemento para que tenga dos veces su ancho original y tres veces su altura original.

    			scaleX()
    				Aumenta o disminuye el ancho de un elemento.
    				Sintaxi
    					matrix(n,n,n,n,n,n)
    				Ejemplo
    					transform: scaleX(2);
    					Aumenta el elemento a dos veces su ancho original.

    			scaleY()
    				Aumenta o disminuye la altura de un elemento.
    				Sintaxi
    					matrix(n,n,n,n,n,n)
    				Ejemplo
    					transform: scaleY(3);
    					Aumenta el elemento a tres veces su altura original.

    			skew()
    				Sesga un elemento a lo largo de los ejes X e Y en los ángulos dados.
    				Sintaxi
    					skew(x-angle,y-angle)
    				Ejemplo
    					transform: skew(20deg, 10deg);
    					Sesga el elemento 20 grados a lo largo del eje X y 10 grados a lo largo del eje Y.

    			skewX()
    				Sesga un elemento a lo largo del eje X en el ángulo dado.
    				Sintaxi
    					skewX(angle)
    				Ejemplo
    					transform: skewX(20deg);
    					Sesga el elemento 20 grados a lo largo del eje X.

    			skewY()
    				Sesga un elemento a lo largo del eje Y en el ángulo dado.
    				Sintaxi
    					mskewY(angle)
    				Ejemplo
    					transform: skewY(20deg);
    					Sesga el elemento 20 grados a lo largo del eje Y.

    			translate()
    				Mueve un elemento desde su posición actual (de acuerdo con los parámetros dados para el eje X y el eje Y).
    				Sintaxi
    					translate(x,y)
    					translateX(n)
    					translateY(n)
    				Ejemplo
    					transform: translate(50px, 100px);
    					Mueve el elemento 50 píxeles a la derecha y 100 píxeles hacia abajo desde su posición actual.


    			matrix()
    				Combina todos los métodos de transformación 2D en uno.
    				Toma seis parámetros, que contienen funciones matemáticas, lo que le permite
    					rotar,
    					escalar,
    					mover (traducir)
    					y sesgar elementos.
    				Los parámetros son los siguientes:
    					matrix (scaleX (), skewY (), skewX (), scaleY (), translateX (), translateY ())
    				Sintaxi
    					matrix(n,n,n,n,n,n)
    				Ejemplo
    					transform: matrix(1, -0.3, 0, 1, 0, 0);

    		Más información
    			https://www.w3schools.com/css/css3_2dtransforms.asp


    	Transformaciones 3D

    		transform: propiedad

    		Propiedades CSS que se pueden utilizar con los métodos de transformación 2D:

    			rotateX()
    				Rota un elemento alrededor de su eje X en un grado dado.
    				Ejemplo
    					transform: rotateX(150deg);

    			rotateY()
    				Rota un elemento alrededor de su eje Y en un grado dado.
    				Ejemplo
    					transform: rotateY(130deg);

    			rotateZ()
    				Rota un elemento alrededor de su eje Z en un grado dado.
    				Ejemplo
    					transform: rotateZ(90deg);


    Transiciones

    	Para crear un efecto de transición, debe especificar dos cosas:

    		· la propiedad CSS a la que desea agregar un efecto
    		· la duración del efecto

    	Nota: Si no se especifica la parte de duración, la transición no tendrá efecto, porque el valor predeterminado es 0.

    	Propiedades CSS que se pueden utilizar con los métodos de transformación 32D:

    		transition()
    			Es una propiedad abreviada de
    				transition-property,
    				transition-duration,
    				transition-timing-function
    				y transition-delay.
    			Ejemplo
    				transition: margin-left 4s ease-in-out 1s;
    			Más información
    				https://developer.mozilla.org/es/docs/Web/CSS/transition


    		transition-delay()
    			Especifica un retraso (en segundos) para el efecto de transición.
    			Ejemplo
    				transition-delay: 1s;
    			Más información
    				https://developer.mozilla.org/es/docs/Web/CSS/transition-delay


    		transition-duration()
    			Especifica la duración (en segundos) para el efecto de transición.
    			Ejemplo
    				transition-duration: 2s;
    			Más información
    				https://developer.mozilla.org/es/docs/Web/CSS/transition-duration


    		transition-property()
    			Define los nombres de las propiedades CSS en las que el efecto de la transición debe aplicarse.
    			Ejemplo
    				transition-property: none;
    				transition-property: all;
    				transition-property: test_05;
    				transition-property: -specific;
    				transition-property: sliding-vertically;
    			Más información
    				https://developer.mozilla.org/es/docs/Web/CSS/transition-property


    		transition-timing-function()
    			Especifica la curva de velocidad del efecto de transición.
    			La propiedad de función de tiempo de transición puede tener los siguientes valores:
    				ease
    					especifica un efecto de transición con un inicio lento, luego rápido, luego termina lentamente (esto es predeterminado)

    				linear
    					especifica un efecto de transición con la misma velocidad de principio a fin

    				ease-in
    					especifica un efecto de transición con un inicio lento

    				ease-out
    					especifica un efecto de transición con un final lento

    				ease-in-out
    					especifica un efecto de transición con un inicio y un final lentos

    				cubic-bezier(n,n,n,n)
    					le permite definir sus propios valores en una función cubic-bezier

    			Ejemplo
    				#div1 {transition-timing-function: linear;}
    				#div2 {transition-timing-function: ease;}
    				#div3 {transition-timing-function: ease-in;}
    				#div4 {transition-timing-function: ease-out;}
    				#div5 {transition-timing-function: ease-in-out;};
    			Más información
    				https://developer.mozilla.org/es/docs/Web/CSS/transition-timing-function


    	Cambiar varios valores de propiedad

    		transition: width 2s, height 4s;


    Transición + Transformación

    	Efecto de transición a la transformación
    	Ejemplo
    		 transition: width 2s, height 2s, transform 2s;



    Animaciones
    	Permite la animación de elementos HTML sin utilizar JavaScript o Flash.
    	Las propiedades:
    		@keyframes
    			Especifica el código de animación.

    		animation
    			Una propiedad abreviada para configurar todas las propiedades de la animación.

    		animation-direction
    			 Especifica si una animación debe reproducirse hacia adelante, hacia atrás o en ciclos alternos.

    		animation-delay
    			Especifica un retraso para el inicio de una animación.

    		animation-duration
    			Especifica cuánto tiempo debe tardar una animación en completar un ciclo.

    		animation-fill-mode
    			Especifica un estilo para el elemento cuando la animación no se está reproduciendo (antes de que comience, después de que termine o ambos).

    		animation-iteration-count
    			Especifica el número de veces que se debe reproducir una animación.

    		animation-name
    			Especifica el nombre de la animación @keyframes.

    		animation-play-state
    			Especifica si la animación se está ejecutando o en pausa.

    		animation-timing-function
    			Especifica la curva de velocidad de la animación.

    	Ejemplo
    		{
    			width: 100px;
    			height: 100px;
    			background: red;
    			position: relative;
    			animation-name: example;
    			animation-duration: 3s;
    			animation-delay: 2s;
    			animation-fill-mode: both;
    		}
    	Ejemplo telegráfico
    		animation: example 5s linear 2s infinite alternate;

\*/

/\* CONDICIONALES
Ejecución condicionada al medio
Se puede establecer la ejecución de reglas CSS en función del medio desde el que se ejecuta el CSS. Es lo que se llaman "CSS queries"
Los queries son insensibles a las mayúsculas o minúsculas.
Las opciones de interfície (medio) son:
all Para todos los dispositivos de tipo multimedia.
print Para impresoras.
screen Para pantallas de computadora, tabletas, teléfonos inteligentes, etc.
speech Para lectores de pantalla que "leen" la página en voz alta.
Nota: Media queries que contengan tipos de medios desconocidos siempre retornaran falso.
Ejemplo de sintaxi
@media screen
{
#leftsidebar {width: 200px; float: left;}
#main {margin-left: 216px;}
}
Operadores lógicos
and Usado para colocar juntas múltiples funciones multimedia.
, Las listas separadas por comas se comportan como el operador "or".
not Negará un query si es posible pero no a todos los query posibles si están ubicados en una lista separada por comas.
El operador not no puede ser usado para negar un query individual, solo para un query completo
only Viene que navegadores antiguos que no soportan queries con funciones apliquen los estilos asignados.
Se puede enriquecer las condiciones con:
aspect-ratio
Razón de aspecto de los pixeles horizontales (primer termino) a los pixeles verticales (segundo termino).
Ejemplo:
@media screen and (min-aspect-ratio: 1/1) { }
color
Tiene en cuenta si el dispositivo soporta colores.
Ejemplo:
@media all and (color) { }
color-index
Indica el numero de entradas en la tabla de colores para el dispositivo de salida.
Ejemplo:
@media all and (color-index) { }
device-aspect-ratio
Describe la proporción de aspecto del dispositivo de salida.
Proporción de aspecto de los pixeles horizontales (primer termino) a los pixeles verticales (segundo termino).
Ejemplo:
@media screen and (device-aspect-ratio: 16/9), screen and (device-aspect-ratio: 16/10) { }
device-height
Describe la altura del dispositivo de salida (ya sea la totalidad de la pantalla o página y no el área del documento a renderizar).
device-width
Describe la anchura del dispositivo de salida (ya sea la totalidad de la pantalla o página y no el área del documento a renderizar).
Ejemplo:
<link rel="stylesheet" media="screen and (max-device-width: 799px)" />
grid
Determina cuando el dispositivo de salida es un dispositivo de cuadrícula o de mapa de bits. Si el dispositivo esta basado en una cuadrícula (como una terminal TTY o una pantalla de teléfono de solo texto), el valor sera 1, de lo contrario sera 0.
Ejemplo:
@media handheld and (grid) and (max-width: 15em) { ... }
Aplica una hoja de estilo a un dispositivo portátil con una pantalla de 15 caracteres o mas estrecha.
height
La función height describe la altura de la superficie a renderizar en el dispositivo de salida (como la altura de una ventana o la bandeja de papel en una impresora).
Ejemplo:
monochrome
Indica el número de bits por pixel en un dispositivo monocromático (escala de grises).
Si el dispositivo no es monocromático el valor sera 0.
Ejemplo:
@media all and (monochrome) { }
Aplica una hoja de estilo a todos los dispositivos monocromáticos.
orientation
Indica cuando el dispositivo esta en modo landscape (el ancho de la pantalla es mayor al alto) o modo portrait (el alto de la pantalla es mayor al ancho).
Ejemplo:
@media all and (orientation: portrait) { }
resolution
Indica la resolución (densidad de pixeles) del dispositivo de salida. La resolución puede ser especificada en puntos por pulgada (dpi) o en puntos por centímetros (dpcm).
Ejemplo:
@media print and (min-resolution: 300dpi) { }
Aplica una hoja de estilo a dispositivos con al menos 300 dpi de resolución.
scan
Describe el proceso de exploración de televisión de los dispositivos de salida.
Ejemplo:
@media tv and (scan: progressive) { }
Aplica una hoja de estilo solo a televisores de exploración progresiva
width
Describe el ancho de la superficie a renderizar en el dispositivo de salida (como el ancho de una ventana de un documento o el ancho de la bandeja de papel en una impresora).
Ejemplo:
@media screen and (min-width: 500px) and (max-width: 800px)
Hoja de estilo para ser utilizada cuando la ventana tiene un ancho entre 500 y 800 pixeles:
(Mozilla amplia esta gama con más opciones. Mirar su documentación para conocerlas.)

    	Mas información y ejemplos
    		https://developer.mozilla.org/es/docs/CSS/Media_queries
    		https://www.w3schools.com/css/css3_mediaqueries_ex.asp

\*/

/_
HACIENDO PRUEBAS CON REGLAS CSS
_/

/_ Pseudoelemento _/
::first-letter
{
font-size:50px;
}

div{
width:300px;
height:300px;
}

/_ Pseudoclase dinamica _/
div:hover
{
background-color:red;
width:500px;
}
