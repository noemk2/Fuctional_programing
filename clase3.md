# Do one thing well

las citas anteriores enfatizan la importancia del enfoque
tambien vio una explicacion rapida de como ese tipo de enfoque se
aplica a la programacion funcional
es el momento de ir mas all de lo superficial y ver el principio con mayor

profundidad a medida que comeienzan a aprender sobre el papel especial que

# the unix philosophy

hay algunas similitudes entre la programacion funcional y como funiona unix
Eso podria no ser demasiado sorprendente
ya
que a menudo unix puede ser tan intimidante como la FP
sin embargo
hay un par de principios clave de la filosofia que lo ayudaran a comprender mejor la

FP
en 1978 Doug McElroy documento los 4 aspectos principales de la filosofia Unix
esos cuatro principios hacen qeu cada programa haga una cosa bien
"mae each program do one thing well"
2do luga espere que la salida de cada programa se convierta en la entrada de otro programa
aun desconocido en 'Expect the output of every program to become the input of another '
3er que el sofware de diseno se pruebe antes y "desing sofware to be tried early"
4to use herrramientas sobre mano de obra no calificada para aligerar la carga
'use tools over unskilled labor '
es decir
escribir un script en lugar de usar un metodo de fuerza bruta para transformar los datos
en un archivo

Una vez mas McEroy estaba hablando especificamente sobre como escribir programas para unix
pero al menos los 2 primeros y probablemente incluso los 3 primeros se aplican tambien a la
programacion funcional

La aplicacion de estos principios de la programacion funcional podria ser algo como esto

FP filosofia
1er 'Make each function do one thing well' haga que cada funcion haga una cosa y solo una cosa bien
2do 'Expect the output every function to become the input of another' espere qeu la salida de cada funcion se
convierta en la entrada de otra funcion desconocida
3er 'Design functions to be tested early' funcinoes de diseno para ser probadas temprano

el reto de este modulo cubrira como estos 3 principios se aplican a la FP

Mira FP de esta manera le ayudara a comprender algunos de los fundamentos del paradigma sin enredarse en
la sintaxis especifica de cualquier idioma

# Focus on One thing

EL 1er principio para mirar a los estados es que debes hacer que cada funcion haga una cosa y solo una cosa bie
si estas pensando bien eso parece
una buena codificacion en general no te equibocas
Mantener el codigo enfocado es una buena practica y ayudara a eleminar los errores pero es posible que se sorprenda
al descubrir que muchas veces las funciones que parece nhacer algo en realidad estan haciendo varias cosas

El siguiente ejemplo va analixar una archivo de texto y encontrar los cursos que
tenemos una lista de cursos con el nombre del curso y sus repectivos profesores
si tu pasaras una funcion con el parametro de Nate taylor te devolveria 2 curos echos por el
ejm

```java
public string[] FindCoursesForAuthor(string author)
{
	var courseFile = File.read(FileName)
	var courses = courseFile.split(\n)
	var authorCourses = []
for(var i=0; i< courses.length; i++) {
	if(courses[i].Contains(author))
		{
			authorCourses.push(courses[i].ToTitleCase())
		}
	}
return authorCourses
}
```

esta fn parece que esta haciendo una sola sosa
es contrar los cursos que le pasemos
pero a medidad que profundizas un poco mas esta haciendo un poco mas
A partir de la primera linea de la fn
var courseFile = File.read(FileName)
este abre un archivo y lee los contenidos
y
la siguiente linea tiene una funcion que divide ese texto en una matriz o array
para qeu puede iterar sobre la matriz de cursos
finalmente dentro del ciclo comienzan a buscar los cursos que solicito
aquellos que contienen el nombre del autor
pero
si te fijas un poco mas en la linea autorCursos ' authorCourses.push(courses[i].ToTitleCase())'
Empuje se puede ver que esta haciendo otra cosa mas antes de insertar contenido en la matriz
esta convirtiendo la cadena ToTitleCase

Todo esto en ultima instancia lograr lo que desea
Le propocina una lista de cadenas de titulos para los cursos creados
por un autor que usted especifico pero esta funcion esta haciendo mas de una cosa
de echo esta funcion esta haciendo al menos 4 cosas
primero esta  
1ero esta abiendo un archivo
2do esta dividiendo el contenido
3er luego esta filtrando los cursos
4to y finalmente es el titulo que lo castea a string

