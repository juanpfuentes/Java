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

### Ejemplos ###

 Aquí hay algunos ejemplos de cómo crear y usar un servlet en Java:

Creación de un servlet básico:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class HelloWorldServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Hello World!</h1>");
    }
}
```
Uso de parámetros en un servlet:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class GreetingServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String name = request.getParameter("name");
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Hello " + name + "!</h1>");
    }
}
Uso de un archivo JSP en un servlet:
Copy code
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class JSPExampleServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        request.setAttribute("message", "Hello World!");
        RequestDispatcher view = request.getRequestDispatcher("example.jsp");
        view.forward(request, response);
    }
}
```

Creación de un servlet que maneja varios métodos HTTP:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class MyServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes GET
    }

    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes POST
    }

    public void doPut(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes PUT
    }

    public void doDelete(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes DELETE
    }
}
```

Creación de un servlet que maneja una ruta específica:

```
import javax.servlet.*;
import javax.servlet.annotation.*;
import javax.servlet.http.*;

@WebServlet("/mypath/*")
public class MyServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes GET a la ruta especificada
    }
}
```

Creación de un servlet que maneja varias rutas:

```
import javax.servlet.*;
import javax.servlet.annotation.*;
import javax.servlet.http.*;

@WebServlet({"/path1/*", "/path2/*"})
public class MyServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // manejar solicitudes GET a las rutas especificadas
    }
}
```

Recuerda que para utilizar los servlets anotados es necesario que tu proyecto tenga configurado el Servlet 3.0 o superior y también es necesario que tengas un archivo web.xml donde se configura el dispatcher para que funcionen las anotaciones.

Ten en cuenta que estos son solo ejemplos básicos y hay muchas otras cosas que puedes hacer con los servlets, como el manejo de sesiones, la autenticación y autorización, y la manipulación de datos en una base de datos.

https://www.javatpoint.com/steps-to-create-a-servlet-using-tomcat-server

https://www.tutorialspoint.com/servlets/servlets-first-example.htm

### Form data ###

Puedes manejar los datos de un formulario enviado a un servlet utilizando el objeto HttpServletRequest. Aquí hay algunos ejemplos de cómo manejar los datos de un formulario enviado a un servlet:

Manejo de datos de formulario con el método getParameter:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class FormServlet extends HttpServlet {
    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String name = request.getParameter("name");
        String email = request.getParameter("email");
        // procesar los datos del formulario
    }
}
```

Manejo de datos de formulario con el método getParameterValues:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class FormServlet extends HttpServlet {
    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String[] hobbies = request.getParameterValues("hobbies");
        // procesar los datos del formulario
    }
}
```

Manejo de datos de formulario con el método getParameterMap:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;
import java.util.*;

public class FormServlet extends HttpServlet {
    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        Map<String, String[]> formData = request.getParameterMap();
        // procesar los datos del formulario
    }
}
```

Ten en cuenta que para que estos ejemplos funcionen, el servlet debe estar configurado para manejar solicitudes HTTP POST, y el formulario en la página HTML debe tener su atributo method configurado como "post".

También es recomendable validar los datos del formulario antes de procesarlos para asegurarte de que son válidos y manejar errores adecuadamente si los datos son inválidos.

https://www.tutorialspoint.com/servlets/servlets-form-data.htm

### Http Request ###

El objeto HttpServletRequest es una clase proporcionada por el paquete javax.servlet.http y es utilizado para recibir y manejar solicitudes HTTP en un servlet.

Un objeto HttpServletRequest es pasado como parámetro en el método service o en los métodos específicos (doGet, doPost, doPut, doDelete) de un servlet. A través de este objeto, puedes acceder a información sobre la solicitud, como los parámetros enviados en la solicitud, los encabezados HTTP, la información del cliente, entre otros.

Aquí hay algunos ejemplos de cómo utilizar el objeto HttpServletRequest en un servlet:

Accediendo a los parámetros enviados en la solicitud:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class RequestServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String name = request.getParameter("name");
        String age = request.getParameter("age");
        // procesar los parámetros
    }
}
```

Accediendo a los encabezados HTTP en la solicitud:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class RequestServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String userAgent = request.getHeader("User-Agent");
        String acceptLanguage = request.getHeader("Accept-Language");
        // procesar los encabezados
    }
}
```

    Obtener las cookies de la solicitud:

```
Cookie[] cookies = request.getCookies();
```

    Obtener la URI de la solicitud:

```
String requestURI = request.getRequestURI();
```

    Obtener el método HTTP utilizado en la solicitud:

```
String method = request.getMethod();
```

    Obtener el objeto HttpSession asociado a la solicitud:

```
HttpSession session = request.getSession();
```

    Obtener el objeto ServletContext asociado a la solicitud:

```
ServletContext context = request.getServletContext();
```

    Obtener el objeto HttpServletResponse asociado a la solicitud:

```
HttpServletResponse response = (HttpServletResponse) request.getAttribute("HTTP_RESPONSE");
```

