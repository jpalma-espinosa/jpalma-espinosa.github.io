---
layout: single
category: blog
title: 'Modelamiento cerebral para la galería: Conectoma'
date: 2019-03-10
permalink: /blog/research-unit
tags: 
- Data Science
- python
- Vino
---


# Introducción
¡Uf! Ya no recuerdo cuándo fue la última vez que escribí en este blog/página (mentira, si me acuerdo, pero me da lata asumir que fue hace tanto tiempo). Como lo dije [hace un tiempo](http://javierpalmaespinosa.cl/science/que-hago), me propuse 
>>
[ir] explicando mi trabajo, algún paper interesante, las consecuencias sociales y económicas de las investigaciones que se realicen en el planeta(ok ok, redondeta para los terraplanistas)  y, en definitiva, intentar acercar a la ciencia a la sociedad, todo esto ~~en cómodas cuotas mensuales~~ castellano

Si bien me demoré un montón en escribir, la excusa era principalmente que no tenía nada interesante que decir.  Pues bien, ahora si tengo algo interesante y me gustaría compartirlo con la mayor cantidad de gente que pueda.

Esta entrada será la primera de unas cuántas (muy posiblemente tres), en donde explicaré en simple algo que me propuse explicar antes **"Neurociencia Computacional, ¿qué carajos es?"**

En esta primera entrada, quiero intentar explicar el modelamiento cerebral que se hace desde hace un tiempo en los diferentes laboratorios de investigación. Por qué se hace y cómo lo entendemos. 

Asi que, ¡empecemos! Mis palabras serán tan claras como en la televisión...

# En el comienzo fue...

El 30 de septiembre del 2005, eran tiempos tumultuosos en nuestra nación: Monica Belucci y Crespita Rodríguez celebraban su cumpleaños(no en conjunto),  las nuevas bebidas nos daban una razón para vivir, el noticiario nocturno nos mostraba lo que algunos cerebritos piensan de viaje a las estrellas [y la domesticación del perro, seguía su marcha sin parar](https://youtu.be/Ytfwyf3myVc?t=140). Además de eso, se publicaba un [paper importantísimo](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.0010042) en el área de la *conectómica*
¿Qué es la conectómica? Según [Wikipedia](https://en.wikipedia.org/wiki/Connectomics), la conectómica es la producción y estudio de los conectomas ~~puta, gracias, weon ¬¬~~ y los conectomas son mapas de la conexión de las diferentes neuronas en el cerebro.  Osea, en simple, la conectómica es la disciplina que se encarga de estudiar los mapas que muestran las conexiones de las neuronas, no sólo en el cerebro, sino también en el sistema nervioso de otros organismos.

Acá quiero hacer dos paradas: La primera es para explicar muy en general qué es una neurona y cómo se estructura el sistema nervioso, y la segunda es ~~para ir a hacerme un café~~ para explicar y dar una idea general de cómo llegamos tan lejos.

## Sistema Nervioso: Desde las medusas y corales hasta los humanos en 2 minutos(o menos)
Antiguamente, cuando no habían muchos animales más que los que vivían en el mar, los primeros en desarrollar algo parecido a un sistema nervioso fueron los [*cndaria*](https://es.wikipedia.org/wiki/Cnidaria), un grupo de animalitos que incluye a medusas y corales (yup, corales, como los de la foto).
![Coral](http://javierpalmaespinosa.cl/blog/img/coral.jpg)

Estos animalitos (créalo o no, los corales son animalitos. Yo también quedé :o cuando lo supe) desarrollaron las primeras neuronas, algo muy básico, pero que les servía para sensar ciertas presas, cambios en el ambiente, etc.  Para sobrevirir, estos animales debieron irse adaptando a su medioambiente.  Por ello, empezaron a desarrollar sistemas de sensado muchísimo más complejos, lo que a su vez les permitió generar comportamientos más complejos.  Estos comportamientos exigían una coordinación mayor entre las neuronas que propagan la información. Por esto, se empezó a desarrollar una estructura que coordinara a estas neuronas: El cerebro.

Aún no hay un consenso en cómo surgió el cerebro. Sin embargo, se sabe es que ciertos organismos empezaron a desarrollar una simetría bilateral y, al parecer, esta simetría es la más utilizada en la naturaleza.  Es esta bilateralidad la que impone, por geometría, una parte de "adelante" y una parte de "atrás".  Imagina cualquier animalito: un perro, una araña, una mariposa, un pulpo o **un humano**.  Todos ellos tienen una cabeza y una cola (o algo similar).  Si imaginariamente se traza una linea que conecte la cabeza con la cola del animal, tenemos dos mitades iguales (la izquierda y la derecha), pero también hay una parte de adelante (arriba en los animales que andan en dos patas) y una parte trasera (o abajo). ¡Esta división permitió la separación de funciones y de sistemas sensoriales! Ahora el animalito se mueve hacia atrás y adelante (¿tiene adelante o atrás una estrella de mar o un coral?) y será ese adelante donde pasarán las cosas interesantes: podrá ver, podrá ingerir comida, podrá oler, [sensar campos eléctricos](https://es.wikipedia.org/wiki/Mormyridae), entre otras cosas.  Todo esto pasará en la parte delantera de este animalito, por lo tanto, tiene sentido colocar un órgano que coordine todos estos nuevos órganos sensoriales y el bombardeo de información que entregan.
Si quieres más información, hay un resumen muy bueno, bastante más técnico y en inglés. Lo puede ver [acá](https://www.springer.com/cda/content/document/cda_downloaddocument/9783642107689-c1.pdf?SGWID=0-0-45-1404406-p174537886)

## Estructura del Sistema Nervioso: desde el martillo hacia el dedo (con un ¡mierda! incluído)
Ok, ya tenemos un animal, con parte delantera/trasera y tiene un cerebro...¿cómo se ordena todo esto? Lo primero que hay que saber es que el sistema nervioso es uno solo. Somos nosotros, para simplificar el estudio, que lo dividimos en **Sistema Nervioso Central(SNC)** y **Sistema Nervioso Periférico**.  En términos generales, el sistema nervioso es simplemente un montón de neuronas conectadas entre ellas.  Las mismas neuronas que las primeras medusas desarrollaron, gracias a la evolución, se especializaron cada vez más.  En los mamíferos, los últimos animales en aparecer en el planeta, podemos reconocer neuronas piramidales, células granulares, céluas del sistema visual(la retina), interneuronas (comunicación ENTRE neuronas),y la lista es eterna!! Sin embargo, en términos generales, sólo existen tres tipos de neuronas: *Primarias o sensitivas, interneuronas y efectoras o motoras*(Acabo de encontrar un [link](https://es.khanacademy.org/science/biology/human-biology/neuron-nervous-system/a/overview-of-neuron-structure-and-function) muy bueno, de Khan Academy que explica con un nivel de detalle respetable el funcionamiento del sistema nervioso).

Estas neuronas tienen como único objetivo el transmitir **información** *desde* el medio externo hacia el medio interno del animal. Esta información se procesa y genera una respuesta que el animal ejercerá *sobre* el medio. La forma de realizar este procesamiento es a través de un montón de transformaciones de esta información. Vamos a tomar el ejemplo de acercar la mano a una estufa.

![SNC](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/SNerviosoC.png/245px-SNerviosoC.png)



```python
red_wine.describe() #esto me entrega estadísticas generales de las columnas
```







![png](http://javierpalmaespinosa.cl/_science/img/output_32_0.png)


### Paso 6(opcional pero necesario): Conclusiones
Usualmente este paso, si bien no siempre es escrito, siempre es necesario, pues permite ver si se respondió la pregunta planteada en el paso 1 o no.
En este caso, no es posible diferenciar la calidad de los 3 vinos analizados, sólo conociendo su densidad y su acidez. Si bien se observa que existen diferencias en las pendientes, en la nube de puntos no es posible diferenciar a los datos, por lo tanto el ajuste por mínimos cuadrados no es suficiente y se requieren otras técnicas para poder estimar la calidad del vino.

# Comentarios
Después de toda esa lata, logré por fin darme cuenta que mi modelo ~~vale callampa~~ requiere más información y quizá un análisis estadístico clásico no es suficiente. Es en este punto donde viene la necesidad de contar con más herramientas. A estas herramientas se les conoce como "Machine Learning" y espero poder hacer luego o no tan luego, un post sobre eso.
Sea cortés, ande con cuidado, edúquese lo mas que pueda, respete para que lo respeten...Y que Dios noh ampare!!


# Canción del Día: La Combo Tortuga - Amor Borracho
[![La Combo Tortuga - Amor Borracho](https://i.ytimg.com/vi/P4YR6lJsuTE/maxresdefault.jpg)](https://www.youtube.com/watch?v=QPmB8zs0SF0)
## Bonus Track (para escucharla con un vinito)
[![El bloque Depresivo - Regresa](https://www.fuzzpass.com/media/Producer/logos/Logo_productor.jpg)](https://www.youtube.com/watch?v=Fqme8r2PHWU)



# Referencias y lectura adicional
1. Sporns, O., Tononi, G., & Kötter, R. (2005). The human connectome: a structural description of the human brain. PLoS computational biology, 1(4), e42.

