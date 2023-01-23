# Strings en Java  #

## Introducción ##

Los Strings en Java son objetos que representan secuencias de caracteres. Son una de las clases más comunes en Java y se utilizan en una amplia variedad de situaciones, como almacenar y manipular texto.

Hay varias formas de crear un objeto String en Java. Una forma es usando el operador "+" para concatenar varios Strings o caracteres. También puedes crear un String a partir de un arreglo de caracteres o de una porción de otro String.

```
String s1 = "Hello";
String s2 = " World";
String s3 = s1 + s2; // "Hello World"

char[] chars = {'H', 'e', 'l', 'l', 'o'};
String s4 = new String(chars);

String s5 = new String(s1, 0, 3); // "Hel"
```

Java proporciona un gran número de métodos para manipular y modificar objetos String. Por ejemplo, el método length() devuelve el número de caracteres en un String, el método substring() devuelve una porción de un String, el método toUpperCase() convierte todos los caracteres de un String a mayúsculas, y el método replace() reemplaza una porción de un String con otra.

```
String s = "Hello World";
int length = s.length(); // 11
String sub = s.substring(0, 5); // "Hello"
String upper = s.toUpperCase(); // "HELLO WORLD"
String replaced = s.replace("World", "Java"); // "Hello Java"
```

También se pueden comparar dos objetos string mediante el metodo equals() y equalsIgnoreCase() el primero compara si son iguales caracter a caracter y el segundo compara si son iguales ignorando las mayusculas y minusculas.

Los Strings son inmutables en Java, lo que significa que una vez creados, no se pueden modificar. Si deseas modificar un String, deberás crear un nuevo String con los cambios deseados. Sin embargo existen las clases StringBuilder y StringBuffer que son mutables y pueden ser modificadas.

## Comparación ##

La comparación de strings en Java se realiza mediante el método equals() o equalsIgnoreCase() de la clase String. El método equals() devuelve true si dos cadenas tienen los mismos caracteres en el mismo orden, y false en caso contrario. El método equalsIgnoreCase() funciona de la misma manera pero ignorando las mayusculas y minusculas.

Por ejemplo:

```
String s1 = "hello";
String s2 = "world";
String s3 = "Hello";

System.out.println(s1.equals(s2)); // false
System.out.println(s1.equals(s3)); // false
System.out.println(s1.equalsIgnoreCase(s3)); // true
```

Es importante tener en cuenta que el método == no se utiliza para comparar strings en Java, ya que compara si dos variables hacen referencia al mismo objeto en la memoria, no si los contenidos son iguales.

```
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");
System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
```

En el primer caso s1 y s2 apuntan al mismo objeto en memoria, por eso el resultado es true, mientras que en el segundo caso s1 y s3 apuntan a dos objetos diferentes en memoria, por eso el resultado es false.

Es recomendable siempre utilizar el método equals() o equalsIgnoreCase() para comparar strings en Java.

## Métodos ##

Aquí te presento algunos de los métodos más comunes de la clase String en Java, junto con ejemplos de cómo utilizarlos:

    length(): Este método devuelve la longitud de un String, es decir, el número de caracteres que contiene.

```
String s = "Hello World";
int length = s.length(); // 11
```

    charAt(int index): Este método devuelve el carácter en la posición especificada de un String. El primer carácter tiene un índice de 0.

```
String s = "Hello World";
char first = s.charAt(0); // 'H'
char last = s.charAt(s.length() - 1); // 'd'
```

    substring(int beginIndex, int endIndex): Este método devuelve una porción de un String. El parámetro beginIndex especifica el índice del primer carácter de la porción devuelta, y el parámetro endIndex especifica el índice del último carácter de la porción devuelta +1.

```
String s = "Hello World";
String sub = s.substring(0, 5); // "Hello"
String sub2 = s.substring(6); // "World"
```

    indexOf(String str): Este método devuelve la posición del primer carácter de la primera ocurrencia de la cadena especificada en el String. Si no se encuentra la cadena, devuelve -1.

