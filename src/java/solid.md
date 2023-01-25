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

[Liskov Substitution] (https://howtodoinjava.com/best-practices/solid-principles/#LSP, https://www.baeldung.com/java-liskov-substitution-principle)

[Interface Segregation] (https://howtodoinjava.com/best-practices/solid-principles/#ISP, https://www.baeldung.com/java-interface-segregation, https://www.javaguides.net/2018/02/interface-segregation-principle.html)

[Dependency Inversion] (https://howtodoinjava.com/spring-core/spring-ioc-vs-di/, https://www.baeldung.com/java-dependency-inversion-principle, https://javatechonline.com/solid-principles-the-dependency-inversion-principle/)
