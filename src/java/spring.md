# Java Programación orientada a objetos #

## Spring ##

### Introducción ###

Spring es un framework para el desarrollo de aplicaciones en Java. Es uno de los frameworks más populares para la construcción de aplicaciones empresariales. Spring ofrece un enfoque modular que permite a los desarrolladores crear aplicaciones más fácilmente y con menos código repetitivo.

El framework Spring se divide en varios módulos, cada uno de los cuales ofrece un conjunto de características específicas para diferentes necesidades de desarrollo. Algunos de los módulos más utilizados son Spring Core, Spring MVC, Spring Data, Spring Security, Spring AOP y Spring Boot.

Spring Core es el módulo central de Spring y proporciona las funcionalidades fundamentales del framework, como la gestión de dependencias y la inversión de control. Spring MVC es un módulo para el desarrollo de aplicaciones web basado en el patrón Modelo-Vista-Controlador. Spring Data es un módulo para trabajar con bases de datos y simplificar el acceso a los datos. Spring Security es un módulo para la gestión de la seguridad de la aplicación.

Spring AOP es un módulo para la programación orientada a aspectos, lo que permite separar las preocupaciones transversales de la aplicación. Spring Boot es un módulo que facilita la creación de aplicaciones autocontenidas que se ejecutan sin necesidad de configuración adicional.

En resumen, Spring es un framework de desarrollo de aplicaciones empresariales muy completo y flexible, que proporciona una amplia variedad de funcionalidades para simplificar el desarrollo de aplicaciones y mejorar su calidad.


## Creación ##

Los pasos que debes seguir para crear una aplicación de Spring pueden variar dependiendo de las necesidades específicas de tu proyecto, pero a grandes rasgos, estos son los pasos que puedes seguir:

Configurar el entorno de desarrollo: Debes asegurarte de tener instalado en tu equipo el JDK (Java Development Kit) y un IDE (Integrated Development Environment) como Eclipse o IntelliJ IDEA.

Crear un proyecto de Spring: Puedes crear un proyecto de Spring utilizando una herramienta como Spring Initializr o a través de la creación manual de un proyecto en tu IDE.

Configurar las dependencias: Es necesario incluir las dependencias que necesites para el desarrollo de tu aplicación en el archivo pom.xml (en caso de estar usando Maven) o build.gradle (en caso de estar usando Gradle).

Crear las clases y componentes: En Spring, las clases que actúan como componentes son administradas por el contenedor de Spring y pueden ser inyectadas en otras clases. Puedes crear las clases y componentes necesarios para tu aplicación y configurar las inyecciones de dependencias.

Configurar el archivo de configuración: En Spring, es posible configurar las opciones de la aplicación mediante el archivo de configuración. Puedes crear y configurar el archivo de configuración de acuerdo con las necesidades de tu aplicación.

Ejecutar la aplicación: Una vez que hayas configurado y creado todos los componentes y archivos necesarios, puedes ejecutar tu aplicación y realizar pruebas para asegurarte de que funciona correctamente.

Estos son los pasos generales que puedes seguir para crear una aplicación de Spring. Ten en cuenta que existen muchos recursos y documentación disponible en línea para guiarte en el proceso de desarrollo.

## Spring boot ##

 Spring Boot es un módulo del framework Spring que facilita la creación de aplicaciones Java autónomas y autoconfigurables.

Spring Boot se basa en el principio de "opinión sobre configuración" (conocido en inglés como "convention over configuration"), lo que significa que se utiliza una configuración predeterminada que se adapta automáticamente a las necesidades de la aplicación, en lugar de tener que configurar cada aspecto de la aplicación de forma manual.

Spring Boot también incluye un conjunto de características que ayudan a reducir el tiempo y esfuerzo necesarios para crear una aplicación Java, como por ejemplo:

Un servidor integrado que permite ejecutar la aplicación sin necesidad de instalar un servidor externo.
Una fácil configuración de dependencias mediante el archivo pom.xml (en caso de estar usando Maven) o build.gradle (en caso de estar usando Gradle).
La posibilidad de empaquetar la aplicación en un archivo JAR ejecutable.
La posibilidad de utilizar propiedades externas para configurar la aplicación, lo que permite cambiar la configuración sin necesidad de modificar el código fuente.
La posibilidad de generar automáticamente un sitio web con información detallada sobre la aplicación y sus componentes.
En resumen, Spring Boot simplifica significativamente el proceso de desarrollo de aplicaciones Java al proporcionar una configuración predeterminada, una fácil configuración de dependencias y una amplia variedad de características útiles.

## Spring Initializr ##

