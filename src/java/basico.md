# Java introducción y conceptos básicos #

## Introducción ##

### Características

https://www.javatpoint.com/features-of-java

https://www.tutorialspoint.com/java/java_overview.htm

### Sintaxis

La sintaxis de Java es similar a la de otros lenguajes de programación como C++ o C#. Algunas características clave incluyen:

    La estructura básica de un programa Java es una clase, que contiene variables y métodos.

    Las variables en Java se declaran con un tipo de datos, seguido del nombre de la variable. Ejemplo: int x;

    Los métodos en Java son similares a las funciones en otros lenguajes. Se declaran con el tipo de retorno, seguido del nombre del método y los parámetros entre paréntesis. Ejemplo: public void miMetodo()

    El cuerpo de un método se escribe entre llaves {}

    Los comentarios en Java son con // para una sola línea o /* */ para varias líneas

    El punto y coma (;) se utiliza para separar instrucciones en una línea.

    La palabra reservada "public" se utiliza para definir un método o variable como público, lo cual significa que puede ser accedido desde cualquier parte del programa.

    La palabra reservada "static" se utiliza para definir un método o variable como estático, lo cual significa que pertenece a la clase en lugar de a una instancia específica de la clase.

Este es un ejemplo básico de un programa Java:

```
public class MiClase {
  public static void main(String[] args) {
    System.out.println("Hola mundo!");
  }
}
```

Este programa imprime "Hola mundo!" en la consola.

 https://www.w3schools.com/java/java_syntax.asp
 
 https://www.tutorialspoint.com/java/java_basic_syntax.htm

## Variables y operadores ##

### Variables

En Java, las variables son contenedores de información que pueden almacenar valores de diferentes tipos. Para declarar una variable en Java, se debe especificar el tipo de datos y el nombre de la variable. Por ejemplo:

```
int edad;
```

En este ejemplo se declara una variable llamada "edad" del tipo entero (int).

Una vez declarada, se puede asignar un valor a la variable utilizando el operador de asignación (=). Por ejemplo:

```
edad = 25;
```

En este ejemplo se asigna el valor 25 a la variable "edad".

También se pueden declarar y asignar un valor a una variable en una sola línea. Por ejemplo:

```
int edad = 25;
```

Java tiene diferentes tipos de variables, los más comunes son:

    int: para números enteros
    double: para números con decimales
    boolean: para valores lógicos (verdadero o falso)
    char: para caracteres
    String: para cadenas de caracteres

Una vez que se ha asignado un valor a una variable, este puede ser utilizado en cualquier parte del programa donde la variable sea visible. Por ejemplo, se puede usar en operaciones matemáticas o para imprimirlo en pantalla.

Además, las variables también pueden ser modificadas, asignando un nuevo valor a la variable. Por ejemplo:

```
edad = 30;
```

En este ejemplo se cambia el valor de la variable "edad" de 25 a 30.

https://www.tutorialspoint.com/java/java_variable_types.htm
https://www.javatpoint.com/java-variables
https://www.w3schools.com/java/java_variables.asp

### Tipos de datos

Los tipos de datos primitivos en Java son:

    byte: Es un tipo de datos numérico con un rango de -128 a 127. Es utilizado para almacenar pequeñas cantidades de datos.
    short: Es un tipo de datos numérico con un rango de -32768 a 32767. Es utilizado para almacenar cantidades de datos medianas.
    int: Es un tipo de datos numérico con un rango de -2147483648 a 2147483647. Es utilizado para almacenar grandes cantidades de datos.
    long: Es un tipo de datos numérico con un rango de -9223372036854775808 a 9223372036854775807. Es utilizado para almacenar valores de gran tamaño.
    float: Es un tipo de datos de punto flotante con precisión simple. Es utilizado para almacenar números con decimales.
    double: Es un tipo de datos de punto flotante con precisión doble. Es utilizado para almacenar números con decimales de mayor precisión.
    char: Es un tipo de datos que almacena un solo carácter. Es utilizado para almacenar un carácter en particular.
    boolean: Es un tipo de datos lógico que solo puede tener dos valores: verdadero o falso

Los tipos de datos de referencia en Java son aquellos que no son primitivos y se refieren a un objeto en memoria. Por ejemplo, una cadena de caracteres (String), una lista (List), una fecha (Date), etc. Los tipos de datos de referencia son utilizados para almacenar conjuntos complejos de datos y para trabajar con objetos en un programa.

https://www.tutorialspoint.com/java/java_basic_datatypes.htm

https://www.javatpoint.com/java-data-types

https://www.w3schools.com/java/java_data_types.asp

### Operadores

