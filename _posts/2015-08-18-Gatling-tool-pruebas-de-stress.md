---
layout: post
title: Gatling tool, pruebas de stress
tags: git tips more
eye_catch: ""
---

Gatling es una herramienta opensource de stress que permite realizar pruebas de carga a un entorno o web para estudiar su 
rendimiento.

Es fácil simular un escenario previamente grabado, es decir, puedes abrir tu navegador, realizar los pasos que quieras (*por ejemplo:* abrir una web y realizar un registro de usuario) y tras esto simular ese recorrido tantas veces como desees para comprobar cuanta carga es capaz de soportar tu web o entorno.

Además, al terminar te genera unos informes bastante majos con información sobre cada sesión simulada, tiempos de respuesta y peticiones que han resultado ok o no_ok.

## Pasos:
* Descarga [Gatling](http://gatling.io/#/download)
* Usaremos por ejemplo el navegador Firefox. Cargar en una pestaña la web que queremos probar.

```
$ cd gatling/bin
```

```
$ ./recorder.sh
```

* Configurar el proxy en firefox, desde **Preferencias > Avanzado > Red > Configuración > marcar configuración manual de proxy** y establecer el **puerto 8000**
* Comenzar la grabación desde la interfaz de Gatling, establecer un nombre para la simulación que resultará de grabar dicho camino, se observará que van apareciendo los pasos en rojo
* Finalmente parar la grabación, en estos momentos tendremos la simulación generada en **gatling/user-files/simulations/nombre-de-la-simulación.scala**

Ahora para lanzar la simulación habría que lanzar:

```
$ ./gatling.sh 
```

y elegir el número que corresponda a nuestra simulación, de esa forma estaríamos lanzando nuestro escenario de nuevo.

La clave para meter caña está en modificar el método setUp de la simulación .scala generada con el recorder, así, por ejemplo, cambiaremos la cantidad de usuarios por segundo que queremos inyectar.

Tras lanzar la simulación, los informes resultantes se almacenan en la carpeta **gatling/results/fecha-de-la-simulación/index.html**


Para quien tenga curiosidad, en su web explican cada una de las partes que componen un [escenario](http://gatling.io/docs/2.1.7/quickstart.html#gatling-scenario-explained)

Todo esto se puede implementar diréctamente sin necesidad de grabar el camino y obtener la clase .scala con la simulación (y ahí es donde se tiene el poder de esta herramienta) pero quería escribir primero sobre el grabador que Gatling nos facilita para que lo conozcáis.

Llegado este punto vemos el potencial que puede llegar a tener esta herramienta pero parece no tener mucho sentido realizar unas pruebas de carga por ejemplo utilizando al mismo usuario, no es normal que se intente registrar la misma persona, en un entorno real, una y otra vez. ¡Pues bien! con Gatling podemos injectar un *.csv* utilizando feeders, de tal forma que consigamos crear un escenario real, donde en cada sesión tendremos a un usuario distinto intentando registrarse en la web. Pero esto, da para otro tema de conversación :)

Espero que sea de ayuda y empecéis a investigar.
