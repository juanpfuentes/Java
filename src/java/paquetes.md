# Java Programación orientada a objetos #

## Paquetes ##

La organización de paquetes en Java es una característica de la plataforma Java que permite agrupar clases relacionadas en un mismo paquete. Esto ayuda a mantener el código organizado y fácil de entender, y también a prevenir conflictos de nombres entre clases.

Para crear un paquete en Java, se utiliza la palabra clave "package" seguida del nombre del paquete al principio de un archivo de código fuente. Por ejemplo:

```
package com.mycompany.myproject;

public class MyClass {
    // código de la clase
}
```

El nombre del paquete se compone de una serie de nombres de paquetes separados por puntos. El primer nombre es el nombre de dominio inverso de la organización que crea el paquete, seguido por los nombres de los proyectos y subproyectos. Esto ayuda a asegurar que los nombres de los paquetes son únicos en todo el sistema.

Una vez que se ha creado un paquete, las clases dentro de ese paquete pueden acceder entre sí utilizando la visibilidad "default" (sin especificar ninguna palabra clave). Sin embargo, las clases en otros paquetes sólo pueden acceder a las clases en ese paquete si se especifica la visibilidad "public" en las clases o métodos.

Además de organizar el código, la organización de paquetes también facilita la distribución y el uso de bibliotecas de clases compartidas. Los paquetes pueden empaquetarse en archivos JAR (Java Archive) y distribuidos para su uso en otros proyectos.

En resumen, la organización de paquetes es una característica importante de Java que permite agrupar clases relacionadas, mantener el código organizado, prevenir conflictos de nombres y distribuir bibliotecas de clases de manera eficiente.

https://www.tutorialspoint.com/java/java_packages.htm

https://www.javatpoint.com/package

https://www.w3schools.com/java/java_packages.asp