Java tiene varios tipos de operadores, que se utilizan para realizar operaciones matemáticas, lógicas y de comparación. Los operadores más comunes son:

    Aritméticos: se utilizan para realizar operaciones matemáticas básicas como suma (+), resta (-), multiplicación (*), división (/), módulo (%), incremento (++) y decremento (--).

    Asignación: se utilizan para asignar valores a variables, como el operador de asignación (=).

    Comparación: se utilizan para comparar valores y determinar si son iguales o diferentes. Los operadores de comparación más comunes son == (igual a), != (no igual a), < (menor que), > (mayor que), <= (menor o igual a), >= (mayor o igual a).

    Lógicos: se utilizan para realizar operaciones lógicas como AND (&&), OR (||), NOT (!)

    Condicionales: se utilizan para realizar operaciones condicionales, como el operador ternario (? :)

    Bit a bit: se utilizan para realizar operaciones a nivel de bit, como AND (&), OR (|), NOT (~), XOR (^), desplazamiento a la izquierda (<<) y desplazamiento a la derecha (>>).

    Instancia de: se utiliza para determinar si un objeto es una instancia de una determinada clase o interface.

    Tipo: se utiliza para determinar el tipo de un objeto en tiempo de ejecución.

Todo estos operadores tienen una prioridad y una asociatividad diferentes, esto puede ser importante en expresiones complejas.
	
https://www.tutorialspoint.com/java/java_basic_operators.htm

https://www.javatpoint.com/operators-in-java

https://www.w3schools.com/java/java_operators.asp

## Estructuras de control ##

### if..else

El if...else es una estructura de control de flujo en Java que permite tomar decisiones en un programa. Funciona de la siguiente manera:

    Se escribe la palabra clave "if" seguida de una expresión booleana en paréntesis. Si la expresión es verdadera, se ejecutan las instrucciones dentro del bloque de código siguiente.

    Si la expresión es falsa, se salta al bloque de código siguiente llamado "else" (si existe) y se ejecutan las instrucciones dentro de él.

Ejemplo:

```
int age = 25;
if (age >= 18) {
    System.out.println("Es mayor de edad");
} else {
    System.out.println("Es menor de edad");
}
```

En este ejemplo, si la variable "age" es mayor o igual a 18, se imprimirá "Es mayor de edad". Si no es así, se imprimirá "Es menor de edad".

También existe una estructura if else anidada donde se pueden hacer varias comparaciones y decisiones.

```
if (condition1) {
    // block of code to be executed if condition1 is true
} else if (condition2) {
    // block of code to be executed if the condition1 is false and condition2 is true
} else {
    // block of code to be executed if the condition1 is false and condition2 is false
}
```

Cabe destacar que el else no es obligatorio, solo se utiliza cuando se quiere tomar una acción en caso de que la condición sea falsa.

https://www.javatpoint.com/java-if-else

https://www.tutorialspoint.com/java/java_decision_making.htm

https://www.w3schools.com/java/java_conditions.asp

### switch

El switch en Java es una estructura de control que permite ejecutar una sección específica de código basada en el valor de una variable. El valor de la variable se compara con varios casos (casos) y se ejecuta el código correspondiente al primer caso que coincide con el valor de la variable. Si ningún caso coincide, se ejecuta el código en la cláusula "default", si es que existe.

Ejemplo:

```
int diaSemana = 3;

switch (diaSemana) {
    case 1:
        System.out.println("Lunes");
        break;
    case 2:
        System.out.println("Martes");
        break;
    case 3:
        System.out.println("Miércoles");
        break;
    case 4:
        System.out.println("Jueves");
        break;
    case 5:
        System.out.println("Viernes");
        break;
    case 6:
        System.out.println("Sábado");
        break;
    case 7:
        System.out.println("Domingo");
        break;
    default:
        System.out.println("Día de la semana no válido");
}
```

En este ejemplo, se declara una variable "diaSemana" con el valor 3. Luego, se utiliza la estructura de control switch para comparar el valor de "diaSemana" con los casos 1-7. Como 3 es igual a "Miércoles", se imprime "Miércoles" en la consola. Si el valor de "diaSemana" fuera 8, se ejecutaría la cláusula "default" y se imprimiría "Día de la semana no válido" en la consola.

El uso del break en cada caso es importante ya que si no se pone, el siguiente case se ejecutaría tambien

```
switch (diaSemana) {
    case 1:
        System.out.println("Lunes");
    case 2:
        System.out.println("Martes");
    case 3:
        System.out.println("Miércoles");
    case 4:
        System.out.println("Jueves");
    case 5:
        System.out.println("Viernes");
    case 6:
        System.out.println("Sábado");
    case 7:
        System.out.println("Domingo");
    default:
        System.out.println("Día de la semana no válido");
}
```

En este caso si diaSemana es 3, imprimiria "Miércoles" "Jueves" "Viernes" "Sábado" "Domingo" "Día de la semana no válido"

https://www.javatpoint.com/java-switch
https://www.w3schools.com/java/java_switch.asp

### while

Sí, el bucle "while" en Java se utiliza para ejecutar un bloque de código mientras se cumpla una condición dada. La sintaxis para crear un bucle while es la siguiente:

```
while (condición) {
   // bloque de código a ejecutar
}
```

La condición se evalúa al principio de cada iteración del bucle, y si se devuelve verdadero, se ejecuta el bloque de código dentro del bucle. Una vez que se ejecuta el bloque de código, la condición se vuelve a evaluar y así sucesivamente hasta que la condición devuelve falso.

