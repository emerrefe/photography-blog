---
layout: post
title: Patrón PageObject
tags: test patterns
eye_catch: ""
---

El patrón Page Object se ha puesto muy de moda en el mundo de las pruebas funcionales debido a que nos ayuda a 
tener un código más limpio, una mejor estructura de proyecto y en definitiva un código más mantenible.

Se basa sencillamente en separar toda la implementación de la aplicación de lo que es su funcionamiento. 
De esta forma nos centramos en probar nuestra web página a página, como si un usuario navegara a través de ella
y teniendo en cuenta que cada página para nosotros será un objeto. Así sólo nos quedará interactuar con cada uno 
de ellos y devolver un objeto (página) inmediatamente posterior para poder encadenar caminos funcionales.

Para tener una imagen clara de esto, imaginemos una aplicación con distintas páginas o elementos como la siguiente:

1. Vista de la página de Registro
2. Vista de la página de Login
3. Página de Gestión de usuarios
4. Página de Gestión de notas
5. Logout (en la misma vista que las páginas de gestión)

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/135417629@N05/24080076590/in/dateposted-public/" title="pageobject"><img src="https://farm2.staticflickr.com/1639/24080076590_60ed5f1403_b.jpg" width="965" height="825" alt="pageobject"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

Y en cada página tendremos agrupado todo el comportamiento de la misma, es decir, ¿qué se puede hacer en cada página?

  * **para 1** tendremos todas las acciones que se pueden llevar a cabo en un registro (rellenar formunario ok, rellenar formulario de forma incorrecta, marcar check, aceptar)
  * **para 2** tendremos todas las acciones para realizar un login  (rellenar formulario ok, rellenar formulario de forma incorrecta, aceptar)
  * **para 3** idem (rellenar campos, buscar y añadir nuevo usuario)

así sucesivamente...

Teniendo esto, se pueden crear tests de cada página, por ejemplo:

  * **para 1**
    - registro ok (que implica rellenar ok el formulario + marcar check + aceptar)
    - registro no_ok (por ejemplo rellenar ok + no marcar check + aceptar)
 
  * **para 2**
    - login ok (rellenar formulario ok + aceptar)

  * **para 3**
    - buscar usuario (rellenar campos + buscar)


De este modo, cada página permite que sus métodos enlacen con los métodos de otras páginas.
Y bien, sólo quedaría unir estos métodos entre ellos para formar caminos funcionales así:

**registro ok** > **login ok** > **buscar usuario** > **cerrar sesión**


Este patrón está muy relacionado con otro llamado PageFactory a nivel de código.
En un nuevo post explicaré este otro ;)

¡Saludos!
