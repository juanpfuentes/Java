# Java Programación orientada a objetos #

## Clases ##

### Introducción ###

En Java, una clase es una plantilla o molde para crear objetos. Un objeto es una instancia de una clase y tiene su propio estado y comportamiento. Cada objeto de una clase tiene su propia copia de los datos miembros (variables) y comparte una copia de los métodos (funciones) de la clase.

Una clase se define mediante la palabra clave "class" seguida del nombre de la clase. Dentro de la clase se definen los datos miembros (variables de instancia) y los métodos (funciones). Por ejemplo, la clase "Auto" podría tener una variable de instancia "color" y un método "encenderMotor()".

```
class Auto {
    String color;
    void encenderMotor(){
        //código para encender el motor
    }
}
```

Para crear un objeto de una clase, se utiliza la palabra clave "new" seguida del nombre de la clase y los paréntesis. Por ejemplo, para crear un objeto de la clase "Auto" se puede usar el siguiente código:

```
Auto miAuto = new Auto();
```

Una vez que se ha creado un objeto, se puede acceder a sus variables de instancia y métodos mediante el operador punto (.). Por ejemplo, para cambiar el color de un objeto "miAuto" se puede usar el siguiente código:

```
miAuto.color = "rojo";
```

Java también proporciona una serie de modificadores de acceso como "public", "private" y "protected" para controlar el acceso a las variables de instancia y métodos de una clase. Los miembros de clase declarados como "public" son accesibles desde cualquier parte del código, mientras que los miembros declarados como "private" solo son accesibles desde dentro de la misma clase.

En resumen, las clases en Java son el mecanismo mediante el cual se pueden crear objetos con estado y comportamiento específicos, y son fundamentales para la programación orientada a objetos.

https://www.javatpoint.com/java-oops-concepts

https://www.w3schools.com/java/java_oop.asp)

### Clases y objetos ###

En Java, una clase es un molde o plantilla para crear objetos, mientras que un objeto es una instancia de una clase con su propio estado y comportamiento.

Para entender mejor la diferencia, aquí hay algunos ejemplos:

    Una clase "Auto" podría tener variables de instancia como "color", "marca" y "modelo", así como métodos como "encenderMotor()" y "apagarMotor()". Esta clase es como un plano o un molde para construir un automóvil.

    Un objeto "miAuto" es una instancia específica de la clase "Auto" con un color, marca y modelo específicos. Por ejemplo, "miAuto" podría ser un automóvil rojo de la marca Toyota con el modelo Corolla.

    Otra instancia de la clase "Auto" podría ser "tuAuto" con un color, marca y modelo diferente. Por ejemplo, "tuAuto" podría ser un automóvil azul de la marca Ford con el modelo Mustang.

    Una clase "Persona" podría tener variables de instancia como "nombre", "edad" y "direccion" y métodos como "caminar()" y "hablar()". Esta clase es como un plano o un molde para construir una persona.

    Un objeto "Juan" es una instancia específica de la clase "Persona" con un nombre, edad y direccion específicos. Por ejemplo, "Juan" podría ser una persona con nombre Juan, edad 30 y direccion "Calle 123".

    Otra instancia de la clase "Persona" podría ser "Maria" con un nombre, edad y direccion diferente. Por ejemplo, "Maria" podría ser una persona con nombre Maria, edad 25 y direccion "Calle 456".

En resumen, una clase es un molde o plantilla para crear objetos, mientras que un objeto es una instancia específica de esa clase con su propio estado y comportamiento. Cada objeto de una clase tiene su propia copia de las variables de instancia y comparte una copia de los métodos de la clase.


 https://www.tutorialspoint.com/java/java_object_classes.htm
 
 https://www.javatpoint.com/object-and-class-in-java
 
 https://www.w3schools.com/java/java_classes.asp

### Métodos ###

En Java, los métodos son funciones que se definen dentro de una clase. Un método tiene un nombre, un tipo de retorno y puede tener parámetros de entrada. Para crear un método dentro de una clase, se utiliza la sintaxis:

```
<tipoDeRetorno> nombreDelMetodo(<parametros>) {
    // cuerpo del método
}
```

Ejemplo:

```
class MiClase {
    // atributos de la clase

    int sumar(int a, int b) {
        return a + b;
    }
}
```

Existen diferentes tipos de métodos en Java, entre ellos:

    Métodos de instancia: son aquellos que se pueden llamar sobre un objeto de una clase.
    Métodos estáticos: son aquellos que se pueden llamar sobre la clase en sí, sin necesidad de tener un objeto de la clase.
    Métodos constructores: son aquellos que se utilizan para inicializar un objeto de una clase.
    Métodos abstractos: son aquellos que no tienen implementación, se deben sobreescribir en clases hijas.

Ejemplo de método estático:

```
class MiClase {
    static int sumar(int a, int b) {
        return a + b;
    }
}
```

Ejemplo de método constructor:

```
class MiClase {
    int numero;

    MiClase(int numero) {
        this.numero = numero;
    }
}
```

https://www.javatpoint.com/method-in-java

https://www.w3schools.com/java/java_class_methods.asp

