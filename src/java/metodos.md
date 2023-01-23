# Funciones y métodos en Java  #

## Introducción ##

Los métodos en Java son bloques de código que realizan una tarea específica y pueden ser llamados por otras partes del programa. Un método tiene un nombre, un conjunto de parámetros de entrada (opcionales) y puede regresar un valor o no. Los métodos permiten la reutilización de código y ayudan a organizar y dividir un programa en partes más manejables. Los métodos también pueden tener modificadores de acceso (como public, private, protected) que controlan cómo y desde dónde pueden ser llamados.

## Parámetros ##

Los parámetros de entrada en un método en Java son variables que se pasan al método cuando se llama. Estas variables se utilizan dentro del cuerpo del método para realizar cálculos o modificaciones. Por ejemplo, un método que calcula el área de un círculo podría tener un parámetro de entrada "radio" que se utiliza en la fórmula para calcular el área.

```
public double calcularAreaCirculo(double radio){
   return Math.PI * Math.pow(radio, 2);
}
```

En este ejemplo, el método "calcularAreaCirculo" tiene un parámetro de entrada "radio", que es de tipo double y se utiliza en la fórmula para calcular el área del círculo.

Los métodos también pueden tener parámetros de salida, es decir, un valor que es devuelto al llamar al método. El tipo de valor devuelto se especifica antes del nombre del método. Por ejemplo, el método anterior devuelve un double.

```
public int suma(int a, int b){
    return a + b;
}
```

En este ejemplo, el método "suma" tiene dos parámetros de entrada "a" y "b" ambos de tipo int, y devuelve un int que es la suma de ambos.

En resumen, los parámetros de entrada son variables que se pasan al método cuando se llama, y se utilizan dentro del cuerpo del método para realizar cálculos o modificaciones. Los parámetros de salida son un valor que es devuelto al llamar al método.

## Sobrecarga de métodos ##

La sobrecarga de métodos en Java es una característica que permite tener varios métodos con el mismo nombre en una clase, siempre y cuando tengan diferentes parámetros de entrada.
Es decir, se puede tener varios métodos con el mismo nombre en una clase, siempre y cuando tengan diferentes cantidades o tipos de parámetros. Esto es útil para crear métodos más generales o flexibles.

Por ejemplo, podrías tener un método llamado "imprimir" que puede imprimir diferentes tipos de datos, como un número, una cadena o un objeto, dependiendo de los parámetros de entrada:

```
public void imprimir(int num){
    System.out.println("El numero es: "+num);
}
public void imprimir(String texto){
    System.out.println("El texto es: "+texto);
}
public void imprimir(Object obj){
    System.out.println("El objeto es: "+obj);
}
```

En este ejemplo, todos los métodos tienen el mismo nombre "imprimir", pero tienen diferentes parámetros de entrada (int, String, Object) y por tanto son diferentes entre si y se pueden utilizar de forma independiente.

Es importante mencionar que la sobrecarga de métodos no se refiere a la sobreescritura de métodos, que es cuando una subclase tiene un método con el mismo nombre y firma que un método en su superclase, y proporciona una implementación diferente.

## Ámbito de las variables ##

El ámbito de una variable en Java también se refiere a la parte del programa en la que la variable es visible y puede ser utilizada, dependiendo del bloque en el que se haya definido.

Variables declaradas en el ámbito de la clase: Son variables que son declaradas fuera de cualquier bloque o método en una clase, son visibles en toda la clase y pueden ser utilizadas en cualquier método de la clase.

```
class Ejemplo{
    int numero;
    void metodo1(){
        numero = 5;
    }
    void metodo2(){
        System.out.println(numero);
    }
}
```

En este ejemplo, la variable "numero" es declarada en el ámbito de la clase y puede ser utilizada en ambos métodos "metodo1" y "metodo2".

Variables declaradas en el ámbito de un método: Son variables que son declaradas dentro de un método, son visibles solo dentro de ese método y no pueden ser utilizadas fuera de él.

```
class Ejemplo{
    void metodo1(){
        int numero = 5;
    }
    void metodo2(){
        System.out.println(numero); //Error, numero no esta disponible en este ámbito
    }
}
```

En este ejemplo, la variable "numero" es declarada en el ámbito del método "metodo1" y solo esta disponible en este método, no puede ser utilizada fuera de él.

