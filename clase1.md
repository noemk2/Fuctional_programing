# Defining functional programing

para poder entender que es programacion funcional sera bueno comenzar con una definicion
esto asegurar que haya un vocabulario comun para el resto del curso

segun wikipedia
es un paradigma de programacion que trata la computacion como la evaluacion de funciones
matematicas y evita el cambio de datos y datos mutables

Esto require un poco de desempaque pero hacerlo ayudara a facilitar el resto del curso

La primera
la programacion functional es un paradigma
en pocas palabras la programacion functional es una forma o estilo de resolver problemas
no se limita a un lenguaje espesifico
ademas
cada vez mas idiomas se estan convirtiendo en lenguajes multiparadigma

Por ejemplo tanto c# como java han incorporado conceptos de programacion de funciones
con las funciones LINQ y lambda respetivamente

Es probable que ya conzcas algunos otros paradigmas

un paradigma comun es POO
una gran cantidad de educacion de programacion formal comienza con ++ o java
Ambos son lenguajes orientados a objetos
Como tales se centran en conceptos como clases herencia y encapsulacion
Si bien
C++ y java son lenguajes orientados objetos la forma en que a menudo se ensenan comienza con
un paradigma diferente
el del procedimiento

ademas
si alguna ves has escrito declaraciones SQL en una base de datos relacionales
ha aprovechado un paradigma declarativo

el lenguaje sql puedesp programar sin preocuparte por el flujo de control

El punto aqui es que existe muchos paradigmas
que lo hace diferente a otros paradigmas

la definicion incluye 2 componentes clave de otros paradigmas
el 1ero se trata de la computacion como la evaluacion de funciones matematicas
esa declarativo hace que parezca que la programacion funcional no es para todos...
tambien
es una razon comun para la que las personas preguntan si pueden usar la aplicacion
empresarial
pero
en este caso en el  la precion necesaria para la definicion causa cierta perocupacion

la palabra clave es funciones matematicas

Una funcion en matematicas es algo en que la salida se asigna uno a uno a la entrada

Por ejmplo la ecuacion y=mx + b
lineal de la recta donde m es la pendiente y b es el desplazamiento

Una vez que se establecen un solo valor de x solo producira un solo valor de y
y
y produce un grafico como el que se ve en la pantalla

en esta grafica la funcion matematica es simple y=x
Es decir cada valor y esta determinado por el valor de x pasado
Como puede ver aqui con el punto que cuando pasa 1 por x produce un valor y
pero
como se relaciona eso con este paradigma
De la misma manera que una funcion matematica asigna los resultados uno a uno con una entrada

en la programacion functional las functiones indivicuales siempre devolveran
el mismo resultado si se tienen las mismas entradas

Funciones como estas se llaman funciones puras

podrias estar pensando que sus funciones orientadas a objetos tambien simpren devuelven el mismo resultado
cuando se les da la misma entrada pero eso no es del todo cierto

Por ejmplo
Que Math.random() se llama dos tiempos diferentes
en este codigo llama a la misma funcion 2 veces
pro
se obtiene 2 resultados diferentes

es cierto anque haya psado e los mismos argunmentos
y
en este caso no se ha pesado ningun argunmento
de echo esta es una forma de saber que una funcion no es pura
SI
no tiene argunmentos no puede ser pura

Otros paradigmas
que incluyen orientados a objetos tienen funciones puras
por ejemplo este codigo en C#
Math.sqrt(81) // 9
demuestra una funcion pura
sqrt(81) simpren devolvera 9 sin importar cuantas veces lo llames sin embargo
la diferencia aqui si bien puede hacer esto en otros paradigmas

debe hacer en programacion funcional
Estas funciones puras en realidad contribuyen al segundo elemento clave en el paradigma
y
es que evitan el estado cambiante
o
los datos mutables
Esto puede ser un poco complicado porque es imposible escribir un programa significactivo que no cambie los datos

Al pensar en el programa promedio se dara cuenta de que todo lo que esta haciendo es tomar algun tipo de entrada
hacer algun tipo de calculo y entregar la salida
pero
para hacer esto los datos deben poder cambiar
Un ejemplo aqui sera util

## shopping cart

shoppingCart.AddBook('You Are What You Love')
shoppingCart.GetTotal() //\$12.29