### Constructores ###

En Java, los constructores son métodos especiales que se utilizan para inicializar un objeto de una clase al momento de su creación. Un constructor tiene el mismo nombre que la clase y no tiene un tipo de retorno.

Para crear un constructor en una clase, se utiliza la sintaxis:

<nombreDeLaClase>(<parametros>) {
    // cuerpo del constructor
}

Ejemplo:

```
class MiClase {
    int numero;

    MiClase(int numero) {
        this.numero = numero;
    }
}
```

Existen diferentes tipos de constructores en Java:

Constructores sin parámetros: son aquellos que no tienen parámetros de entrada. Es recomendable tener un constructor sin parámetros en caso de que no se necesite inicializar ningún atributo al momento de crear el objeto.

```
class MiClase {
    int numero;

    MiClase() {
    }
}
```

Constructores con parámetros: son aquellos que tienen parámetros de entrada y se utilizan para inicializar los atributos del objeto al momento de su creación.

```
class MiClase {
    int numero;

    MiClase(int numero) {
        this.numero = numero;
    }
}
```

Constructores copia: son aquellos que se utilizan para crear una copia de un objeto existente, se suelen utilizar como una forma de defensa contra la modificación de un objeto original.

```
class MiClase {
    int numero;
    MiClase(MiClase original) {
        this.numero = original.numero;
    }
}
```

Es importante tener en cuenta que si no se define ningún constructor en una clase, Java creará automáticamente un constructor sin parámetros.


https://www.javatpoint.com/java-constructor

https://www.w3schools.com/java/java_constructors.asp

### Sobrecarga de constructores ###

La sobrecarga de constructores en Java es una técnica que permite tener varios constructores con diferentes parámetros en una misma clase. Cada constructor tiene una firma diferente, es decir, un conjunto diferente de parámetros.

La sobrecarga de constructores se utiliza para proporcionar diferentes formas de crear una instancia de una clase. Por ejemplo, podrías tener un constructor que no requiere parámetros y otro constructor que requiere varios parámetros. Cada vez que se crea una instancia de una clase, se utiliza el constructor apropiado en función de los parámetros proporcionados.

Un ejemplo de sobrecarga de constructores en una clase "Persona" sería el siguiente:

```
class Persona {
    private String nombre;
    private int edad;

    // Constructor sin parámetros
    public Persona() {
        this.nombre = "";
        this.edad = 0;
    }

    // Constructor con parámetros
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }
}
```

En este ejemplo, la clase Persona tiene dos constructores: uno sin parámetros y otro con dos parámetros (nombre y edad).
Al crear una instancia de la clase Persona, se puede utilizar cualquiera de los dos constructores de acuerdo a lo que se necesite:

```
// Creando una persona sin especificar nombre ni edad
Persona p1 = new Persona();

// Creando una persona especificando nombre y edad
Persona p2 = new Persona("Juan", 25);
```

La sobrecarga de constructores es una práctica común en Java ya que permite crear objetos de una clase de diferentes formas, y puede ser muy útil para la creación de objetos con diferentes características y comportamientos.

Un ejemplo de utilizar la sobrecarga de constructores en Java para llamar a otro constructor dentro de una clase sería el siguiente:

```
class Persona {
    private String nombre;
    private int edad;
    private String direccion;

    // Constructor sin parámetros
    public Persona() {
        this("", 0, "");
    }

    // Constructor con dos parámetros
    public Persona(String nombre, int edad) {
        this(nombre, edad, "");
    }

    // Constructor con tres parámetros
    public Persona(String nombre, int edad, String direccion) {
        this.nombre = nombre;
        this.edad = edad;
        this.direccion = direccion;
    }
}
```

En este ejemplo, la clase Persona tiene tres constructores: uno sin parámetros, otro con dos parámetros (nombre y edad) y otro con tres parámetros (nombre, edad y dirección).
El constructor sin parámetros llama al constructor con tres parámetros pasando valores vacíos, en cambio el constructor con dos parámetros llama al constructor con tres parámetros pasando valores vacios en el campo direccion.

Al crear una instancia de la clase Persona, se puede utilizar cualquiera de los tres constructores de acuerdo a lo que se necesite:

Copy code
// Creando una persona sin especificar nombre ni edad ni direccion
Persona p1 = new Persona();

// Creando una persona especificando nombre y edad
Persona p2 = new Persona("Juan", 25);

// Creando una persona especificando nombre, edad y direccion
Persona p3 = new Persona("Juan", 25, "Calle 123");
De esta manera, se puede reutilizar el código del constructor con tres parámetros y evitar escribir código repetitivo en los constructores con menos parámetros.
Es una buena práctica utilizar la sobrecarga de constructores para llamar a otros constructores dentro de la misma clase, ya que permite una mejor organización y mantenimiento del código.

### this ###

En Java, la palabra "this" hace referencia al objeto actual de una clase en el que se está ejecutando un método o un constructor. Se utiliza para acceder a los atributos y métodos de la clase desde dentro de un método o constructor.