Spring Initializr es una herramienta en línea que permite generar fácilmente un esqueleto de proyecto para aplicaciones de Spring Boot.

Con Spring Initializr, puedes especificar las características de la aplicación que deseas crear, como el lenguaje de programación, la versión de Spring Boot, las dependencias necesarias, el paquete base de la aplicación, entre otros aspectos. Una vez especificadas estas características, Spring Initializr generará un archivo ZIP que contiene el proyecto inicial listo para ser importado en tu IDE (Eclipse, IntelliJ IDEA, NetBeans, etc.) y comenzar a desarrollar.

Spring Initializr se puede utilizar de diferentes maneras, pero una forma común es a través de la interfaz web en línea. Para usar Spring Initializr en línea, sigue estos pasos:

Accede a la página web oficial de Spring Initializr en https://start.spring.io/.
Especifica las características de tu aplicación en la página principal de Spring Initializr, como el lenguaje de programación, la versión de Spring Boot, las dependencias necesarias, el paquete base de la aplicación, entre otros aspectos.
Haz clic en el botón "Generate" para generar un archivo ZIP con el proyecto inicial.
Descarga el archivo ZIP generado y descomprímelo en una ubicación local de tu equipo.
Importa el proyecto en tu IDE y comienza a desarrollar.
Además de la interfaz web en línea, también es posible utilizar Spring Initializr mediante herramientas de línea de comandos o integraciones con otras herramientas de desarrollo, como Maven o Gradle.

En resumen, Spring Initializr es una herramienta muy útil para generar rápidamente un esqueleto de proyecto para aplicaciones de Spring Boot, lo que permite a los desarrolladores ahorrar tiempo y esfuerzo en la configuración inicial de la aplicación.

## application.properties ##

l archivo application.properties es un archivo de configuración muy útil en las aplicaciones de Spring que permite especificar una amplia variedad de configuraciones para la aplicación. Algunas de las opciones más comunes que se pueden configurar en application.properties son:

server.port: especifica el puerto en el que se ejecutará el servidor web integrado de Spring Boot.

spring.datasource.url, spring.datasource.username, spring.datasource.password: especifica la URL de la base de datos, el nombre de usuario y la contraseña para la conexión a una base de datos.

spring.jpa.hibernate.ddl-auto: especifica el modo de generación de tablas de Hibernate para JPA (create, create-drop, update, validate, none).

spring.jpa.show-sql: especifica si se deben mostrar o no las consultas SQL generadas por Hibernate.

logging.level: especifica el nivel de registro para las diferentes clases de la aplicación (por ejemplo, logging.level.org.springframework.web=DEBUG para registrar las solicitudes web).

spring.profiles.active: especifica los perfiles de Spring activos para la aplicación.
Estas son solo algunas de las opciones más comunes que se pueden configurar en application.properties. Cada aplicación de Spring tendrá sus propias necesidades y requisitos de configuración, por lo que se pueden agregar otras opciones personalizadas en función de las necesidades específicas de la aplicación.

## Datasource ## 

En las aplicaciones de Spring que utilizan una base de datos, es muy común configurar el DataSource (origen de datos) mediante el archivo application.properties. Algunas de las opciones de configuración más comunes para DataSource son:

spring.datasource.url: especifica la URL de la base de datos. Por ejemplo: spring.datasource.url=jdbc:mysql://localhost:3306/mydb

spring.datasource.username: especifica el nombre de usuario para la conexión a la base de datos. Por ejemplo: spring.datasource.username=myuser

spring.datasource.password: especifica la contraseña para la conexión a la base de datos. Por ejemplo: spring.datasource.password=mypassword

spring.datasource.driver-class-name: especifica el nombre de la clase del controlador JDBC que se utilizará para la conexión a la base de datos. Por ejemplo: spring.datasource.driver-class-name=com.mysql.jdbc.Driver

spring.datasource.validation-query: especifica la consulta SQL de validación que se utilizará para comprobar si la conexión con la base de datos está activa. Por ejemplo: spring.datasource.validation-query=SELECT 1

Además de estas opciones, hay muchas otras opciones que se pueden configurar para DataSource en application.properties, como la cantidad máxima de conexiones, la cantidad máxima de conexiones inactivas, el tiempo de espera máximo para una conexión, entre otras opciones.

Es importante tener en cuenta que las opciones de configuración pueden variar según la base de datos que se esté utilizando. Por ejemplo, en el caso de MySQL se utilizará la propiedad jdbc:mysql en spring.datasource.url, mientras que en el caso de PostgreSQL se utilizará jdbc:postgresql. Por lo tanto, es importante consultar la documentación correspondiente para configurar adecuadamente el DataSource.

