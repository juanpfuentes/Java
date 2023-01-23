# OOP Composición y herencia #

## Herencia ##

[Herencia]

La herencia en Java permite que una clase herede las propiedades y métodos de otra clase. Esto significa que una clase hija puede heredar todas las variables y métodos de una clase padre, así como agregar sus propias variables y métodos.

Por ejemplo, supongamos que tenemos una clase Animal:

```
class Animal {
    int numLegs;
    String name;

    void makeNoise() {
        System.out.println("Some noise");
    }
}
```

Ahora, queremos crear una clase Dog que herede de Animal:

```
class Dog extends Animal {
    void bark() {
        System.out.println("Woof");
    }
}
```

En esta clase Dog, podemos acceder a las variables numLegs y name de la clase padre Animal, así como a su método makeNoise(). Además, la clase Dog tiene su propio método bark().

Para utilizar esta clase Dog, podemos crear una instancia de la misma:

```
Dog myDog = new Dog();
myDog.numLegs = 4;
myDog.name = "Fido";
myDog.makeNoise(); // imprime "Some noise"
myDog.bark(); // imprime "Woof"
```

En resumen, la herencia en Java permite que una clase herede las propiedades y métodos de otra clase, lo cual nos permite crear clases que comparten ciertas características y comportamientos comunes.

https://www.tutorialspoint.com/java/java_inheritance.htm

https://www.javatpoint.com/inheritance-in-java

https://www.w3schools.com/java/java_inheritance.asp

[Polimorfismo] 

El polimorfismo en Java es la capacidad de un objeto de una clase derivada para ser tratado como un objeto de una clase base. Esto significa que una variable de una clase base puede almacenar una referencia a un objeto de una clase derivada.

Por ejemplo, supongamos que tenemos una clase base llamada Shape y dos clases derivadas llamadas Circle y Rectangle:

```
class Shape {
    void draw() {
        System.out.println("Drawing a shape");
    }
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing a circle");
    }
}

class Rectangle extends Shape {
    void draw() {
        System.out.println("Drawing a rectangle");
    }
}
```

Ahora, podemos crear una variable de tipo Shape y asignarle una referencia a un objeto de la clase Circle o Rectangle:

```
Shape s1 = new Circle();
s1.draw(); // imprime "Drawing a circle"

Shape s2 = new Rectangle();
s2.draw(); // imprime "Drawing a rectangle"
```

En este ejemplo, la variable s1 es de tipo Shape, pero almacena una referencia a un objeto de la clase Circle. Al llamar al método draw() en s1, se ejecuta el método sobreescrito de la clase Circle. Lo mismo ocurre con la variable s2 de tipo Shape pero almacena una referencia a un objeto de la clase Rectangle.

En resumen, el polimorfismo en Java permite tratar un objeto de una clase derivada como si fuera un objeto de una clase base, lo cual nos permite crear métodos y estructuras de datos más genéricas y reutilizables.

https://www.tutorialspoint.com/java/java_polymorphism.htm

https://www.javatpoint.com/method-overloading-in-java

https://www.w3schools.com/java/java_polymorphism.asp

### Sobrecarga ###

En Java, el overriding se refiere a la capacidad de una subclase para redefinir (sobrescribir) un método de su superclase. Esto significa que una subclase puede proporcionar una implementación diferente de un método que ya existe en su superclase. El objetivo principal de esto es permitir a las subclases personalizar el comportamiento heredado.

Para sobrescribir un método, la subclase debe tener la misma firma (nombre del método, tipo de retorno y argumentos) que el método de la superclase. Además, la anotación @Override debe utilizarse para indicar que el método está siendo sobrescrito.

Aquí hay un ejemplo de cómo se usa el overriding en Java:

```
class Animal {
    public void move() {
        System.out.println("Los animales se mueven de diferentes maneras.");
    }
}

class Dog extends Animal {
    @Override
    public void move() {
        System.out.println("Los perros corren y caminan.");
    }
}

class Fish extends Animal {
    @Override
    public void move() {
        System.out.println("Los peces nadan.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        a.move();  // Imprime "Los animales se mueven de diferentes maneras."

        Animal d = new Dog();
        d.move();  // Imprime "Los perros corren y caminan."

        Animal f = new Fish();
        f.move();  // Imprime "Los peces nadan."
    }
}
```

En este ejemplo, la clase Animal tiene un método move() que se sobrescribe en las subclases Dog y Fish. Cada subclase proporciona su propia implementación de move() para personalizar el comportamiento heredado.