Al igual que con las functiones puras comience mirando un codigo de estilo orientado a objetos
aqui tienes a hoppingCart.AddBook shoppingCart.GetTotal
incluso si nunca has trabajado en un sitio de comersio electronico haciendo codigo

Esta tomando el libro 'You Are What You Love' y colocando en el carrito
despues de eso al obtener el total
se resume todos los elementos en ese carrito
Si
Tubiera que profundizar un poco mas en la funcion GetTotal
podria
verse algo como esto
no funaliti funcion

```java
public float GetTotal()[
return Items.sum(i=> i.price)
]
```

GetTotal devuelve un articulo
suma del precio
Aqui elementos es una matriz de los elementos que han agregado cada vez que llamaba a AddBook
colocaba un nuevo elemento en la lista de elementos
es decir la funcion la funcion
AddBook esta ectualizando el estado en la clase shopping Cart
Este es un enfoque
bastante comu en terrenos orientados a objetos
donde un metodo actulizara el estado y otro metodo realizara calculos en el nuevo estado

En funtional programing

```java
updatedCart = add(shoppingCart, 'You Are What You Love')
price = getTOtal(updatedCart)
```

la programacion funciona es una diferente approach to writing software

la programacion funcional y parte de como se diferencia de otros paradigmas
si aun no lo conseguide 100

beneficios

aprenderas modulos
So one thing well
reducir bugs with immutable data
why functional programing matters

# Contrasting with object oriented programing

A traves de los ejmplos que acaba de ver
ya ha visto algunas diferencias entre la prggramacion funcinal y
la programacion POO pero lamentablemente sera util dar un paso atras y observar algunas de las diferencias
fundamentales entre estos 2

Paradigmas
el artista marcial Brusce Lee dijo una vez que no temo al hombre que practico 10000 patadas sino al hombre que
alla practicado ona patada 10000 veces

el punto aqui es que si practicas un tipo de patada una vez no vas a ser muy compenente con el
y
serguro puedes conecer 10000 patadas
pero no conces ninguna de ellas
muy bien

en el otro extremo es posilbe que solo sepaas 1 patada
pero si has hecho esa patada 10000 veces existe una gran patada con la posibilidad de que sea bueno
si no
incluso genial con esa patada
quizas te preguntes que tiene que ver kicking con la programacion funcinal
bueno
el cientofico informatico y profesor Alan Perlis
tubo una observacion similar a la de Bruce Lee
senalo que es mejor tener 100 funciones operando en 1 estructura de datos que 10 funciones en 10 estructuras de datos

al giual que la cita de Bruce le
al final del dia hay 100 funciones ya sea en una sola estructura de datos o varias
mientras que la cantidad no cambia
la calidad silo hace
Y esta es una de las diferencias fundamentales

quizas te preguntes como se desarrolla estos en los lenguajes de programacion funcional
la PF tiene menos estructura de datos qu POO
para la PF hay 2 estructura de datos principales que se utilizan
la primera es una lista []
una lista es similar a una matriz
contiene multiples valores
estos podrian ser primitivos como enteros o cadenas
o
estructura de datos mas complejas
la otra estructura de datos
es un mapa {}
esta es una estructura de datos que tiene una coleccion de pares de valores clave
combinacion de listas y mapas le permitira lograr bastante en la programacion funcional

OPP vs FP
More data structures | Fewer data structures
Fewer functions per data structures | More funtions per data structure
10 functions on 10 data structures | 100 functions on 1 data structure

la oop enel cual la forma es crear nuevas clases para manejar nuevas funcionalidads
su clase constara de datos tales como campos y propiedades
asi como funciones que se ejecutan en los datos

Aqui es donde Dr la cita
la oop es el case en el que tendria 10 funciones en 10 estructuras de datos
pero la FP le daria 100 funciones en una sola estructura de datos

en la practica
este
parece ser el secreto para odoptar la FP  
otros aspectos
"la major diferencia es como la data es procesada"
como la funciones puras y la imutabilidad 
puede ocurrir en la OOP pero la diferencia en como se prosesan  los datos 

en los 2 paradigmas puede causar confusion y provocar acidez cuando alguien 
trata de pasar de la programacion OOP a la FP

Es entendible completamente que todo esto puede ser confuso y abrumador
