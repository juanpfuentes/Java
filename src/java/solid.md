# Java SOLID #

## Principios SOLID ##

### Introducción ###

SOLID es un acrónimo para los principios de diseño de software de alta calidad desarrollado por Robert C. Martin. Estos principios son una guía para desarrollar software mantenible y escalable. Los principios SOLID son:

**Single Responsibility Principle (Principio de Responsabilidad Única)**: Una clase debe tener una y solo una razón para cambiar. Esto significa que una clase debe tener una responsabilidad específica y no debería tener varias responsabilidades.

**Open-Closed Principle (Principio Abierto-Cerrado)**: Una clase debe estar abierta para extensión y cerrada para modificación. Esto significa que una clase debe estar diseñada de tal manera que se pueda extender su funcionalidad mediante herencia o implementación de interfaces, sin tener que modificar su código existente.

**Liskov Substitution Principle (Principio de Sustitución de Liskov)**: Un objeto de una subclase debe poder reemplazar a un objeto de su superclase. Esto significa que las subclases deben ser intercambiables con sus superclases sin afectar el correcto funcionamiento del software.

**Interface Segregation Principle (Principio de Segregación de Interfaces)**: Un cliente no debe ser obligado a implementar interfaces que no utiliza. Esto significa que deben crearse interfaces específicas para cada cliente en lugar de crear interfaces generales con muchos métodos que no son necesarios para todos los clientes.

**Dependency Inversion Principle (Principio de Inversión de Dependencias)**: Los módulos de alto nivel no deben depender de módulos de bajo nivel, ambos deben depender de abstracciones. Esto significa que el código debe estar diseñado de tal manera que los componentes de alto nivel no dependan directamente de componentes de bajo nivel, sino que ambos dependan de abstraccione

https://www.enmilocalfunciona.io/principios-solid/

https://www.baeldung.com/solid-principles

### Single responsibility ###

El principio de Responsabilidad Única (Single Responsibility Principle - SRP) es uno de los principios SOLID y se refiere a que una clase debe tener una y solo una razón para cambiar. Esto significa que una clase debe tener una responsabilidad específica y no debería tener varias responsabilidades.

Por ejemplo:

1.    Una clase BankAccount que se encarga de llevar el control de las operaciones bancarias (depósitos, retiros, transferencias) y también maneja la impresión de los estados de cuenta. Es mejor dividir esta clase en dos clases distintas: BankAccount y BankAccountPrinter para que cada una tenga una única responsabilidad.
2.    Una clase Car que se encarga de la lógica de conducción y también maneja la lógica de diseño del automóvil. Es mejor dividir esta clase en dos clases distintas: Car y CarDesign para que cada una tenga una única responsabilidad.
3.    Una clase Employee que se encarga de manejar el registro de empleados y también maneja el cálculo de salarios. Es mejor dividir esta clase en dos clases distintas: Employee y SalaryCalculator para que cada una tenga una única responsabilidad.

En resumen, al aplicar el principio de Responsabilidad Única, se logra que las clases sean más fáciles de entender, de probar y de mantener, ya que su responsabilidad esta claramente definida y es menos probable que un cambio en una parte del sistema afecte otras partes del mismo.

Aquí te dejo un ejemplo de código en Java que ilustra el principio de Responsabilidad Única:

```
class BankAccount {
    private double balance;
  
    public void deposit(double amount) {
        balance += amount;
    }
  
    public void withdraw(double amount) {
        balance -= amount;
    }
  
    public double getBalance() {
        return balance;
    }
  
    // viola el principio SRP, una clase debería tener solo una razón para cambiar
    public void printStatement() {
        // lógica de impresión del estado de cuenta
    }
}
```

En este ejemplo, la clase BankAccount tiene varias responsabilidades: manejar las operaciones bancarias (depósitos, retiros) y manejar la impresión del estado de cuenta. Esto viola el principio de Responsabilidad Única, ya que si hay un cambio en la lógica de impresión del estado de cuenta, tendría que modificar la clase BankAccount, aun si no tiene nada que ver con las operaciones bancarias.

