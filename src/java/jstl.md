# JSTL en Java  #

## Introducción ##

JSTL es el acrónimo de Java Standard Tag Library. Es una librería de etiquetas que proporciona una colección de etiquetas JSP (JavaServer Pages) para simplificar el desarrollo de aplicaciones web.

JSTL es una librería estándar que proporciona una serie de etiquetas que pueden ser utilizadas en las páginas JSP para realizar una variedad de tareas comunes, como la iteración sobre una colección de datos, la ejecución de expresiones lógicas y aritméticas, la gestión de fechas y números, la internacionalización, etc.

Algunas de las principales ventajas de usar JSTL son:

Simplifica el código JSP, ya que las tareas comunes se realizan con etiquetas simples en lugar de código Java.
Permite a los desarrolladores centrarse en la lógica de la aplicación, en lugar de preocuparse por la presentación de datos.
Proporciona una solución estandarizada para tareas comunes, lo que reduce la necesidad de crear soluciones personalizadas.
Para utilizar JSTL en un proyecto Java, es necesario incluir las librerías correspondientes en el classpath de la aplicación y utilizar las etiquetas JSTL en las páginas JSP.

Para usarlo con jakarta hay que poner:

```
<%@taglib uri="http://java.sun.com/jstl/core" prefix="c" %>
```

## JSTL core ##

JSTL proporciona una serie de etiquetas en su librería Core que se utilizan para realizar tareas comunes en el desarrollo de aplicaciones web. Algunos de los tags más comunes de JSTL Core incluyen:

c:if: Este tag se utiliza para realizar una evaluación condicional en una página JSP. Por ejemplo, se puede utilizar para mostrar un mensaje solo si una determinada condición se cumple.

```
<c:if test="${not empty myVariable}">
   My variable is not empty.
</c:if>
```

c:forEach: Este tag se utiliza para iterar sobre una colección de datos en una página JSP. Por ejemplo, se puede utilizar para mostrar una lista de productos.

```
<c:forEach items="${products}" var="product">
   <p>Product: ${product}</p>
</c:forEach>
```

c:out: Este tag se utiliza para mostrar el valor de una variable en una página JSP. Por ejemplo, se puede utilizar para mostrar el valor de una variable de sesión.

```
<p>The value of myVariable is: <c:out value="${myVariable}"/></p>
```

c:set: Este tag se utiliza para asignar un valor a una variable en una página JSP. Por ejemplo, se puede utilizar para asignar un valor a una variable de sesión.

```
<c:set var="myVariable" value="Hello, World!" />
```

c:import: Este tag se utiliza para importar un recurso externo en una página JSP. Por ejemplo, se puede utilizar para importar un archivo CSS o JavaScript.

```
<c:import url="header.jsp" />
```

Estos son solo algunos ejemplos de los tags que se incluyen en la librería Core de JSTL. Hay muchos otros tags disponibles que se pueden utilizar para realizar una variedad de tareas en una aplicación web.

## Format tags ##

JSTL también proporciona una serie de etiquetas en su librería Format que se utilizan para dar formato a los datos en una página JSP. Algunos de los tags más comunes de JSTL Format incluyen:

f:formatNumber: Este tag se utiliza para dar formato a números en una página JSP. Por ejemplo, se puede utilizar para formatear un número como moneda.

```
<p>The price is: <f:formatNumber value="${price}" type="currency" /></p>
```

f:formatDate: Este tag se utiliza para dar formato a fechas en una página JSP. Por ejemplo, se puede utilizar para formatear una fecha como "dd-MM-yyyy".

```
<p>Today's date is: <f:formatDate value="${today}" pattern="dd-MM-yyyy" /></p>
```

f:formatMessage: Este tag se utiliza para dar formato a mensajes en una página JSP. Por ejemplo, se puede utilizar para mostrar un mensaje internacionalizado.

```
<f:formatMessage key="welcome.message"/>
```

f:timeZone: Este tag se utiliza para dar formato a zonas horarias en una página JSP. Por ejemplo, se puede utilizar para mostrar la hora local de un usuario.

```
<p>The local time is: <f:formatDate value="${currentTime}" timeZone="${userTimeZone}" pattern="hh:mm a" /></p>
```

Estos son solo algunos ejemplos de los tags que se incluyen en la librería Format de JSTL. Hay muchos otros tags disponibles que se pueden utilizar para dar formato a los datos en una aplicación web.

## SQL tags ##

JSTL también proporciona una serie de etiquetas en su librería SQL que se utilizan para trabajar con bases de datos en una página JSP. Algunos de los tags más comunes de JSTL SQL incluyen:

sql:setDataSource: Este tag se utiliza para establecer una fuente de datos en una página JSP. Por ejemplo, se puede utilizar para establecer una conexión a una base de datos MySQL.

```
<sql:setDataSource var="dataSource" driver="com.mysql.jdbc.Driver" url="jdbc:mysql://localhost:3306/testDB" user="root" password="password"/>
```

sql:query: Este tag se utiliza para ejecutar una consulta en una base de datos en una página JSP. Por ejemplo, se puede utilizar para seleccionar todos los productos de una tabla.
```
<sql:query dataSource="${dataSource}" var="result" sql="SELECT * FROM products">
</sql:query>
```

sql:update: Este tag se utiliza para ejecutar una sentencia de actualización en una base de datos en una página JSP. Por ejemplo, se puede utilizar para actualizar el precio de un producto.

```
<sql:update dataSource="${dataSource}" sql="UPDATE products SET price=${newPrice} WHERE id=${productId}">
</sql:update>
```

Estos son solo algunos ejemplos de los tags que se incluyen en la librería SQL de JSTL. Hay muchos otros tags disponibles que se pueden utilizar para trabajar con bases de datos en una aplicación web.

Es importante mencionar que, aunque JSTL ofrece una forma fácil de trabajar con bases de datos en una página JSP, en general se recomienda utilizar una capa de acceso a datos separada y un patrón de arquitectura adecuado en lugar de incluir directamente código SQL en las páginas JSP. Esto ayuda a mejorar la seguridad, la escalabilidad y la mantenibilidad de la aplicación.

https://help.hcltechsw.com/commerce/9.1.0/admin/refs/rsdjspbpjstl_dup.html

http://www.jtech.ua.es/j2ee/restringido/cw/sesion08-apuntes.html

https://www.baeldung.com/jstl

https://www.javatpoint.com/jstl