En Java, se recomienda usar la etiqueta @Override cuando se sobreescribe un método. Esto ayuda a evitar errores como sobreescribir un método que no existe o tiene una firma de método diferente. Además, la etiqueta @Override también ayuda a mejorar la legibilidad del código ya que indica intencionalmente que un método es una sobreescritura. Sin embargo, no es obligatorio usar la etiqueta @Override y el código todavía funcionará correctamente si no se utiliza.

https://www.tutorialspoint.com/java/java_overriding.htm

https://www.javatpoint.com/method-overriding-in-java

### Abstracción ###

En Java, las clases abstractas son clases que no pueden ser instanciadas directamente. En cambio, se utilizan como una plantilla para crear otras clases que heredan de ellas. Una clase abstracta puede contener métodos abstractos, que son métodos que no tienen un cuerpo y deben ser implementados por las clases que heredan de la clase abstracta. Estos métodos son utilizados para definir un comportamiento esperado para las clases hijas.

Por ejemplo, podríamos tener una clase abstracta llamada "Animal" que tiene un método abstracto llamado "makeSound()". Las clases "Dog" y "Cat" podrían heredar de "Animals" y proporcionar implementaciones específicas para el método "makeSound()", como "bark" y "meow" respectivamente.

Para declarar una clase como abstracta se usa la palabra reservada "abstract" en la declaración de la clase. Para declarar un método como abstracto se usa la palabra reservada "abstract" en la declaración del método y no se proporciona cuerpo al método.

Ejemplo:

```
abstract class Animals {
  abstract void makeSound();
}
class Dog extends Animals {
  void makeSound(){
    System.out.println("bark");
  }
}
class Cat extends Animals {
  void makeSound(){
    System.out.println("meow");
  }
}
```

En este ejemplo, la clase "Animals" es una clase abstracta que tiene un método abstracto "makeSound()". Las clases "Dog" y "Cat" heredan de "Animals" y proporcionan implementaciones específicas para el método "makeSound()".

https://www.tutorialspoint.com/java/java_abstraction.htm

https://www.javatpoint.com/abstract-class-in-java

https://www.w3schools.com/java/java_abstract.asp

### Encapsulación ###

La encapsulación es uno de los principios fundamentales de la programación orientada a objetos y se refiere a la idea de ocultar los detalles de implementación de una clase y exponer solo una interfaz pública a través de la cual se puede acceder a los datos y comportamientos de la clase. Esto ayuda a proteger la integridad de los datos y a asegurar que solo se pueden realizar acciones válidas sobre ellos.

En Java, la encapsulación se logra mediante el uso de modificadores de acceso como "private", "protected" y "public". Los miembros de una clase declarados como "private" solo pueden ser accedidos desde dentro de la clase, mientras que los miembros declarados como "public" pueden ser accedidos desde cualquier lugar.

Por ejemplo, podríamos tener una clase "Car" con un miembro de datos privado llamado "engineSize" y un método público llamado "setEngineSize()" que permite cambiar el tamaño del motor. El código siguiente ilustra cómo se podría utilizar esta clase:

```
class Car {
  private int engineSize;

  public void setEngineSize(int size) {
    engineSize = size;
  }
}
```

En este ejemplo, el miembro de datos "engineSize" es privado y solo puede ser accedido desde dentro de la clase "Car". El método "setEngineSize()" es público y permite cambiar el valor de "engineSize" de manera segura y controlada.

Otro ejemplo podría ser una clase "BankAccount" con un miembro de datos privado llamado "balance" y un método público llamado "withdraw()" que permite retirar dinero de la cuenta. El código siguiente ilustra cómo se podría utilizar esta clase:

```
class BankAccount {
  private double balance;

  public void withdraw(double amount) {
    if (amount > 0 && amount <= balance) {
      balance -= amount;
    }
  }
}
```

En este ejemplo, el miembro de datos "balance" es privado y solo puede ser accedido desde dentro de la clase "BankAccount". El método "withdraw()" es público y permite retirar dinero de la cuenta de manera segura y controlada.

https://www.tutorialspoint.com/java/java_encapsulation.htm

https://www.javatpoint.com/encapsulation

https://www.w3schools.com/java/java_encapsulation.asp

### Interfaces ###