https://www.tutorialspoint.com/servlets/servlets-client-request.htm

https://www.javatpoint.com/servletrequest

### Variables de sesión ###

Para usar variables de sesión en un servlet de Java, primero debes obtener el objeto HttpSession del objeto HttpServletRequest, que es el objeto que representa la solicitud HTTP que llega al servidor. Para hacer esto, debes llamar al método getSession() del objeto HttpServletRequest, como se muestra a continuación:

```

HttpSession session = request.getSession();
```

Una vez que tienes el objeto HttpSession, puedes guardar cualquier objeto Java en él utilizando el método setAttribute(), como se muestra a continuación:

```
session.setAttribute("nombreVariable", objetoJava);
```

El primer argumento es el nombre de la variable que quieres guardar en la sesión, y el segundo argumento es el objeto Java que quieres guardar.

Para obtener el valor de una variable de sesión, debes llamar al método getAttribute() del objeto HttpSession, como se muestra a continuación:

```
Object objetoJava = session.getAttribute("nombreVariable");
```

El valor devuelto por el método getAttribute() es un objeto Java, por lo que debes convertirlo al tipo de objeto que deseas utilizar.

Por ejemplo, si quieres guardar el nombre de usuario de un usuario en una variable de sesión, puedes hacerlo de la siguiente manera:

```
String username = "john";
session.setAttribute("username", username);
```

Para obtener el valor de la variable de sesión del usuario, puedes hacerlo de la siguiente manera:

```
String username = (String) session.getAttribute("username");
```

Es importante tener en cuenta que las variables de sesión son específicas del usuario y no se comparten entre usuarios. También debes tener en cuenta que las variables de sesión se almacenan en la memoria del servidor, por lo que no deben ser utilizadas para almacenar grandes cantidades de datos.

### Server response ###

El objeto HttpServletResponse es una clase proporcionada por el paquete javax.servlet.http y es utilizado para enviar una respuesta HTTP desde un servlet.

Un objeto HttpServletResponse es pasado como parámetro en el método service o en los métodos específicos (doGet, doPost, doPut, doDelete) de un servlet. A través de este objeto, puedes establecer el código de estado de respuesta, los encabezados HTTP y escribir el cuerpo de la respuesta.

Aquí hay algunos ejemplos de cómo utilizar el objeto HttpServletResponse en un servlet:

Estableciendo el código de estado de respuesta:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class ResponseServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setStatus(HttpServletResponse.SC_OK);
    }
}
```

Estableciendo encabezados HTTP en la respuesta:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class ResponseServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setHeader("Content-Type", "text/html");
        response.setHeader("X-Custom-Header", "Value");
    }
}
```

Escribiendo el cuerpo de la respuesta:

```
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class ResponseServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        PrintWriter out = response.getWriter();
        out.println("<html>");
        out.println("<body>");
    }
}
```

https://www.tutorialspoint.com/servlets/servlets-client-request.htm

Para pasar un valor desde un servlet a una página JSP, puedes utilizar el objeto HttpServletRequest y el objeto RequestDispatcher.

Aquí hay un ejemplo que muestra cómo pasar un valor desde un servlet a una página JSP:

En el servlet, establece el valor que deseas pasar a la página JSP en un atributo del objeto HttpServletRequest utilizando el método setAttribute():

```
String message = "Hola desde el servlet";
request.setAttribute("mensaje", message);
```

Obtén un objeto RequestDispatcher para la página JSP que deseas mostrar. Esto se hace utilizando el método getRequestDispatcher() del objeto ServletContext:

```
RequestDispatcher dispatcher = getServletContext().getRequestDispatcher("/pagina.jsp");
```

Nota: Asegúrate de ajustar "/pagina.jsp" al nombre de la página JSP que deseas mostrar.

Llama al método forward() del objeto RequestDispatcher para redirigir la solicitud a la página JSP:

```
dispatcher.forward(request, response);
```

En la página JSP, puedes obtener el valor que se pasó desde el servlet utilizando el objeto request y el método getAttribute():

```
<p><%=request.getAttribute("mensaje")%></p>
```

El código completo del servlet se vería así:

```
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class MiServlet extends HttpServlet {

   public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
      String message = "Hola desde el servlet";
      request.setAttribute("mensaje", message);

      RequestDispatcher dispatcher = getServletContext().getRequestDispatcher("/pagina.jsp");
      dispatcher.forward(request, response);
   }
}
```

El código completo de la página JSP se vería así:


```
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
   <head>
      <title>Página JSP</title>
   </head>
   <body>
      <p><%=request.getAttribute("mensaje")%></p>
   </body>
</html>
```

Cuando el usuario solicita el servlet, se establece el valor "Hola desde el servlet" en un atributo del objeto HttpServletRequest utilizando el método setAttribute(). Luego, se obtiene un objeto RequestDispatcher para la página JSP y se llama al método forward() para redirigir la solicitud a la página JSP. En la página JSP, se obtiene el valor que se pasó desde el servlet utilizando el objeto request y el método getAttribute().