Una forma de solucionar esto es dividir la clase en dos:

```
class BankAccount {
    private double balance;
  
    public void deposit(double amount) {
        balance += amount;
    }
  
    public void withdraw(double amount) {
        balance -= amount;
    }
  
    public double getBalance() {
        return balance;
    }
}

class BankAccountPrinter {
    public void printStatement(BankAccount account) {
        // lógica de impresión del estado de cuenta
    }
}
```

De esta forma, cada clase tiene una responsabilidad específica y es menos probable que un cambio en una parte del sistema afecte otras partes del mismo.

https://www.geeksforgeeks.org/single-responsibility-principle-in-java-with-examples/

https://howtodoinjava.com/design-patterns/single-responsibility-principle/

### OPen/Close ###

El principio Open/Closed (Abierto/Cerrado) es otro de los principios SOLID y se refiere a que una clase o módulo debe estar diseñado de tal manera que esté abierto para extensión, pero cerrado para modificación. Esto significa que se deben permitir cambios en la funcionalidad de una clase o módulo sin tener que modificar su código existente.

Algunos ejemplos de cómo aplicar este principio en Java son:

1.    Utilizando herencia: se puede crear una clase base Shape con un método draw() y crear subclases como Circle, Square, Rectangle, etc. que heredan de Shape y sobreescriben el método draw() con la lógica específica para cada forma. De esta manera, se pueden agregar nuevas formas sin tener que modificar la clase Shape.

```
class Shape {
    public void draw() {
        // lógica común para dibujar cualquier forma
    }
}

class Circle extends Shape {
    @override
    public void draw() {
        // lógica específica para dibujar un círculo
    }
}
```

2.    Utilizando interfaces: se puede crear una interfaz Payment con un método processPayment() y crear clases que implementen esta interfaz, como CreditCardPayment, DebitCardPayment, PaypalPayment, etc. De esta manera, se pueden agregar nuevos métodos de pago sin tener que modificar las clases existentes.

```
interface Payment {
    void processPayment();
}

class CreditCardPayment implements Payment {
    @override
    public void processPayment() {
        // lógica específica para procesar un pago con tarjeta de crédito
    }
}
```

 https://howtodoinjava.com/best-practices/open-closed-principle/
 
 https://www.geeksforgeeks.org/open-closed-principle-in-java-with-examples/?ref=rp

### Liskov Substitution ###

El principio de Sustitución de Liskov (LSP, por sus siglas en inglés) es un principio de diseño de programación que se basa en que si una clase es una subclase de otra, entonces debería ser posible utilizar instancias de la subclase en lugar de la superclase sin causar problemas. Es decir, una subclase debe ser capaz de reemplazar completamente a su superclase.

Ejemplos en Java:

1.    Un ejemplo común es el uso de una clase Rectangle y una clase Square. Square es una subclase de Rectangle, por lo que debería ser posible utilizar un objeto Square en lugar de un objeto Rectangle sin causar problemas. Sin embargo, si la clase Square tiene un método setWidth que no establece el valor de la propiedad height, no cumpliría el principio LSP.

2.    Otro ejemplo seria una clase Animal y una clase Gato. Gato es una subclase de Animal, por lo que debería ser posible utilizar un objeto Gato en lugar de un objeto Animal sin causar problemas. Sin embargo, si la clase Gato tiene un método maullar() que no esta en la clase Animal, no cumpliría el principio LSP.

3.    Un último ejemplo es una clase Operación y una clase Suma. Suma es una subclase de Operación, por lo que debería ser posible utilizar un objeto Suma en lugar de un objeto Operación sin causar problemas. Sin embargo, si la clase Suma tiene un método sumar() que no esta en la clase Operación, no cumpliría el principio LSP.

Aquí te dejo un ejemplo en Java que ilustra el uso del principio de Sustitución de Liskov. En este ejemplo se tiene una clase Shape, que es la superclase y dos subclases: Circle y Square.