si esta aconstumbrado a escribir codigo de esta manera
es
probable que ni siquiera piense que los elementos numero 1 y 2 son tareas separadas
se qeu cuando empece a jugar con la PF eso es exactamente lo que pense
pense bien
por supuesto que abri el archivo y devidi los contenido
? de que otra manera se supone qeu debo filtrar los cursos?
tambien
podrian estar pensando como podria la manera mas enfocada
Asi es como la funcion que usted vio anteriormente puede ser refactorizada
para hacer una cosa y solo una cosa bien?
bueno al igual que el codigo OOP
un bloque de codigo en la pantalla tambien es un psudo codigo

a functional example

```java
def findAuthorCourses author, courses
	filter(x=> x.contains(author), courses)
end
```

intente usar una sintaxis diferente para que sea mas evidente en este curso cuando jugamos con OOP
en lugar de FP
la funcion findAuthorCourses solo esta haciendo solo una sola cosa
esta tomando una lista de cursos y los esta pasando una funcion de fultro
esa funcion de filtro esta llamado a una funcion anonima separada 'def findAuthorCourses author, courses'
En este caso x contiene autor
muchas veces esta funcion se llamara prueba y se devolvera todo lo que pase la prueba
cualquier cosa no pase la prueba no sera
Despues de ver esta funcion podrias estar diciendo
'estas haciendo trampa'
despues de todo
el funcional findAuthorCourses ni siquiera devuelve el mismo resultado que FindCoursesForAuthor
Es una funcion completamente diferente no un refactor
y
si tubieras pruebas de unidad para la funcion probablemente todas fallarian en la segunda funcion
si bien podria pensar que esto es solo un ejemplo ideado para demos trar un punto durante una demostracion
puedo
garantizarle que no lo es

Do one thing well

si la funcion solo hace una cosa pero ese es el punto
aemas hacer una cosa bien es solo el primer de nuestros
principios para la programcion funcional
a medida que esta modulo continua vera
como esta funcion encaja en el esquema mas amplio de las cosas y finalmente lograra
lo mismos resultados que la version OOP

# Type signatures

antes de agregar otras funcionalidades como abrir el archivo o la caratula del titulo permitame tomar un breve desvio
para hablar sobre la firmas de tipo

Cimence mirando el codigo funcional del ultimo

```java
def findAuthorCourses author, courses
	filter(x=> x.contains(author), courses)
end
```

mira las entradas aqui
? de que tipo son ?
es algo dificil de decir porqeu he hecho que este codigo es psudo-funcional
sea dinamico pero a partir del contexto
se puede decir que es probable que los cursos (valores de entrada) sean una matriz de cadenas
o
al menos es una matriz de un tipo de contiene funcion
el autor es probablemten o al menos es un tipo de lo que este en la matriz que se pasa
ademas de los nombres de las variables
aqui no hay nada que sea especifico de los cursos o autores
Esa es la mismoa funcion que funcionaria para cada conbinacion de cadena y matriz de cadena que pasaste
si este codigo se escribiera en C#
puede hacer que tanto el autor como los cursos sean genericos utlizando el
IEnumerable de T
Esto le dice al compilador NET que la lista de curosos y la de resultados estan
compuestos de elementos del mismo tipo T
y
codigo:

```c#
public IEnumerable <T> FindCoursesForAuthor <T> (T author, IEnumerable <T> courses)
```

ese tipo tambien es el mismo que el
autor individual
Ademas el tipo T aqui es un marcador de posicion lo que significa que a C# no le importa que tipo es
siempre que los cuatro tipos sean iguales

en programacion funcional a menudo veras fimas de tipo en lugar de firmas de metodo

Type Signature

```c#

findAuthorCourses :: (String, [String]) -> [String]
```

para la funcion findAuthorCourses es posible que vea una firma de tipo como la que parace en la pantalla

```c#

findAuthorCourses :: (String, [String]) -> [String]
def findAuthorCourses autor, courses
	filter(x=> x.contains(author), courses)
end
```

