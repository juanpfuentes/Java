# Arrays en Java  #

## Introducción ##

Un array en Java es una estructura de datos que permite almacenar una colección de elementos del mismo tipo. Los elementos del array se acceden mediante un índice numérico, comenzando desde 0. Los arrays son muy útiles para almacenar y procesar grandes cantidades de datos de manera eficiente.

Existen dos formas de declarar un array en Java:

```
int[] arr1;  // Declaración de un array vacío
int[] arr2 = new int[5];  // Declaración de un array con 5 elementos
```

También se puede declarar y asignar valores a los elementos de un array de la siguiente manera:

```
int[] arr = {1, 2, 3, 4, 5};
```

Una vez creado, se pueden acceder a los elementos del array mediante su índice:

```
int[] arr = {1, 2, 3, 4, 5};
int first = arr[0];  // first = 1
int last = arr[arr.length - 1];  // last = 5
```

También se pueden modificar los valores de los elementos de un array:

```
int[] arr = {1, 2, 3, 4, 5};
arr[2] = 10;  // El valor en la posición 2 del array es ahora 10
```

Además de los arrays unidimensionales, también existen los arrays multidimensionales, los cuales se pueden entender como arrays de arrays, y se usan para almacenar información en un formato de matriz.

```
int[][] multi = new int[3][4]; 
```


## Arrays como parámetros de métodos ##

En Java, los arrays se pueden utilizar como parámetros y valores devueltos en métodos de la misma manera que cualquier otro tipo de datos.

Para pasar un array como parámetro a un método, simplemente se proporciona el nombre del array en el parámetro del método:

```
public static void printArray(int[] arr) {
    for (int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + " ");
    }
    System.out.println();
}
```

Y se usa así:

```
int[] arr = {1, 2, 3, 4, 5};
printArray(arr);  // Imprime: 1 2 3 4 5
```

Para devolver un array desde un método, se especifica el tipo de array como el tipo de retorno del método:

```
public static int[] reverseArray(int[] arr) {
    int[] result = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        result[i] = arr[arr.length - i - 1];
    }
    return result;
}
```

Y se usa así:

```
int[] arr = {1, 2, 3, 4, 5};
int[] reversedArr = reverseArray(arr);
printArray(reversedArr);  // Imprime: 5 4 3 2 1
```

Es importante tener en cuenta que los arrays en Java son objetos, por lo que cuando se pasa un array como parámetro a un método, se está pasando una referencia al objeto array, no una copia del mismo. Por lo tanto, cualquier cambio realizado al array dentro del método se verá reflejado

## Métodos de array ##

Los principales métodos de Array en Java incluyen:

    length: Este método devuelve la longitud de un array. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
System.out.println(numbers.length);  // imprime 5
```

    sort: Este método ordena los elementos de un array en orden ascendente. Ejemplo:

```
int[] numbers = {3, 1, 4, 5, 2};
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers));  // imprime [1, 2, 3, 4, 5]
```

    fill: Este método rellena un array con un valor específico. Ejemplo:

```
int[] numbers = new int[5];
Arrays.fill(numbers, 7);
System.out.println(Arrays.toString(numbers));  // imprime [7, 7, 7, 7, 7]
```

    binarySearch: Este método busca un valor específico en un array ordenado y devuelve su índice. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
int index = Arrays.binarySearch(numbers, 3);
System.out.println(index);  // imprime 2
```

    equals: Este método compara dos arrays y devuelve verdadero si son iguales. Ejemplo:

```
int[] numbers1 = {1, 2, 3};
int[] numbers2 = {1, 2, 3};
boolean areEqual = Arrays.equals(numbers1, numbers2);
System.out.println(areEqual);  // imprime true
```

    toString: Este método convierte un array a una cadena. Ejemplo:

```
int[] numbers = {1, 2, 3};
System.out.println(Arrays.toString(numbers));  // imprime [1, 2, 3]
```

    copyOf: Este método copia un array a otro. Ejemplo:

```
int[] numbers = {1, 2, 3};
int[] numbersCopy = Arrays.copyOf(numbers, numbers.length);
System.out.println(Arrays.toString(numbersCopy));  // imprime [1, 2, 3]
```

    copyOfRange: Este método copia un rango de elementos de un array a otro. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
