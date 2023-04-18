---
layout: post
title: El origen de los números aleatorios 
---

Los generadores de números aleatorios tienen múltiples aplicaciones en juegos de azar, muestreo estadístico, simulación por computadora, criptografía, entre otras áreas donde es deseable obtener resultados impredecibles. En este post realizamos un recorrido por la historia de los números aleatorios. 

## Orígenes de los números aleatorios

La historia de lás técnicas para generación de números aleatorios es larga e interesante. Comienza con métodos manuales como el lanzamiento de dados o la extracción de cartas de un mazo, pasa por las tablas impresas en libros, y llega hasta los algoritmos computacionales actuales.

Dados, monedas y mecanismos similares se han utilizado desde tiempos milenarios para realizar elecciones "aleatorias" y producir números aleatorios en juegos de azar. Algunos dados encontrados en excavaciones en Irán e Iraq datan de más de 5000 años (¡Sí! ¡5000 años!). Este tipo de artículos también fue popular en India, China y Egipto hace unos 4000 años (Puedes observar parte de esta historia en [este link](https://en.wikipedia.org/wiki/Dice) )

![ Pintura mural ]({{ site.baseurl }}/images/Wall_painting_-_scenes_around_the_pub_-_Pompeii_(VI_14_35-36)_-_Napoli_MAN_111482_-_04.jpeg "Pintura mural romana que muestra a dos jugadores de dados, Pompeya, siglo I")

En aquellos tiempos, algunas personas creían que los resultados del lanzamiento de dados no eran aleatorios, sino designios de los dioses. Por ejemplo, en tiempos del Imperio Romano, a veces la diferencia entre la vida y la muerte podría depender del resultado del lanzamiento de una moneda. Incluso hoy, el lanzamiento de monedas se utiliza en ocasiones para resolver disputas en compromisos deportivos.

## Tablas de números aleatorios

Para los profesionales en estadística, estos mecanismos resultan inconvenientes. Por eso L.H.C. Tippett publicó en 1927 "Random Sampling Numbers", donde introdujo la primera "tabla de números aleatorios", con 41600 dígitos aleatorios, tomando datos del censo británico de 1925. A partir de ese momento el método estándar para generar números aleatorios consistía en seleccionar una muestra de una tabla de números aleatorios.

Fisher y Yates en 1928, construyeron una tabla de números aleatorios con 15000 digitos a partir de dígitos de tablas logarítmicas. Introdujeron un elemento de aleatoriedad utilizando naipes para seleccionar las páginas y las columnas en las cuales buscar los números que introducirían en sus propias tablas.

En 1938, Kendall y Babington-Smith crearon una tabla con 100000 muestras de números aleatorios a partir de la primera "máquina" que producía números aleatorios. La máquina consistía en un disco dividido en 10 sectores marcados con los números del 0 al 9, que giraba 250 veces por minuto. Un haz de luz destellaba en un momento aleatorio, aproximadamente cada 2 segundos. Una persona registraba cuál era el número del sector que había destellado.

La pregunta que surge al utilizar este tipo de tablas es cómo medir la calidad de la tabla; es decir, ¿cómo se garantiza que una muestra obtenida a partir de la tabla en verdad sea aleatoria? Kendall y Babington-Smith respondieron introduciendo la noción "secuencia aleatoria localmente": cualquier selección dentro de la secuencia (suficientemente larga) debe parecer aleatoria y pasar algunas pruebas estadísticas. Entre las pruebas, propusieron algunas que median:
-la frecuencia de cada dígito
-la frecuencia de cada par de valores sucesivos
-la frecuencia de ciertos bloques de cinco dígitos
-la longitud entre la aparición sucesiva de un dígito

Estas frecuencias son comparadas con sus respectivos valores esperados a través de pruebas chi-cuadrado. 

En 1955 la RAND Corporation editó un libro con 50 filas de 50 dígitos por página, en un total de 400 páginas. El libro de máximo suspenso jamás escrito. Leyéndolo como una sucesión de dígitos, es imposible para el lector saber lo que vendrá después (disponible en [amazon](https://www.amazon.com/-/es/RAND-Corporation/dp/0833030477/ref=sr_1_1?__mk_es_US=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=Million+Random+Digits+With+100%2C+000+Normal+Deviates&qid=1600380410&sr=8-1) ).

![ Tabla de números aleatorios ]({{ site.baseurl }}/images/Table_of_random_digits.jpg "Tabla de números aleatorios")

## La era de los computadores

Para obtener muestras aleatorias computacionalmente, las tablas en los libros no son convenientes. En 1947, la RAND Corporation (la misma que después imprimiría el libro), desarrolló un proyecto para producir un millón de dígitos aleatorios de forma automatizada. Un dispositivo electrónico emitía pulsos aleatoriamente. Cada segundo se contaban el número de pulsos emitidos, se obtenía el residuo de dividir el número entre 32. Los primeros 20 resultados, de los posibles 32, eran mapeados a dígitos decimales, los otros eran descartados. 

Los dígitos fueron guardados en 20000 tarjetas perforadas, 50 dígitos por tarjeta. Como los dígitos impares eran ligeramente más frecuentes, se hizo una transformación adicional, añadiendo a cada número el número correspondiente de la carta anterior y obtiendo el módulo 10. Los dígitos transformados pasaron las pruebas estadísticas. Una copia del conjunto de las tarjetas perforadas (una gran caja) podía comprarse en 1950.

A partir de entonces han surgido dos grandes vertientes para la generación de números aleatorios:
1. Utilizar dispositivos físicos (a partir del ruido eléctrico o similares).
2. Programar algoritmos puramente determinísticos que 'imiten' la aleatoriedad.

Con los computadores, se pueden emplear dispositivos físicos contadores de eventos aleatorios a partir del ruido térmico y eléctrico, efecto fotoeléctrico, dispositivos basados en fenómenos de física cuántica, ruido del disparo en circuitos electrónicos, desintegración radiactiva detectada por un contador Geiger, etc. Miles de artículos y patentes de generadores de números aleatorios como estos han surgido en los últimos 70 años.

Uno de los primeros ejemplos que se pueden encontrar es el de Cobine y Curry (1947), quienes utilizan el ruido eléctrico en un tubo de gas en un campo magnético que se amplifica y se muestrea para producir bits aleatorios. Para 1957, el ERNIE (Electronic Random Number Indicator Equipment) podía producir 50 números aleatorios por segundo, y fue utilizado para determinar los números de la lotería británica. Funcionaba amplificando y recolectando el ruido eléctrico producido por la corriente dentro de tubos llenos de gas neón.

Por el lado algoritmico, las primeras aproximaciones consistían en utilizar decimales sucesivos de números irracionales como pi y e, para imitar una secuencia aleatoria. Metropolis et al. (1950) calcularon 2000 decimales para pi y e con este propósito y la secuencia pasó las pruebas estadísticas. En 1962, Patrhia consiguió 10000 decimales para pi y posteriormente, en 1965, Esmenjaud-Bonnardel alcanzó los 100000 decimales. 

El día de pi (Marzo 14 de 2019), Emma Haruka Iwao, utilizó Google Cloud para calcular el valor más preciso de pi conocido a la fecha. Usando 25 máquinas virtuales y 121 días calculó 31.4 billones de dígitos decimales, batiendo el récord anterior de 22.4 billones obtenido por Peter Trueb's en 2016, quien había usado una sola computadora, equipada con dos docenas de discos duros de 6 TB para manejar el enorme conjunto de datos y que tardó 105 días en calcularlo.

Utilizar estos dígitos, sin embargo, es muy lento, además que requiere de mucho espacio para almacenarlos. Por lo que resulta más interesante un algoritmo puramente determinístico que "imite" el comportamiento de aleatoriedad esperado. Un punto clave  de cualquiera de estos algoritmos es que puede reproducir la misma secuencia cada vez que se requiera, sin tener que almacenarlo. 

## El método congruencial lineal 

El método congruencial lineal es la técnica de generación de números aleatorios más popular. De hecho, muchos de los generadores utilizados actualmente se basan en generadores congruenciales lineales. El método fue propuesto inicialmente por Derrick Lehmer en 1951.

Produce una secuencia de números enteros $X_1$, $X_2$, ... entre cero y $m-1$ siguiendo la siguiente relación recursiva:
$$X_(i+1)=(aX_i+ c) mod m, i=0,1,2,...$$

Esta ecuación da como resultado el residuo de la división entre el número $aX_i + c$ y el número $m$.

El valor inicial $X_0$ se llama semilla, $a$ se llama multiplicador, $c$ es el incremento, y $m$ es el módulo. Todos enteros no negativos. Los enteros $m$, $a$, $c$ y $X_0$ deben satisfacer las siguientes relaciones:
-$0<m$
-$a<m$
-$c<m$
-$X_0>m$

La elección de los valores para a, c, m y X0 afecta las propiedades estadísticas y la longitud del ciclo.

Los números aleatorios se generan dividiendo $X_i/m, i=1,2,...$. La secuencia se repetirá con un periodo $p<=m$, por lo que el generador alcanza el periodo máximo si $p=m$.

Si el incremento c = 0, se denomina método congruencial multiplicativo.

No alcanza el periodo máximo ya que la secuencia no contendrá $X_i = 0$, sin embargo pueden llegar a alcanzar el periodo $m-1$ si se seleccionan $m$ y $a$ en forma adecuada.

Si el incremento $c /= 0$, se denomina método congruencial mixto.

### Pasos del método Congruencial Lineal

Un resumen de los pasos del método congruencial lineal se puede ver a continuación:

![ Paso 1 ]({{ site.baseurl }}/Metodo_congruencial_Paso1.jpg "Paso 1 del método congruencial lineal")
![ Paso 2 ]({{ site.baseurl }}/Metodo_congruencial_Paso2.jpg "Paso 2 del método congruencial lineal")
![ Paso 3 ]({{ site.baseurl }}/Metodo_congruencial_Paso3.jpg "Paso 3 del método congruencial lineal")
![ Paso 4 ]({{ site.baseurl }}/Metodo_congruencial_Paso4.jpg "Paso 4 del método congruencial lineal")

### Desventajas

Su caracter de repetividad, común a todos los generadores de números pseudoaleatorios, que establece que cualquier número generado $X_i$, está totalmente determinado por los valores que caracterizan al generador $m$, $a$, $c$ y por la semilla escogida $X_0$.

Otra objeción con respecto a los generadores congruenciales lineales es que pueden generar solo valores racionales $0, 1/m, 2/m, ... ,(m-1)/m$, en realidad, solo una porción de dichos valores.

Sin embargo, el módulo $m$ se selecciona la mayor parte de las veces como un número muy grande, por lo que los puntos en $[0,1]$ generados son muy densos.

Variaciones sobre la ecuación de la relación recurrente son comunes.

¿Qué te pareció esta historia acerca del orígen de los números aleatorios? Deja tu opinión en la casilla de comentarios.