```
class Shape {
    public void draw() {
        System.out.println("Dibujando forma genérica");
    }
}

class Circle extends Shape {
    public void draw() {
        System.out.println("Dibujando círculo");
    }
}

class Square extends Shape {
    public void draw() {
        System.out.println("Dibujando cuadrado");
    }
}

public class Main {
    public static void drawShape(Shape shape) {
        shape.draw();
    }

    public static void main(String[] args) {
        Shape circle = new Circle();
        Shape square = new Square();
        drawShape(circle); // imprime "Dibujando círculo"
        drawShape(square); // imprime "Dibujando cuadrado"
    }
}
```

En este ejemplo, se tiene un método drawShape() que toma como parámetro una instancia de la clase Shape. Dentro de este método, se llama al método draw() de la instancia de Shape. Sin embargo, gracias al principio de Sustitución de Liskov, es posible pasar tanto un objeto Circle como un objeto Square a este método sin causar problemas, ya que ambos objetos son instancias de una subclase de Shape y tienen un método draw() que se comporta de forma esperada.

Aquí te dejo un ejemplo en Java que ilustra cómo romper el principio de Sustitución de Liskov. En este ejemplo se tiene una clase Bird, que es la superclase y una subclase: Penguin.

```
class Bird {
    public void fly() {
        System.out.println("Volando");
    }
}

class Penguin extends Bird {
    public void fly() {
        throw new UnsupportedOperationException("Los pingüinos no pueden volar");
    }
}

public class Main {
    public static void makeFly(Bird bird) {
        bird.fly();
    }

    public static void main(String[] args) {
        Bird penguin = new Penguin();
        makeFly(penguin); // lanza UnsupportedOperationException
    }
}
```

En este ejemplo, se tiene un método makeFly() que toma como parámetro una instancia de la clase Bird. Dentro de este método, se llama al método fly() de la instancia de Bird. Sin embargo, al pasar un objeto Penguin a este método, se lanza una excepción, lo que viola el principio de Sustitución de Liskov, ya que no se esperaba que ocurriera esto al pasar una instancia de una subclase de Bird. Esa es la razón que en este caso no se cumple el principio LSP, ya que al utilizar un objeto Penguin en lugar de un objeto Bird ha causado un problema.

https://www.adictosaltrabajo.com/2014/10/24/solid-3/

https://howtodoinjava.com/best-practices/solid-principles/#LSP

https://www.baeldung.com/java-liskov-substitution-principle

### Interface Segregation ###

El principio de Segregación de Interfaces (ISP, por sus siglas en inglés) es un principio de diseño de programación que se basa en que una clase no debería ser obligada a implementar métodos que no utilizará. Es decir, las interfaces deben ser lo más pequeñas y específicas posibles, de manera que una clase solo tenga que implementar los métodos que realmente necesita.

Ejemplos en Java:

1. Un ejemplo común es el uso de una interfaz Document y una clase PDF. La interfaz Document tiene métodos para imprimir, escribir y leer un archivo, pero la clase PDF solo necesita implementar los métodos de escribir y leer. En este caso, se debería crear una interfaz específica para la escritura y lectura de PDFs en lugar de forzar a la clase PDF a implementar métodos innecesarios.

1. Otro ejemplo seria una interfaz Automovil y una clase Electrico. Automovil tiene metodos como encender, apagar y cambiar velocidad, pero la clase Electrico solo necesita implementar los métodos encender y apagar. En este caso, se debería crear una interfaz específica para los automoviles electricos en lugar de forzar a la clase Electrico a implementar métodos innecesarios.

1. Un último ejemplo es una interfaz Servicio y una clase Mensajeria. Servicio tiene métodos para enviar correos, mensajes de texto y realizar llamadas, pero la clase Mensajería solo necesita implementar los métodos para enviar correos y mensajes de texto. En este caso, se debería crear una interfaz específica para servicios de mensajería en lugar de forzar a la clase Mensajería a implementar métodos innecesarios.

