---
layout: post
comments: True
title: Tests funcionales
tags: talks
eye_catch: ""
---

Las pruebas o test funcionales son pruebas específicas que nos sirven para validar que el software hace lo que debe hacer y no hace lo que no debe hacer.
Básicamente se utilizan para determinar que el sofware está funcionando como se especificó.

Hace unos meses intenté explicar esto a mis compañeros de equipo puesto que todos vamos a poner nuestro granito de arena en probar las aplicaciones lo más profundamente posible.

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/therealmrf/21108879965/in/album-72157657715561460/" title="charla1"><img src="https://farm1.staticflickr.com/731/21108879965_915b075900_b.jpg" width="950" height="635" alt="charla1"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/therealmrf/20487726973/in/album-72157657715561460/" title="charla2"><img src="https://farm6.staticflickr.com/5685/20487726973_e7c52a70fb_b.jpg" width="1024" height="416" alt="charla2"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

Los desarrolladores, con nuestra mente de desarrolladores, tendemos a hacer pruebas unitarias, esto es, probar funcionamientos de tipo: Tengo esta entrada --> debo obtener esta salida.
Pero un test funcional requiere algo más, comprobar una característica por completo, un camino funcional.

De ahí que, si estamos acostumbrados a testear de forma unitaria, no lleguemos a ver "más allá de nuestra nariz" e intentemos probar
nuestra aplicación como si sólo conociésemos el código.

Tenemos que ir más allá, meternos en la piel del usuario que utilizará la aplicación y comprobar los caminos que éste llevará a cabo cuando la maneje.

Plantearnos preguntas:

¿Se puede acceder a esta funcionalidad desde otro sitio? como por ejemplo en el caso
de los registros en webs, a veces, si introduces mal las credenciales a la hora de hacer login, se te redirige a una página donde te invita a registrarte (página distinta a la original de registro).

¿Qué sucede si el usuario accede a este lugar sin hacer antes tal otra cosa? como por ejemplo comprar una canción antes de hacer login ¿te redirige a login?

En fin, mil posibilidades.

Y vosotros, al probar funcionalidades ¿qué os soléis preguntar?

¡A las pruebas!
