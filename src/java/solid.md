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

https://www.geeksforgeeks.org/single-responsibility-principle-in-java-with-examples/

https://howtodoinjava.com/design-patterns/single-responsibility-principle/

[OPen/Close] (https://howtodoinjava.com/best-practices/open-closed-principle/, https://www.geeksforgeeks.org/open-closed-principle-in-java-with-examples/?ref=rp)

[Liskov Substitution] (https://howtodoinjava.com/best-practices/solid-principles/#LSP, https://www.baeldung.com/java-liskov-substitution-principle)

[Interface Segregation] (https://howtodoinjava.com/best-practices/solid-principles/#ISP, https://www.baeldung.com/java-interface-segregation, https://www.javaguides.net/2018/02/interface-segregation-principle.html)

[Dependency Inversion] (https://howtodoinjava.com/spring-core/spring-ioc-vs-di/, https://www.baeldung.com/java-dependency-inversion-principle, https://javatechonline.com/solid-principles-the-dependency-inversion-principle/)