En Java, una interfaz es una especificación de un conjunto de métodos que deben ser implementados por una clase. Una interfaz es similar a una clase abstracta, pero no puede contener implementaciones de métodos ni campos. En cambio, define solo la firma de los métodos que deben ser implementados.

Las interfaces son útiles para varios propósitos, como:

    Permitir la implementación de múltiples herencias, ya que una clase puede implementar varias interfaces.
    Proporcionar una forma de especificar el comportamiento esperado de una clase sin proporcionar una implementación específica.
    Permitir que una clase proporcione una interfaz común para diferentes implementaciones.

Para implementar una interfaz en una clase, se utiliza la palabra clave "implements" en la declaración de la clase. Todos los métodos declarados en la interfaz deben ser implementados en la clase. Si una clase no implementa todos los métodos de una interfaz, la clase debe ser declarada como abstracta.

Por ejemplo, podríamos tener una interfaz llamada "Movable" con un método llamado "move()". La clase "Car" y "Person" podrían implementar la interfaz "Movable" y proporcionar implementaciones específicas para el método "move()", como "drive" y "walk" respectivamente.

Ejemplo:

```
interface Movable {
  void move();
}
class Car implements Movable {
  void move(){
    System.out.println("drive");
  }
}
class Person implements Movable {
  void move(){
    System.out.println("walk");
  }
}
```

En este ejemplo, la interfaz "Movable" define un método "move()" que debe ser implementado por las clases "Car" y "Person". ambas clases proporcionan implementaciones específicas para el método "move()", como "drive" y "walk" respectivamente.

Además, una clase puede implementar múltiples interfaces, separando cada una con una coma, como por ejemplo:

```
class Car implements Movable, Electric{
  void move(){
    System.out.println("drive electric");
  }
  void charge(){
    System.out.println("charging");
  }
}
```

En este ejemplo se ve como la clase Car implementa dos interfaces Movable y Electric.


https://www.tutorialspoint.com/java/java_interfaces.htm

https://www.javatpoint.com/interface-in-java

https://www.w3schools.com/java/java_interface.asp


### Ejercicios ###

Aquí tienes algunos ejemplos de herencia en Java:

Crea una clase llamada "Animal" que tenga atributos como "name" y "age", y métodos como "eat()" y "sleep()". Luego crea una clase llamada "Mammals" que herede de la clase "Animals" y tenga un atributo adicional llamado "numOfLegs". Crea también un método "move()" en esta clase.

Crea una clase llamada "Vehicle" que tenga atributos como "numOfWheels" y "maxSpeed", y métodos como "startEngine()" y "stopEngine()". Luego crea una clase llamada "Car" que herede de la clase "Vehicle" y tenga un atributo adicional llamado "numOfDoors". Crea también un método "drive()" en esta clase.

Crea una clase llamada "Shape" que tenga un método abstracto llamado "calculateArea()". Luego crea dos clases llamadas "Circle" y "Rectangle" que hereden de la clase "Shape" y implementen el método "calculateArea()" de manera diferente.

Crea una clase llamada "Person" que tenga atributos como "name" y "age", y un método "introduce()" que imprima una presentación de la persona. Luego crea una clase llamada "Student" que herede de la clase "Person" y tenga un atributo adicional llamado "major". Crea también un método "study()" en esta clase.

Crea una interfaz llamada "Shape" que tenga un método abstracto llamado "calculateArea()". Luego crea dos clases llamadas "Circle" y "Rectangle" que implementen la interfaz "Shape" y definan el método "calculateArea()" de manera diferente.

Crea una interfaz llamada "Movable" que tenga métodos abstractos llamados "move()" y "stop()". Luego crea dos clases llamadas "Car" y "Bicycle" que implementen la interfaz "Movable" y definan los métodos de manera diferente.

Crea una interfaz llamada "Drawable" que tenga un método abstracto llamado "draw()". Luego crea una clase llamada "PaintProgram" que tenga un método que acepte un objeto "Drawable" y lo dibuje en pantalla. Crea varias clases que implementen la interfaz "Drawable" y prueba el método en cada una.

Crea una interfaz llamada "Playable" que tenga métodos abstractos llamados "play()" y "stop()". Luego crea una clase llamada "MediaPlayer" que tenga un método que acepte un objeto "Playable" y lo reproduzca. Crea varias clases que implementen la interfaz "Playable" (como "Audio" y "Video") y prueba el método en cada una.

Recuerda siempre respetar las buenas prácticas de programación y la encapsulación de los atributos y métodos.