Variables declaradas en el ámbito de un bloque: Son variables que son declaradas dentro de un bloque, como un bloque if, while, for, etc. Son visibles solo dentro de ese bloque y no pueden ser utilizadas fuera de él.

```
class Ejemplo{
    void metodo1(){
        int numero = 5;
        if(numero > 0){
            int numero2 = 10;
        }
        System.out.println(numero2); //Error, numero2 no esta disponible en este ámbito
    }
}
```

En este ejemplo, la variable "numero2" es declarada en el ámbito del bloque "if" dentro del método "metodo1" y solo esta disponible dentro de este bloque, no puede ser utilizada fuera de él.

```
public class Ambito {
 
    public static void main(String[] args) {
        // x está definida para todo el bloque, incluyendo subbloques
        int x=0;
         
        for(int i=0;i<10;i++) {
            // i y nombre sólo están definidas dentro de este bloque
            String nombre="Juan";
            System.out.println(i);
            System.out.println(nombre);
            System.out.println(x);
        }
        // x existe
        System.out.println(x);
        // Pero i y nombre no porque se ha cerrado el bloque en el que
        // estaban definidas
        System.out.println(i);
        System.out.println(nombre);
 
    }
 
}
```

En resumen, el ámbito de una variable en java depende del bloque en el que se haya definido, las variables declaradas en el ámbito de la clase son visibles en toda la clase, las variables declaradas en el ámbito de un método son visibles solo dentro de ese método y las variables declaradas en el bloque solo son visibles dentro del bloque.

https://www.tutorialspoint.com/java/java_methods.htm

https://www.w3schools.com/java/java_methods.asp

https://www.programiz.com/java-programming/methods

## Recursividad ##

La recursión en Java es una técnica de programación en la cual un método llama a sí mismo para resolver un problema. Es una forma de resolver problemas complejos mediante la división del problema en subproblemas más pequeños y similares, hasta que se alcance un caso base.

Ejemplo 1: Calcular el factorial de un número. El factorial de un número n es el producto de n por todos los números enteros positivos menores a él. El caso base es cuando n es igual a 1, en cuyo caso se devuelve 1.

```
public int factorial(int n) {
    if (n == 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}
```

Ejemplo 2: Calcular la serie de fibonacci: La serie de Fibonacci es una secuencia en la cual cada número es la suma de los dos números anteriores. La serie comienza con 0 y 1 y continúa con 1, 2, 3, 5, 8, etc. El caso base es cuando n es igual a 0 o 1, en cuyo caso se devuelve n.

```
public int fibonacci(int n) {
    if (n == 0 || n == 1) {
        return n;
    } else {
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
}
```

Es importante tener en cuenta que el uso excesivo de recursión puede causar un desbordamiento de pila y hacer que su aplicación sea inestable. Es importante siempre tener un caso base y una forma de salir de la recursión.

No siempre la recursividad se utiliza con series matemáticas. Aquí te dejo un ejemplo de un método en Java que busca recursivamente archivos con un nombre dado en una carpeta dada:

```
import java.io.File;

public class FileSearch {

    public static void search(String directoryName, String fileName) {
        File directory = new File(directoryName);
        File[] fList = directory.listFiles();
        for (File file : fList) {
            if (file.isFile() && file.getName().equals(fileName)) {
                System.out.println("Archivo encontrado en: " + file.getAbsolutePath());
            } else if (file.isDirectory()) {
                search(file.getAbsolutePath(), fileName);
            }
        }
    }

    public static void main(String[] args) {
        String directory = "/path/to/directory";
        String fileName = "example.txt";
        search(directory, fileName);
    }
}
```

El método search() toma dos parámetros: el primer parámetro es el nombre de la carpeta en la que se va a buscar, y el segundo parámetro es el nombre del archivo que se está buscando. Dentro del método, se crea un objeto File para la carpeta especificada y se obtiene una lista de todos los archivos y carpetas dentro de esa carpeta. A continuación, se itera a través de cada archivo y carpeta en la lista, y se comprueba si es un archivo y si tiene el nombre especificado. Si es así, se imprime la ruta absoluta del archivo. Si es una carpeta, se llama recursivamente al método search() con la ruta de la carpeta como el primer parámetro.

Ten en cuenta que este ejemplo imprime la ruta del archivo encontrado, si quieres hacer algo más con él, puedes hacerlo en esa linea.