```
String s = "Hello World";
int index = s.indexOf("World"); // 6
int index2 = s.indexOf("Java"); // -1
```

    replace(CharSequence target, CharSequence replacement): Este método devuelve una nueva cadena en la que se han reemplazado todas las ocurrencias de la cadena especificada en la cadena original con la cadena de reemplazo especificada.

```
String s = "Hello World";
String replaced = s.replace("World", "Java"); // "Hello Java"
```

    toUpperCase() y toLowerCase(): Este método devuelve una nueva cadena con todos los caracteres en mayúsculas o en minúsculas.

```
String s = "Hello World";
String upper = s.toUpperCase(); // "HELLO WORLD"
String lower = s.toLowerCase(); // "hello world"
```

    equals(Object another) y equalsIgnoreCase(String another): Este método compara si dos cadenas son iguales caracter a caracter o ignorando mayusculas y minusculas respectivamente.

## StringBuilder ##

La clase StringBuilder en Java es una clase mutable que permite construir y modificar strings de manera eficiente. A diferencia de la clase String, que es inmutable, StringBuilder permite agregar, eliminar y reemplazar caracteres en una cadena existente sin tener que crear una nueva cadena en cada operación.

Aquí te doy algunos ejemplos de cómo utilizar StringBuilder en Java:

    Crear una nueva instancia de StringBuilder:

StringBuilder sb = new StringBuilder();

    Crear una nueva instancia de StringBuilder con una cadena específica:

StringBuilder sb = new StringBuilder("Hello");

    Agregar caracteres a una cadena existente:

StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // "Hello World"

    Insertar caracteres en una posición específica:

StringBuilder sb = new StringBuilder("Hello World");
sb.insert(5, "my "); // "Hello my World"

    Reemplazar caracteres en un rango específico:

StringBuilder sb = new StringBuilder("Hello World");
sb.replace(0, 5, "Hi"); // "Hi World"

    Eliminar caracteres en un rango específico:

StringBuilder sb = new StringBuilder("Hello World");
sb.delete(0, 5); // " World"

    Obtener la cadena resultante:

StringBuilder sb = new StringBuilder("Hello World");
String result = sb.toString();

    Obtener el tamaño de la cadena:

StringBuilder sb = new StringBuilder("Hello World");
int size = sb.length();

Ten en cuenta que también existe la clase StringBuffer que es similar a StringBuilder pero es thread-safe, es decir, se garantiza que varios hilos pueden acceder a un objeto StringBuffer simultáneamente sin causar problemas. Sin embargo, StringBuffer es menos eficiente que StringBuilder en caso de no ser utilizado en un ambiente multi-thread.

https://www.tutorialspoint.com/java/java_strings.htm

https://www.javatpoint.com/java-string

https://www.w3schools.com/java/java_strings.asp

## Ejercicios ##

Aquí te doy 6 ejercicios relacionados con la clase String en Java para practicar:

Escribir una función que invierta el orden de los caracteres de una cadena dada. invertir("hola")-->"aloh"

Escribir una función que cuente el número de veces que se repite un carácter específico en una cadena dada. contarChar("gola que tal",'a')-->2

Escribir una función que elimine los espacios en blanco al principio y al final de una cadena dada. sinEspacios("  cadena  ")-->cadena

Escribir una función que compruebe si una cadena es un palíndromo (una palabra o frase que se lee igual de izquierda a derecha y de derecha a izquierda). palindromo("hola")--> false palindromo("ana")-->true

Escribir una función que elimine todas las ocurrencias de una subcadena específica de una cadena dada. eliminar("que queso es un paquete","que")-->" so es un pate"

Escribir una función que reemplace todas las ocurrencias de un carácter específico en una cadena dada con otro carácter. cambiar("hola que tal","a","@")-->"hol@ que t@l"