# Java Web Servlet #

## Servlet ##

### Introducción ###

Los servlets son una tecnología de Java que permite crear aplicaciones web dinámicas. Un servlet es una clase Java que se ejecuta en un servidor web y maneja las peticiones y respuestas HTTP. Los servlets son especialmente útiles para manejar peticiones de formularios, generar contenido dinámico, y manejar sesiones de usuario.

Para crear un servlet, debes extender la clase HttpServlet e implementar los métodos doGet() o doPost() para manejar las peticiones GET y POST respectivamente. Además, debes registrar el servlet en el archivo web.xml de tu aplicación web para que el servidor web sepa cómo manejar las peticiones para ese servlet.

Los servlets son especialmente útiles para desarrollar aplicaciones web dinámicas, ya que permiten generar contenido dinámico en función de la solicitud del cliente. Por ejemplo, un servlet podría generar una página web dinámica en función de los datos recibidos de un formulario o podría generar una respuesta en formato JSON a una solicitud AJAX.

Los servlets son muy flexibles y escalables, ya que permiten crear aplicaciones web dinámicas que pueden ser ejecutadas en cualquier servidor web que soporte Java. Además, los servlets se pueden combinar con otras tecnologías web como JSP, JSTL y JSF para crear aplicaciones web complejas.

Los servlets son parte de la especificación Java Servlet, que es una interfaz de programación de aplicaciones (API) para desarrollar aplicaciones web en Java. Para utilizar servlets en una aplicación web, es necesario un servidor web compatible con Java Servlet, como Apache Tomcat o Jetty.

Para crear un servlet, se debe crear una clase que extienda de la clase HttpServlet de la API de Java Servlet. Esta clase debe sobreescribir al menos uno de los métodos HTTP (doGet, doPost, doPut, doDelete, etc) para manejar las solicitudes del cliente.
La configuración para que el servidor web redireccione las solicitudes a un servlet se realiza en un archivo web.xml o en la configuración de anotaciones si se esta utilizando JavaEE

Un ejemplo simple de un servlet podría ser el siguiente:

```
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class MiServlet extends HttpServlet {

  public void doGet(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    out.println("<h1>Hola Servlet!</h1>");
  }
}
```

En este ejemplo, el servlet extiende la clase HttpServlet y implementa el método doGet() para manejar las peticiones GET. Dentro del método, se establece el tipo de contenido de la respuesta como "text/html" y se imprime un HTML.

https://www.tutorialspoint.com/servlets/servlets_overview.htm

https://www.javatpoint.com/servlet-tutorial

### Ciclo de vida ###

El ciclo de vida de un servlet en Java se refiere al proceso por el cual un servlet es creado, inicializado, utilizado para procesar solicitudes y finalmente destruido.

1.    Creación: Cuando un servlet es cargado por primera vez por un servidor web, se crea una instancia de la clase del servlet. Esta instancia es creada utilizando el constructor sin argumentos de la clase.

1.    Inicialización: Después de que una instancia del servlet ha sido creada, el servidor web llama al método init() del servlet. El método init() se utiliza para realizar cualquier configuración o inicialización necesaria antes de que el servlet comience a procesar solicitudes.

1.    Manejo de solicitudes: Una vez que un servlet ha sido inicializado, está listo para procesar solicitudes. Cada vez que el servidor web recibe una solicitud para el servlet, llama al método service() del servlet. El método service() a su vez llama al método apropiado (doGet, doPost, etc) para manejar la solicitud. El servlet procesa la solicitud y genera una respuesta adecuada.

1.    Destrucción: Cuando el servidor web decide descargar un servlet (por ejemplo, debido a un cambio en la configuración o un reinicio del servidor), llama al método destroy() del servlet. El método destroy() se utiliza para realizar cualquier limpieza necesaria antes de que la instancia del servlet sea eliminada.

https://www.tutorialspoint.com/servlets/servlets-life-cycle.htm

https://www.javatpoint.com/life-cycle-of-a-servlet

[Ejemplos] (https://www.javatpoint.com/steps-to-create-a-servlet-using-tomcat-server, https://www.tutorialspoint.com/servlets/servlets-first-example.htm)

[Form data] (https://www.tutorialspoint.com/servlets/servlets-form-data.htm)

[Http Request] (https://www.tutorialspoint.com/servlets/servlets-client-request.htm, https://www.javatpoint.com/servletrequest)

[Server response] (https://www.tutorialspoint.com/servlets/servlets-client-request.htm)
