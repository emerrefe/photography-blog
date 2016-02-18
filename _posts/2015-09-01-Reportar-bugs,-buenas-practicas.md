---
layout: post
comments: True
title: Reportar un bug, buenas prácticas
tags: tips
eye_catch: ""
---

Esta entrada simplemente pretende plasmar una buena práctica a la hora de seguir un esquema o plantilla 
cuando hay que reportar un bug. 

Para quien no las conoza, existen medios como JIRA, que son herramientas enfocadas a la gestión de las tareas del equipo, es decir, 
son como agendas avanzadas que permiten indicar qué debe hacer cada trabajador, cómo hacerlo, establecer el tiempo
que le ha llevado acometer cierta tarea etc.

Pues bien, cuando testeamos, encontramos bugs y de alguna manera debemos reportarlos para que el resto del 
equipo sepa que existen y se puedan resolver lo antes posible.

Una manera clara de indicar el error que acabamos de detectar, es la siguiente:

1. Crear una nueva issue tipo "bug" (o un nuevo "ticket" donde describiremos el bug) con un título descriptivo de lo que
ha ocurrido, por ejemplo: "Error al publicar una canción favorita en red social"

2. Elegir los valores adecuados para los indicadores "fecha en que ha ocurrido", "entorno", "proyecto" etc, si corresponde

3. La descripción debe ser lo más estricta posible ¡He aquí el quid de la cuestión! por ello ésta contendrá 
los siguientes puntos:

  * **Acciones:** Es donde contarás paso a paso lo que has hecho para reproducir el bug, por ejemplo:
    - Acceder a la web
    - Buscar una canción
    - Agregar esa canción a "mis favoritos"
    - Ir a menú > "mis favoritos"
    - Intentar publicar esa canción en una red social
 
Cuantos más detalles des mejor, piensa que la persona que lo lea, de primeras, no tiene ni idea de qué es lo que ha pasado
ni cómo ha podido ocurrir. Todo detalle es poco.

  * **Comportamiento obtenido:** comentas lo que ha ocurrido + detalles, por ejemplo:
    - Aparece página de error de tipo "loqueseaException"

  * **Comportamiento esperado:** lo que debería haber ocurrido, por ejemplo:
    - Debería aparecer notificación de éxito.

Nos podemos valer además de unas **"Precondiciones"** (como primer punto, antes de los de la lista anteriormente mencionada) y
unas **"Notas"** (como punto final). 
Las "precondiciones" nos sirven para indicar por ejemplo situaciones o elementos necesarios para poder reproducir el bug 
si no se ha podido indicar de alguna forma en el paso 2, por ejemplo: "Ocurre sólo desde el navegador Firefox con versión X".
Las "Notas" por su lado, pueden ser apuntes que creas convenientes para dar luz a los desarrolladores a la hora de afrontar la resolución
o fix de ese error, por ejemplo: "Reproducido sólo entre las 15:00h y las 17:00h ¿ocurrió algo con el entorno en ese periodo de tiempo?"

Con esto, se tiene de una forma sencilla, un reporte de 10. Al final es ahorrar tiempo puesto que, cuanto más detalle,
menos dudas tendrá el receptor de la issue.

Es lo que he aprendido en el día a día, espero que lo pongáis en práctica :)
