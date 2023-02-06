# Java Maven #

## Introducción ##

Maven es una herramienta de gestión de proyectos para Java que se utiliza para automatizar tareas comunes de compilación, pruebas, empaquetado y despliegue. Es similar a otras herramientas como Gradle y Ant, pero tiene un enfoque en la convención sobre la configuración.

Puede crear un nuevo proyecto Maven en Eclipse seleccionando "File->New->Other->Maven Project".

Una vez creado el proyecto, puede agregar dependencias al archivo pom.xml del proyecto. Esto es especialmente útil para agregar bibliotecas de terceros a su proyecto.

Maven también proporciona una serie de comandos como "mvn compile" para compilar el proyecto, "mvn test" para ejecutar pruebas, "mvn package" para empaquetar el proyecto y "mvn deploy" para desplegar el proyecto en un servidor. Estos comandos pueden ser ejecutados en la línea de comandos o en Eclipse mediante el uso de la consola de Maven.

https://www.genbeta.com/desarrollo/que-es-maven

https://www.javiergarzas.com/2014/06/maven-en-10-min.html

## Eclipse y Maven ##

Para crear un proyecto Maven con Eclipse, debes seguir los siguientes pasos:

Abrir Eclipse y hacer clic en "File" -> "New" -> "Project".
Seleccionar "Maven Project" en la lista de proyectos disponibles y hacer clic en "Next".
Seleccionar la opción "Create a simple project (skip archetype selection)" y hacer clic en "Next".
Ingresar los detalles del proyecto, como el nombre del proyecto, el grupo ID y la versión.
Hacer clic en "Finish".
Una vez creado el proyecto Maven, puedes agregar dependencias a través del archivo pom.xml. Puedes hacer esto haciendo clic derecho en el proyecto -> "Maven" -> "Add Dependency" y buscando la dependencia que necesitas.

Maven automatiza el proceso de descargar y gestionar las dependencias de un proyecto, lo que significa que puedes centrarte en escribir el código de tu aplicación sin preocuparte por la gestión de las dependencias.

## Arquetipos ##

Un arquetipo es una plantilla predefinida que proporciona una estructura y un conjunto de archivos básicos para un proyecto en particular. Por ejemplo, si deseas crear un proyecto web Java con Spring Boot, puedes seleccionar el arquetipo spring-boot-starter-web. De esta manera, Maven creará una estructura de proyecto que incluye todas las dependencias necesarias para crear una aplicación web con Spring Boot.

Una vez creado el proyecto, puedes agregar dependencias a través del archivo pom.xml y escribir el código en el proyecto según tus necesidades.

## Dependencias en Maven ##

Para agregar una dependencia en Maven, debes editar el archivo pom.xml de tu proyecto y agregar la dependencia dentro de la etiqueta "dependencies". La sintaxis para agregar una dependencia es la siguiente:

```
<dependency>
  <groupId>nombre del grupo</groupId>
  <artifactId>nombre del artefacto</artifactId>
  <version>versión</version>
</dependency>
```

Por ejemplo, si quieres agregar la dependencia de Hibernate en tu proyecto, debes agregar la siguiente línea dentro de la etiqueta "dependencies":

```
<dependency>
  <groupId>org.hibernate</groupId>
  <artifactId>hibernate-core</artifactId>
  <version>5.4.21.Final</version>
</dependency>
```

También puedes buscar las dependencias en el repositorio central de Maven (https://mvnrepository.com/) y copiar y pegar las dependencias necesarias en tu archivo pom.xml.

Una vez que hayas agregado las dependencias, debes actualizar tu proyecto en Eclipse para que Maven descargue e instale las dependencias. Puedes hacer esto seleccionando el proyecto en el explorador de proyectos y eligiendo "Maven" -> "Update Project" o simplemente presionando "Alt+F5".


Repositorios de dependencias:

https://search.maven.org

https://mvnrepository.com/

## POM ##

El archivo pom.xml es el archivo principal de configuración de Maven. Es utilizado para especificar las dependencias del proyecto, configurar plugins y definir metadatos sobre el proyecto, como su nombre, descripción y organización.

Por ejemplo, para agregar una dependencia a un proyecto de Maven, se debe agregar una etiqueta dependency dentro del elemento dependencies del archivo pom.xml, con la información de la dependencia, como el nombre del grupo, el nombre del artefacto y la versión.

```
<dependencies>
  <dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.6</version>
  </dependency>
</dependencies>
```

También es posible especificar plugins en el archivo pom.xml, por ejemplo para compilar el proyecto, ejecutar pruebas unitarias, generar documentación, etc.

```
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.0</version>
      <configuration>
        <source>1.8</source>
        <target>1.8</target>
      </configuration>
    </plugin>
  </plugins>
</build>
```

En resumen, el archivo pom.xml es el lugar donde se especifican las configuraciones y dependencias de un proyecto de Maven, lo que permite automatizar tareas y facilitar la gestión de dependencias y configuraciones del proyecto.

https://maven.apache.org/guides/introduction/introduction-to-the-pom.html

## Ejemplos ##

Creación de una página web con Maven:

https://www.javaguides.net/2018/11/how-to-create-simple-maven-project-in.html

https://crunchify.com/how-to-create-dynamic-web-project-using-maven-in-eclipse/

https://medium.com/geekculture/build-a-spring-boot-rest-api-with-java-maven-and-mysql-92bdb654caa9

http://javainsimpleway.com/hibernate-setup-in-eclipse-with-maven-and-mysql-db/