int[] numbersCopy = Arrays.copyOfRange(numbers, 1, 4);
System.out.println(Arrays.toString(numbersCopy));  // imprime [2, 3, 4]
```

## Pasar a stream ##

El método Arrays.stream() en Java es un método de utilidad que convierte un array en un stream (flujo) de datos. Los streams son una característica nueva en Java 8 que proporciona una forma eficiente y concisa de procesar datos. Los streams no almacenan los datos, sino que proporcionan una interfaz para procesar los datos de forma declarativa.

El método Arrays.stream() toma un array como argumento y devuelve un stream que contiene los elementos del array. Una vez que se tiene un stream, se pueden aplicar diferentes operaciones para procesar los datos, como filtrado, transformación y reducción.

Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
Arrays.stream(numbers)
      .filter(x -> x % 2 == 0)
      .forEach(x -> System.out.print(x + " "));
//output: 2 4
```

En este ejemplo, Arrays.stream(numbers) crea un stream de números, luego se utiliza el método filter() para filtrar solo los números pares y se utiliza forEach() para imprimirlos.

En resumen, el método Arrays.stream() es una forma de procesar los datos de un array de forma eficiente y concisa, utilizando las funcionalidades de los streams de Java 8.

Aquí hay algunos ejemplos de los principales métodos de stream en Java:

    filter: Este método toma una expresión lambda que especifica una condición, y devuelve un stream con solo los elementos que cumplen esa condición. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
Arrays.stream(numbers)
      .filter(x -> x % 2 == 0)
      .forEach(x -> System.out.print(x + " "));
//output: 2 4
```

    map: Este método toma una expresión lambda que especifica una transformación, y devuelve un stream con los elementos transformados. Ejemplo:

```
String[] words = {"Java", "Python", "C++", "JavaScript"};
Arrays.stream(words)
      .map(String::toUpperCase)
      .forEach(System.out::println);
//output: JAVA PYTHON C++ JAVASCRIPT
```

    forEach: Este método toma una expresión lambda que especifica una acción, y aplica esa acción a cada elemento del stream. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
Arrays.stream(numbers)
      .forEach(x -> System.out.print(x + " "));
//output: 1 2 3 4 5
```

    reduce: Este método toma una expresión lambda que especifica cómo combinar los elementos del stream, y devuelve un valor acumulado. Ejemplo:

```
int[] numbers = {1, 2, 3, 4, 5};
int sum = Arrays.stream(numbers)
                .reduce(0, (x, y) -> x + y);
System.out.println("Suma: " + sum);  // imprime "Suma: 15"
```

    min y max: Este método devuelve el elemento mínimo o máximo del stream. Ejemplo:

```
int[] numbers = {3, 7, 1, 9, 4};
int max = Arrays.stream(numbers).max().getAsInt();
int min = Arrays.stream(numbers).min().getAsInt();
System.out.println("Máximo: " + max + ", Mínimo: " + min);  // imprime "Máximo: 9, Mínimo: 1"
```

    count: Este método devuelve el número de elementos en el stream. Ejemplo:

```
String[] words = {"Java", "Python", "C++", "JavaScript"};
long count = Arrays.stream(words).count();
System.out.println("Número de palabras: " + count);  // imprime "Número de palabras: 4"
```

https://www.tutorialspoint.com/java/java_arrays.htm

https://www.javatpoint.com/array-in-java

https://www.w3schools.com/java/java_arrays.asp

## Ejercicios ##

A continuación presento algunos ejercicios:

1) Crear una función Java para copiar todos los elementos de una matriz en otra matriz
2) Crear una función Java para encontrar la frecuencia de cada elemento en la matriz
3) Crear una función Java para girar a la izquierda los elementos de una matriz
4) Crear una función Java para imprimir los elementos duplicados de una matriz
5) Crear una función Java para imprimir los elementos de una matriz
6) Crear una función Java para imprimir los elementos de una matriz en orden inverso
7) Crear una función Java para imprimir los elementos de una matriz presente en posición par
8) Crear una función Java para imprimir los elementos de una matriz presente en posición impar
9) Crear una función Java para imprimir el elemento más grande en una matriz
10) Crear una función Java para imprimir el elemento más pequeño en una matriz
11) Crear una función Java para imprimir el número de elementos presentes en una matriz
12) Crear una función Java para imprimir la suma de todos los elementos de la matriz
13) Crear una función Java para rotar a la derecha los elementos de una matriz
14) Crear una función Java para ordenar los elementos de una matriz en orden ascendente
15) Crear una función Java para ordenar los elementos de una matriz en orden descendente
16) Encuentra el tercer número más grande en una matriz
17) Encuentra el segundo número más grande en una matriz
18) Encuentra el número más grande en una matriz
19) Encuentra el segundo número más pequeño en una matriz
20) Encuentra el número más pequeño en una matriz
21) Eliminar elemento duplicado en una matriz