Un ejemplo de un bucle while es el siguiente:

```
int i = 1;
while (i <= 10) {
   System.out.println(i);
   i++;
}
```

Este bucle imprimirá los números del 1 al 10 en la consola. La condición "i <= 10" se evalúa en cada iteración, y mientras sea verdadera, el bucle seguirá ejecutando el código dentro del bucle, que en este caso es simplemente imprimir el valor de "i" y luego aumentar en 1.

El bucle "do-while" en Java es similar al bucle "while", pero con una pequeña diferencia en cuanto a cuándo se evalúa la condición. En un bucle "do-while", el bloque de código dentro del bucle se ejecuta al menos una vez antes de que se evalúe la condición. Si la condición se devuelve verdadera, el bucle se ejecutará de nuevo, mientras que si devuelve false, el bucle se detendrá.

La sintaxis para crear un bucle do-while es la siguiente:

```
do {
   // bloque de código a ejecutar
} while (condición);
```

Un ejemplo de un bucle do-while es el siguiente:

```
Scanner sc = new Scanner(System.in);
char respuesta;
do {
   System.out.println("¿Desea continuar (s/n)?");
   respuesta = sc.next().charAt(0);
} while (respuesta == 's');
```

Este bucle pedirá al usuario si desea continuar (s/n) y se ejecutará mientras la respuesta sea 's'. Una vez que el usuario ingrese 'n', la condición "respuesta == 's'" se devolverá falsa y el bucle se detendrá.

https://www.tutorialspoint.com/java/java_loop_control.htm

https://www.javatpoint.com/java-while-loop

https://www.w3schools.com/java/java_while_loop.asp

### for

El bucle "for" en Java se utiliza para ejecutar un bloque de código un número específico de veces. La sintaxis para crear un bucle for es la siguiente:

```
for (inicialización; condición; incremento) {
   // bloque de código a ejecutar
}
```

La inicialización se ejecuta una sola vez al principio del bucle, la condición se evalúa antes de cada iteración del bucle, y el incremento se ejecuta al final de cada iteración del bucle. Si la condición se devuelve verdadera, se ejecuta el bloque de código dentro del bucle, y luego se ejecuta el incremento. Este proceso se repite hasta que la condición devuelve falso.

Un ejemplo de un bucle for es el siguiente:

```
for (int i = 1; i <= 10; i++) {
   System.out.println(i);
}
```

Este bucle imprimirá los números del 1 al 10 en la consola. La inicialización "int i = 1" se ejecuta una sola vez al principio del bucle, la condición "i <= 10" se evalúa antes de cada iteración del bucle, y el incremento "i++" se ejecuta al final de cada iteración del bucle. El código dentro del bucle es simplemente imprimir el valor de "i".

Otro ejemplo es el siguiente:

```
for (int i = 10; i >= 1; i--) {
   System.out.println(i);
}
```

Este bucle imprimirá los números del 10 al 1 en la consola. La inicialización "int i = 10" se ejecuta una sola vez al principio del bucle, la condición "i >= 1" se evalúa antes de cada iteración del bucle, y el incremento "i--" se ejecuta al final de cada iteración del bucle. El código dentro del bucle es simplemente imprimir el valor de "i".

Es importante mencionar que los elementos de la inicialización, condición e incremento son opcionales, es decir, puedes crear un bucle for vacio.

https://www.javatpoint.com/java-for-loop

https://www.w3schools.com/java/java_for_loop.asp

### Ejercicios y ejemplos

Aquí hay tres ejercicios de bucles en Java que puedes intentar:

    Escribir un programa que imprima los números del 1 al 100 utilizando un bucle for.

```
for (int i = 1; i <= 100; i++) {
    System.out.println(i);
}
```

    Escribir un programa que sume los números ingresados por el usuario utilizando un bucle while. El bucle debe continuar mientras el usuario ingrese números mayores a cero.

```
Scanner sc = new Scanner(System.in);
int num, sum = 0;

System.out.println("Ingrese un número (0 para terminar): ");
num = sc.nextInt();

while (num > 0) {
    sum += num;
    System.out.println("Ingrese un número (0 para terminar): ");
    num = sc.nextInt();
}

System.out.println("La suma es: " + sum);
```

    Escribir un programa que imprima la tabla de multiplicar del número ingresado por el usuario utilizando un bucle do-while. El bucle debe continuar mientras el usuario desee ver otra tabla de multiplicar.

```
Scanner sc = new Scanner(System.in);
char respuesta;
int num;

do {
    System.out.println("Ingrese un número: ");
    num = sc.nextInt();
    for (int i = 1; i <= 10; i++) {
        System.out.println(num + " x " + i + " = " + (num * i));
    }
    System.out.println("¿Desea ver otra tabla de multiplicar (s/n)?");
    respuesta = sc.next().charAt(0);
} while (respuesta == 's');
```

Recuerda que estos son solo ejemplos y puedes modificarlos para adaptarlos a tus necesidades, ademas de que estos ejercicios son para que te des una idea de como se usa cada uno de los bucles en Java.