Por ejemplo, si se tiene un atributo "numero" y un parámetro "numero" en un constructor, se puede usar "this.numero" para acceder al atributo y "numero" para acceder al parámetro:

```
class MiClase {
    int numero;

    MiClase(int numero) {
        this.numero = numero;
    }
}
```

También se puede utilizar "this" para llamar a otros métodos de la clase desde dentro de un método o constructor. Por ejemplo:

```
class MiClase {
    int numero;

    MiClase(int numero) {
        this.numero = numero;
    }
    void setNumero(int numero) {
        this.numero = numero;
    }
}
```

En resumen, la palabra "this" se utiliza para referirse al objeto actual de una clase y para acceder a sus atributos y métodos desde dentro de un método o constructor. Se utiliza para diferenciar entre variables miembro de la clase y variables locales de un método o constructor.

https://www.javatpoint.com/this-keyword

### Modificadores ###

En Java, existen varios modificadores de acceso que se utilizan para controlar el acceso a los atributos y métodos de una clase. Los modificadores de acceso son palabras clave que se colocan antes de la definición de un atributo o método para especificar quién puede acceder a ese atributo o método. Los modificadores de acceso más comunes en Java son:

public: los elementos marcados como públicos pueden ser accedidos desde cualquier parte del código, tanto dentro como fuera de la clase.

```
public class MiClase {
    public int numero;
    public void setNumero(int numero) {
        this.numero = numero;
    }
}
```

private: los elementos marcados como privados solo pueden ser accedidos desde dentro de la clase en la que se definen.

```
class MiClase {
    private int numero;
    void setNumero(int numero) {
        this.numero = numero;
    }
}
```

protected: los elementos marcados como protegidos pueden ser accedidos desde la clase en la que se definen y desde cualquier clase que herede de ella.

```
class MiClase {
    protected int numero;
}
class MiClaseHija extends MiClase {
    void setNumero(int numero) {
        this.numero = numero;
    }
}
```

default: los elementos marcados como default pueden ser accedidos solo dentro del paquete en el que se encuentran. Es decir, son accesibles desde cualquier clase dentro del mismo paquete pero no desde otro paquete diferente.

Es importante tener en cuenta que si no se especifica ningún modificador de acceso, se asume que es default.

En resumen, los modificadores de acceso en Java son palabras clave que se utilizan para controlar el acceso a los atributos y métodos de una clase. Los modificadores de acceso más comunes son public, private, protected y default. Cada uno de ellos tiene un alcance de acceso diferente y se utilizan según las necesidades del diseño de la clase.

https://www.w3schools.com/java/java_modifiers.asp

https://www.javatpoint.com/access-modifiers

### Getters y setters ###

Los getters y los setters son métodos utilizados para obtener (get) y establecer (set) el valor de una propiedad o atributo de una clase en Java. Los getters devuelven el valor de la propiedad, mientras que los setters establecen un nuevo valor para la propiedad. Los getters y los setters se utilizan para proteger los atributos de una clase de posibles accesos no autorizados y modificaciones no deseadas.

Un ejemplo de una clase con un getter y un setter para un atributo "nombre" sería el siguiente:

```
class Persona {
    private String nombre;

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
}
```

En este ejemplo, el atributo "nombre" es privado y solo se puede acceder a él a través de los métodos públicos "getNombre" y "setNombre".
Por ejemplo, si quieres obtener el nombre de una persona, primero debes crear una instancia de la clase Persona y luego llamar el metodo getNombre()

```
Persona p1 = new Persona();
p1.setNombre("Juan");
String nombre = p1.getNombre();
```


De esta manera, aseguramos que no se pueda modificar el atributo de una manera no deseada.


### Ejercicios ###

Aquí te doy algunos ejemplos sencillos de ejercicios que puedes hacer para practicar trabajando con clases en Java:

Crea una clase llamada "CuentaBancaria" con los atributos "titular" (String) y "saldo" (double). Agrega un constructor que inicialice los valores de los atributos y un método llamado "depositar" que aumente el saldo en una cantidad específica.

Crea una clase llamada "Persona" con los atributos "nombre" (String), "edad" (int) y "genero" (String). Agrega un constructor que inicialice los valores de los atributos y un método llamado "presentarse" que imprima los valores de los atributos en consola.

Crea una clase llamada "Libro" con los atributos "titulo" (String), "autor" (String) y "numeroDePaginas" (int). Agrega un constructor que inicialice los valores de los atributos y un método llamado "infoLibro" que imprima los valores de los atributos en consola.

Crea una clase llamada "Automovil" con los atributos "marca" (String), "modelo" (String), "anno" (int) y "kilometraje" (double). Agrega un constructor que inicialice los valores de los atributos y un método llamado "mostrarInformacion" que imprima los valores de los atributos en consola.

Crea una clase llamada "Rectangulo" con los atributos "base" (double) y "altura" (double). Agrega un constructor que inicialice los valores de los atributos y un método llamado "calcularArea" que calcule y devuelva el área del rectángulo.

Espero que estos ejercicios te ayuden a practicar y a entender mejor cómo trabajar con clases en Java. Recuerda que la práctica es clave para mejorar tus habilidades en programación.