Aquí te dejo un ejemplo en Java que ilustra el uso del principio de Segregación de Interfaces. En este ejemplo se tiene una interfaz Shape, que es la interfaz principal y dos interfaces específicas: Drawable y Resizable.

```
interface Shape {
    double getArea();
}

interface Drawable {
    void draw();
}

interface Resizable {
    void resize(double factor);
}

class Circle implements Shape, Drawable {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getArea() {
        return Math.PI * radius * radius;
    }

    public void draw() {
        System.out.println("Dibujando círculo");
    }
}

class Square implements Shape, Drawable, Resizable {
    private double side;

    public Square(double side) {
        this.side = side;
    }

    public double getArea() {
        return side * side;
    }

    public void draw() {
        System.out.println("Dibujando cuadrado");
    }

    public void resize(double factor) {
        side *= factor;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        Shape square = new Square(10);
        System.out.println("Area del círculo: " + circle.getArea());
        System.out.println("Area del cuadrado: " + square.getArea());
        ((Drawable) square).draw();
        ((Resizable) square).resize(0.5);
        System.out.println("Nueva area del cuadrado: " + square.getArea());
    }
}
```

Aquí te dejo un ejemplo en Java que ilustra cómo romper el principio de Segregación de Interfaces. En este ejemplo se tiene una interfaz Shape, que es la interfaz principal y una clase Circle.

```
interface Shape {
    double getArea();
    void draw(); // Método que no todas las formas necesitan implementar
    void resize(double factor); // Método que no todas las formas necesitan implementar
}

class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getArea() {
        return Math.PI * radius * radius;
    }

    public void draw() {
        System.out.println("Dibujando círculo");
    }

    public void resize(double factor) {
        radius *= factor;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        System.out.println("Area del círculo: " + circle.getArea());
        circle.draw(); // El círculo no necesita dibujarse
        circle.resize(0.5); // El círculo no necesita redimensionarse
        System.out.println("Nueva area del círculo: " + circle.getArea());
    }
}
```

En este ejemplo, la interfaz Shape tiene métodos para dibujar y redimensionar una forma, pero no todas las clases necesitan implementarlos.

https://howtodoinjava.com/best-practices/solid-principles/#ISP

https://www.baeldung.com/java-interface-segregation

https://www.javaguides.net/2018/02/interface-segregation-principle.html

### Dependency Inversion ###

El principio de Inversión de Dependencias (DIP, por sus siglas en inglés) es un principio de diseño de programación que se basa en que las clases de alto nivel no deben depender de las clases de bajo nivel, sino que ambas deben depender de una abstracción común. Es decir, en lugar de que una clase dependa directamente de otra clase, ambas deben depender de una interfaz o una clase abstracta que las defina.

Ejemplos en Java:

1. Un ejemplo común es el uso de una clase Motor y una clase Automóvil. En lugar de que la clase Automóvil dependa directamente de la clase Motor, se crea una interfaz Motor y ambas clases dependen de esta interfaz. Esto permite cambiar el motor sin afectar al automóvil y viceversa.

1. Otro ejemplo es el uso de una clase Cliente y una clase Servicio. En lugar de que la clase Servicio dependa directamente de la clase Cliente, se crea una interfaz Cliente y ambas clases dependen de esta interfaz. Esto permite cambiar la implementación de Cliente sin afectar al Servicio y viceversa.

Aquí te dejo un ejemplo en Java que ilustra el uso del principio de Inversión de Dependencias. En este ejemplo se tiene una interfaz Motor, que es la interfaz principal, una clase ElectricMotor que implementa la interfaz Motor, y una clase Automobile que depende de la interfaz Motor.

```
interface Motor {
    void start();
}

class ElectricMotor implements Motor {
    public void start() {
        System.out.println("Iniciando motor eléctrico");
    }
}

class Automobile {
    private Motor motor;
    public Automobile(Motor motor) {
        this.motor = motor;
    }

    public void start() {
        motor.start();
    }
}

public class Main {
    public static void main(String[] args) {
        ElectricMotor electricMotor = new ElectricMotor();
        Automobile automobile = new Automobile(electricMotor);
        automobile.start();
    }
}
```