Esto aprecera a menudo en los documentos asi como inmediatamente encima de la definicion de la funcion
por ejmplo
podria tener una aspecto similar a este si estuviera leyendo una base de codigo para la FP
la firma se puede descomponer con bastante rapidez
Antes de los 2 puntos dobles es el nombre de la funcion en este caso
findAuthorCourses Los parentesis representan los parametros de entrada
en
este caso es una cadena y una matriz de cadenas
la flecha delgada indica lo que se devolvera en este caso una serie de cadenas
si
tubierra una funcion similar
pero
ligeramente diferente
como la que ve en la pantalla su firma de tipo tambien
podria modificarse
Aqui en lugar de cursos
la lista es una lista de autores

```c#
def findAuthorCourses autor, courses
	filter(x=> x.contains(author), courses)
end
```

su tipo de fima podria tener este aspecto
Note que ha sido generico para usar una cadena en lugar de una programacion funcional simplemente
representa algun tipo esta firma le indica que si pasa algun tipo y una matriz del mismo tipo
devolvera una matriz del mismo tipo ahi es donde verias t en c#

es probable que veas una 'a' en programacion funcional

(a, [b]) -> [a]
en constraste si viera la firma
de tipo que esta ahora en la pantalla sabria que la siguiente funcion toma entrada de algun tipo
y una matriz de otro tipo
y devuelve una matriz que tiene el mismo tipo que el 1er parametro pasaste dentro ls firmas de
tipo como esta ayudan a resaltar que tan generica es una funcion

similar a las plantillas en otros lenguajes

Ask 'Can I genericeze this?'
para nuestra funcion de encontrar cursos por el nombre del autor ya no tiene mucho sentido
generico pero siempre es algo para deternerse y pensar mientras escribe codigo

A menudo me pregunto si esto solo funionara en el tipo de datos que estoy usando en este
momento o funcionara algun otro tipo?
y cuando te enfocas en hacer solo una cosa bien
se vuelve mas facil pensar en una funcion que funcione de manera generica

Por que era importante?
bueno hay algunas razones
1ero a medida que continue su viaje y lea documentos para bibliotecas e idiomas en
el ambito funcional
vera cada vez mas firmas tipograficas (Prevalent in documentation)
2do lugar nuevamente destaca la filosofia de Alan perlis que muchas personas escriben
codigos funcionales tenderan a hacer que sus fn sean genericas
claro que puedese hacer eso en otros paradigmas
pero ser mas frecuente en la programacion funcional

Estas firmas de tipo son un recordatoriio y a veces incluso un estimulo
Ahora desea tener esas 100 funciones en una sola estructura de datos en lugar de 10 fn en 10
estructuras de datos diferentes(100 fn on 1 data estructure)
y
3ro finalmente se simplificara el segundo principio (simply second principle)
el siguiente clip se sumergira en el 2do principio de FP con mayor profundidad
y al final de este clip vera como las firmas de tipos pueden ayudarlo a redactar su

# From output to imput

el 2do punto de la filosofia de unix que se esta aplicando aqui a la FP es que debe esperar que la salida de cualquier
o funcion se convierta en la entrada de otro programa o funcion aun por escrivir la aplicacion de firmas de tipo

- Type signatures show how functions can be chained

Al examinar las firmas de tipo puede comenzar a ver como las diferentes funciones se relacionaran entre si
por ejem

la firma de tipo en la pantalla
FuncA :: [a] -> [b]

es para una funcion que puede tomar una lista de una estrutura de datos y devuelve una lista con una estructura de
datos diferente

FuncB :: [a] -> b

la nueva firma de tipo qeu esta en la pantalla para funcB muestra que es una funcion que toma una lista de estructura
de datos y devuelve una instancia unica de datos

Al observar las 2 firmas puede ver que la salida de funcA se puede pasar facilmente como los datos a funcB
[b] (de funcA) se cambia por [a] (de funcB)
No se obsesione con el hecho de que funcA devuelve una lista de B
en este caso B no es un tipo de datos especifico sino que indica que funcA esta transformando
los datos de un tipo a otro
es decir puede considerarse simplemente como el primer tipo de dato y puede considerarse
como el segundo tipo de datos
pero en este caso el segunto tipo de datos puede convertirse en el primer tipo de dato

otro ejm

```js
var tempResult = funcA([{name: 'Nate Taylor, location: 'Omaha'}])

var finalResult = funcB(tempResult)
```

```js
var finalResult = funcB(funcA({name: 'Nate Taylor', location 'Omaha'}))
```

eliminar la variable temporal y lograria el mismo resultado
sin embargo lo bueno de las variables temporales es que puede ayudar a mejorar la legibilidad del codigo
Esta opcion que esta en la pantalla ahora
para mi de todos modos es difil de leer porque hay varios parentesis corchetes y llaves
y todo esta en una linea

## pipe operator

la FP se enfoca en permitir que los resultados de una funcion fluyan a otra funcion a medida que se ingresa
varios de ellos han desarrollado un operador llamado tuberia (pipe)

para el proposito del codigo pseudo-funcional
usaremos el operador de tuberia que se encuentra en el lado izquierdo de la pantalla
No por casualidad este es el mismo operador que se usa en mas de un idioma

Este operador le dice al idioma que tome la salida de una funcion y la use como entrada a otra

Por lo tanto encadenar o canalizar esas mismas llamadas de funcion se veria como el codigo que se en pantalla
ejm

```js
funcA([{ name: "Nate Taylor", location: "Omaha" }]) |> funcB;
```

note que no se pasa un parametro a funcB se debe a que el operador de la tuberia lo hara automaticamente es hora
de aplicar este principio de nuevo a la fn que se discutio en el clip
de enfoque en una cosa

Si recuerdas dejamos ese clip con la funcion que ves en la pantalla ahora

En ese momento comente que si bien podrias pensar que estaba haciendo trampa
al simplificar esta funcion tan dramaticamente que al final verias como se unio
bueno
el momento de ver que se unio

```java
def findAuthorCourses author, courses
	filter(x => x.contains(author), courses)
end
```

## function chain

loadFile('courses')
|> splitOnNewLine()
|> findAuthorCourses(author)
|> titleCase()

Bueno
el momento de ver que es ahora
Al utilizar el operador de tuberia en nuestro pseudo codigo podria escribir codigo que devolveria el mismo resultado
que el codigo original orientado a objetos

Al recorrer este codigo
puede ver que la primera linea lee un archivo de texto en una sola cadena
ejm loadFile('courses')

el resultado de esta se le pasa a
|> splitOnNewLine() que igual solo hace una accion
y se le pasa al otro
|> findAuthorCourses(author) junto con el nombre del autor esta funcion devuelve una lista de cadenas
recuerde que el idioma esta canalizando los datos en esta funcion para nosotros
|> findAuthorCourses(author) (tachado)
|> findAuthorCourses(author, courses)

por lo que la sintaxis de la tuberia es la misma que el codigo que ve en la pantalla
es decir
la tuberia proporciona los cursos para nosotros

titleCase()
la utltima funcion toma una lista de cadenas y devuelve una lista de la misma longitud pero esta vez esas
cadenas se encajonan en el titulo  
en este putno tiene cuatro funciones individuales
cada una de las culaes solo hace una cosa
Estas cuatro fn se encadenan para producir el mismo resultado que el enfoque orientado a objetos anterior

Es decir al tener funciones que hacen una cosa bien y que devuelven datos que esperan que sean entradas para otra fn
han descompuesto un problema mas dificil en pequenos pasos sucintos
Hay un beneficio mas para estas cuatro fn
esto se debe a que solo se enfocan en hacer una cosa bien
'Focused functions lead to higher resue'

pueden ser utlizadas por otras fn
es probable que puedan imaginar muchos escenarios en los que se podria usar la fn SplitOnNewLine
o
incluso la fn titleCase
si solo hubieran sido envueltos en una funcion mas grande de findCoursesByAuthor
entonces
cada vez que quisiera dividirte en una nueva linea tendrias que escribir ese codigo nuevamente

Al seguir los 2 primeros principios de la FP
ahora tiene fn de utilidad bien definidas que se pueden usar en otros lugares

# Test early

el tercer principio de la filosofia de unix que aplica a FP es realizar una prueba temprana

## Always test early

para ser justos en mi opinion las pruebas iniciales se aplican a todo el software
independiente del idioma o el paradigma en el que esta escrito
Cuando realiza la pruba a tiempo esta mejor preparado para detectar errores en los casos perdidos
antes de que sea demaciado tarde puede ser bastante frustrante una cantidad significativa de tiempo trabajando en una
pieza de software para darse cuenta solo dias o incluso semanas despues de que no esta del todo bien
pero aun si se da cuenta de que los cambios que necesita hacer ahora son mas dificiles debido a cuanto tiempo espero para
realizar la prueba