En este ejemplo, la clase Automobile no depende directamente de ElectricMotor, sino de la interfaz Motor. Esto permite cambiar el tipo de motor utilizado por el automóvil (por ejemplo, un motor de gasolina) sin afectar al código de la clase Automobile.

Aquí te dejo un ejemplo en Java que ilustra cómo romper el principio de Inversión de Dependencias. En este ejemplo se tiene una clase Motor y una clase Automóvil, donde la clase Automóvil depende directamente de la clase Motor.

```
class Motor {
    public void start() {
        System.out.println("Iniciando motor");
    }
}

class Automobile {
    private Motor motor;

    public Automobile() {
        this.motor = new Motor();
    }

    public void start() {
        motor.start();
    }
}

public class Main {
    public static void main(String[] args) {
        Automobile automobile = new Automobile();
        automobile.start();
    }
}
```

En este ejemplo, la clase Automobile depende directamente de la clase Motor. Si se quisiera cambiar el tipo de motor utilizado por el automóvil, se tendría que modificar el código de la clase Automobile, violando así el principio de Inversión de Dependencias. Es recomendable usar una interfaz para abstraer la dependencia y poder cambiar la implementación sin afectar al código de la clase Automobile

https://howtodoinjava.com/spring-core/spring-ioc-vs-di/

https://www.baeldung.com/java-dependency-inversion-principle

https://javatechonline.com/solid-principles-the-dependency-inversion-principle/

### Inversión del control ###

El principio de Inversión del Control (IoC, por sus siglas en inglés) se refiere a la forma en que los objetos obtienen sus dependencias. En lugar de que un objeto cree sus dependencias por sí mismo, las dependencias son pasadas a él. Esto permite un mayor control y flexibilidad en el sistema, ya que las dependencias pueden ser cambiadas o inyectadas en tiempo de ejecución.

Ejemplos en Java:

1. Un ejemplo común es el uso de un contenedor de inyección de dependencias (DI, por sus siglas en inglés) como Spring. En lugar de que las clases creen sus dependencias por sí mismas, las dependencias son pasadas a través de la configuración del contenedor.

1. Otro ejemplo es el uso de una clase abstracta para inyectar dependencias. En lugar de que las clases creen sus dependencias por sí mismas, las dependencias son pasadas a través de la implementación de la clase abstracta.

1. Un último ejemplo es el uso de una interfaz para inyectar dependencias. En lugar de que las clases creen sus dependencias por sí mismas, las dependencias son pasadas a través de la implementación de la interfaz.

Aquí te dejo un ejemplo en Java que ilustra el uso del principio de Inversión del Control. En este ejemplo se tiene una clase Motor, una clase Automóvil, y una clase ControladorMotor.

```
class Motor {
    public void start() {
        System.out.println("Iniciando motor");
    }
}

class Automobile {
    private Motor motor;

    public Automobile(Motor motor) {
        this.motor = motor;
    }

    public void start() {
        motor.start();
    }
}

class ControladorMotor {
    public static void main(String[] args) {
        Motor motor = new Motor();
        Automobile automobile = new Automobile(motor);
        automobile.start();
    }
}
```

En este ejemplo, la clase ControladorMotor es la que se encarga de crear una instancia de Motor y pasarla a la clase Automobile, en lugar de tener la clase Automobile crear la dependencia por si misma. Esto permite tener un mayor control sobre la creación de objetos y las dependencias entre ellos, lo cual facilita la inyección de dependencias en tiempo de ejecución.

https://blog.auriboxtraining.com/java/introduccion-la-ioc/

https://www.oscarblancarteblog.com/2016/12/01/concepto-inversion-of-control/

https://www.tutorialsteacher.com/ioc/inversion-of-control