Es importante averiguar que significa la prueba temprana
En la filosofia de Unix el autor original pretendia qeu el software se probara en cuestrion de semanas y luego desechara las
partes torpes o partes qeu no funcionaban

Pero
Cre que es demasiado tiempo
especificamente
si estas trabajando en un equipo
piense en cuanto codigo se puede generar en una sola semana
Esperar hasta que termine esa semana para probar el codigo podria producir una cantidad abrumadora de trabajo
Recomiendo hacer pruebas en unos minutos
La forma mas facil de probar su fn en minutos
no semanas
es tener buenas pruebas de unidad (unit test) (write unit test)

Las pruebas unitarias no son exclusivas de la programacion funcional
de hecho
espero que los estes escribiendo en el idioma que estes usando actualmente

Si bien las pruebas unitarias no son exclusivas de FP
ofrecen algunas ventajas cuando se trata de pruebas. En 1er lugar la configuracion es mucho mas facil

## FP Advantages

### Easier set up

Muchas veces, cuando esta probando el codigo puede ser dificil determinar todos los diferentes simulacros y falsificaciones
que son necesarios para que su prueba funcione
A menudo puede requerir establecer varias propiedades en un objeto
o en una serie de objetos solo para poder tener los datos correctos para probar

Sin estos se reduce en gran medida porque los unicos datos con los que operara una funcion seran los datos que usted
transmita
como resultado a menudo hay menos necesidad de simular o falsificar las llamadas a funciones y normalmente
puede pasar los datos exactos mas facilmente a una sola funcion

### Easier verification

En segundo lugar la verificacion es mas facil
Al igual que con la configuracion a menudo puede ser dificil determinar si su codigo
hizo lo que pensaba que iba a hacer
A menudo puede requerir verificar que alguna otra funcion haya sido llamada con los datos correctos o incluso que haya sido
llamada en absoluto sin embargo con la FP cada funcion devuelve un valor...
Como resultado de probar si una fn hizo lo correcto
simplemente necesitaba verificar su valor de retorno
y dado que la programacion funcional se enfoca en que cada funcion haga una cosa bien
deberia poder determinar que se supone que debe ser la salido sin mucha molestia

## Testing functional programing is straight forward

Imaginese
probando la funcion splitOnNewLine del ultimo clip

sabe que tendria que pasar una cadena con una nueva linea y que deberia obtener una lista con 2 elementos
como resultado
y si bien esto puede parecer una caso trivial
recuerde que la funcion es la incorporacion de los principios de FP

La salida solo depende de la entrada y la fn se enfoca en hacer una cosa bien concedido que no todas las fn que escriba seran
tan sencilas
pero si mantiene esos principios en su lugar  
probar el codigo desde una base de codigo funcional deberia ser bastante sencillo

## Complexity through Simplicity

Este modulo podria resumirse diciendo que la programacion funcional resuelve problemas complejos
a traves de metodos simples

### Descompose problems

La programacion funcional intenta descomponer los problemas mas dificiles en problemas mas simples y luego descomponer esos
problemas simple en problemas aun mas simples
hasta que todo lo que queda es una serie de funciones que cada una hace una cosa particularmente bien
despues de indentificar esos simples

### Reuse building blocks

La FP lo alienta a usar esos bloques de construccion para reslver su problema mas complejo
esto se logra al encadenar esas funciones de proposito unico

La composicion de fn de esta manera le permite crear funcuines mas complejas

### Test early

y como esas funciones son bastantes sencillas se pueden probar mas facilmente
Esto significa que puede tener un mayor grado de certeza de que funcionaran en los diversos datos que usted transmita
Y
asi es como Alan Perlis
puede lograr sus 100 funciones en una estructura de datos
al crear muchas fn pequenas que se aplican a cualquier lista o cualquier mapa
comienza a eliminar la necesidad de definir estructuras de datos personalizadas

"Learning functional programing involves a shift in perspective"
Al final del dia hacer programacion funcional no es tanto aprender una nueva sintaxis
sino
cambiarla como se ven los problemas
y una forma de cambiar la forma en que ve los problemas es como utiliza los datos
