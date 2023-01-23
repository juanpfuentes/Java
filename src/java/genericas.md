# Colecciones y genéricos Java #

## Colecciones ##

[ArrayList]

Sí, un ArrayList en Java es una implementación de la interfaz List que permite almacenar una colección de elementos ordenados. Es similar a un array, pero tiene algunas ventajas adicionales, como la capacidad de ajustar dinámicamente su tamaño.

Ejemplo de creación de un ArrayList:

```
ArrayList<String> lista = new ArrayList<String>();
```

Ejemplo de agregar elementos a un ArrayList:

```
lista.add("elemento 1");
lista.add("elemento 2");
lista.add("elemento 3");
```

Ejemplo de acceder a un elemento en un ArrayList:

```
String elemento = lista.get(1);
```

Ejemplo de eliminar un elemento de un ArrayList:

```
lista.remove(1);
```

Ejemplo de recorrer un ArrayList:

```
for (String elemento : lista) {
   System.out.println(elemento);
}
```

Hay muchas otras operaciones disponibles para ArrayList, como insertar elementos en una posición específica, buscar elementos, etc. Se recomienda revisar la documentación de ArrayList en la página web de Java para obtener más información.

Aquí tienes un ejemplo de cómo crear y utilizar un ArrayList en Java:

```
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        // Crear un ArrayList de enteros
        ArrayList<Integer> numbers = new ArrayList<>();

        // Añadir elementos al ArrayList
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);

        // Imprimir el tamaño del ArrayList
        System.out.println("Tamaño del ArrayList: " + numbers.size());

        // Imprimir todos los elementos del ArrayList
        for (int num : numbers) {
            System.out.println(num);
        }

        // Eliminar un elemento del ArrayList
        numbers.remove(1);

        // Imprimir el tamaño del ArrayList después de eliminar un elemento
        System.out.println("Tamaño del ArrayList después de eliminar un elemento: " + numbers.size());

        // Imprimir todos los elementos del ArrayList después de eliminar un elemento
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

Este ejemplo crea un ArrayList de enteros, añade algunos elementos, imprime el tamaño del ArrayList, imprime todos los elementos del ArrayList, elimina un elemento y vuelve a imprimir el tamaño y los elementos del ArrayList.

Aquí te presento algunos de los métodos más comunes de ArrayList en Java con ejemplos:

    add(element): Añade un elemento al final de la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
```

    add(index, element): Añade un elemento en la posición especificada en la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
list.add(1, "pájaro");
```

    get(index): Devuelve el elemento en la posición especificada en la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
String element = list.get(1);
System.out.println(element); // imprime "gato"
```

    remove(index): Elimina el elemento en la posición especificada en la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
list.remove(1);
```

    size(): Devuelve el número de elementos en la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
int size = list.size();
System.out.println(size); // imprime 2
```

    clear(): Elimina todos los elementos de la lista. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
list.clear();
```

    isEmpty(): Devuelve si la lista esta vacía o no. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
boolean isEmpty = list.isEmpty();
System.out.println(isEmpty); // imprime false
```

    contains(element): Devuelve si el elemento especificado existe en la lista o no. Ejemplo:

```
ArrayList<String> list = new ArrayList<>();
list.add("perro");
list.add("gato");
boolean contain = list.contains("perro");
System.out.println(contain); // imprime true
```

https://www.javatpoint.com/java-arraylist

https://www.w3schools.com/java/java_arraylist.asp

[LinkedList] 

LinkedList es una clase en Java que implementa la interfaz List y utiliza un enlace simple para almacenar elementos. Cada elemento en una LinkedList tiene un enlace al siguiente elemento en la lista.

Aquí tienes un ejemplo de cómo crear y utilizar una LinkedList en Java:

```
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        // Crear una LinkedList de enteros
        LinkedList<Integer> numbers = new LinkedList<>();

        // Añadir elementos a la LinkedList
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);

        // Añadir un elemento al inicio de la lista
        numbers.addFirst(0);

        // Imprimir el tamaño de la LinkedList
        System.out.println("Tamaño de la LinkedList: " + numbers.size());

        // Imprimir todos los elementos de la LinkedList
        for (int num : numbers) {
            System.out.println(num);
        }

        // Eliminar un elemento de la LinkedList
        numbers.remove(1);

        // Imprimir el tamaño de la LinkedList después de eliminar un elemento
        System.out.println("Tamaño de la LinkedList después de eliminar un elemento: " + numbers.size());

        // Imprimir todos los elementos de la LinkedList después de eliminar un elemento
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

Este ejemplo crea una LinkedList de enteros, añade algunos elementos, añade un elemento al inicio de la lista, imprime el tamaño de la LinkedList, imprime todos los elementos de la LinkedList, elimina un elemento y vuelve a imprimir el tamaño y los elementos de la LinkedList.

Una de las ventajas de utilizar una LinkedList en lugar de un ArrayList es que las operaciones de inserción y eliminación en una posición específica son más rápidas en una LinkedList debido a que no requiere desplazar los elementos en la lista. Sin embargo, las operaciones de acceso aleatorio son más lentas en una LinkedList en comparación con un ArrayList.

Aquí te presento algunos de los métodos más comunes de LinkedList en Java con ejemplos:

    add(element): Añade un elemento al final de la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
```

    addFirst(element): Añade un elemento al inicio de la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.addFirst("perro");
list.addFirst("gato");
```

    getFirst(): Devuelve el primer elemento de la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
String first = list.getFirst();
System.out.println(first); // imprime "perro"
```

    removeFirst(): Elimina el primer elemento de la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
list.removeFirst();
```

    size(): Devuelve el número de elementos en la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
int size = list.size();
System.out.println(size); // imprime 2
```

    clear(): Elimina todos los elementos de la lista. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
list.clear();
```

    isEmpty(): Devuelve si la lista esta vacía o no. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
boolean isEmpty = list.isEmpty();
System.out.println(isEmpty); // imprime false
```

    contains(element): Devuelve si el elemento especificado existe en la lista o no. Ejemplo:

```
LinkedList<String> list = new LinkedList<>();
list.add("perro");
list.add("gato");
boolean contain = list.contains("perro");
System.out.println(contain); // imprime true
```

Estos son solo algunos de los métodos más comunes de LinkedList en Java. Hay muchos otros métodos disponibles en la clase LinkedList que puedes utilizar para realizar diferentes operaciones en una lista enlazada.

https://www.javatpoint.com/java-linkedlist

https://www.w3schools.com/java/java_linkedlist.asp

[HashMap] 

HashMap es una clase en Java que implementa la interfaz Map. Un HashMap almacena elementos en forma de pares clave-valor, en donde la clave es única y se utiliza para acceder al valor correspondiente.

Aquí tienes un ejemplo de cómo crear y utilizar un HashMap en Java:

```
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // Crear un HashMap de enteros y cadenas
        HashMap<String, Integer> map = new HashMap<>();

        // Añadir elementos al HashMap
        map.put("one", 1);
        map.put("two", 2);
        map.put("three", 3);

        // Obtener el valor de una clave específica
        int value = map.get("two");
        System.out.println("Valor de la clave 'two': " + value);

        // Imprimir todos los elementos del HashMap
        for (String key : map.keySet()) {
            System.out.println("Clave: " + key + ", Valor: " + map.get(key));
        }

        // Eliminar un elemento del HashMap
        map.remove("two");

        // Imprimir todos los elementos del HashMap después de eliminar un elemento
        for (String key : map.keySet()) {
            System.out.println("Clave: " + key + ", Valor: " + map.get(key));
        }
    }
}
```

Este ejemplo crea un HashMap de enteros y cadenas, añade algunos elementos, obtiene el valor de una clave específica, imprime todos los elementos del HashMap, elimina un elemento y vuelve a imprimir todos los elementos del Hash.

Aquí te presento algunos de los métodos más comunes de HashMap en Java con ejemplos:

    put(key, value): Añade un par clave-valor al HashMap. Ejemplo:

```
HashMap<String, Integer> map = new HashMap<>();
map.put("one", 1);
map.put("two", 2);
```

    get(key): Devuelve el valor asociado a la clave especificada. Ejemplo:

```
HashMap<String, Integer> map = new HashMap<>();
map.put("one", 1);
map.put("two", 2);
int value = map.get("two");
System.out.println(value); // imprime 2
```

    remove(key): Elimina el par clave-valor con la clave especificada. Ejemplo:

```
HashMap<String, Integer> map = new HashMap<>();
map.put("one", 1);
map.put("two", 2);
map.remove("two");
```

Un HashMap en Java es una implementación de un mapa que utiliza una función de hash para asignar valores a claves específicas. A continuación se presentan algunos de los métodos más comunes de HashMap en Java:

    put(key, value): Este método se utiliza para agregar un nuevo par clave-valor al mapa. Ejemplo:

```
HashMap<String, Integer> map = new HashMap<>();
map.put("uno", 1);
map.put("dos", 2);
```

    get(key): Este método se utiliza para obtener el valor asociado a una clave específica. Ejemplo:

```
int value = map.get("uno");
```

    remove(key): Este método se utiliza para eliminar un par clave-valor específico del mapa. Ejemplo:

```
map.remove("dos");
```

    containsKey(key): Este método se utiliza para determinar si una clave específica está presente en el mapa. Ejemplo:

```
boolean containsKey = map.containsKey("uno");
```

    clear(): Este método se utiliza para eliminar todos los pares clave-valor del mapa. Ejemplo:

```
map.clear();
```

    size(): Este método se utiliza para obtener el número de pares clave-valor en el mapa. Ejemplo:

```
int size = map.size();
```

    isEmpty(): Este método se utiliza para determinar si el mapa está vacío. Ejemplo:

```
boolean isEmpty = map.isEmpty();
```

    keySet(): Este método se utiliza para obtener un conjunto de todas las claves en el mapa. Ejemplo:

```
Set<String> keys = map.keySet();
```

    values(): Este método se utiliza para obtener una colección de todos los valores en el mapa. Ejemplo:

```
Collection<Integer> values = map.values();
```

    entrySet(): Este método se utiliza para obtener un conjunto de todos los pares clave-valor en el mapa. Ejemplo:

```
Set<Map.Entry<String, Integer>> entries = map.entrySet();
```


https://www.javatpoint.com/java-hashmap

https://www.w3schools.com/java/java_hashmap.asp

[HashSet] 

En Java, un HashSet es una implementación de un conjunto (set) que utiliza una tabla hash para almacenar sus elementos. Los elementos en un HashSet no están ordenados, y no se permiten elementos duplicados.

Para utilizar un HashSet, primero se debe importar la clase "java.util.HashSet". Luego, se puede crear una nueva instancia del HashSet usando el constructor vacío:

```
import java.util.HashSet;

HashSet<String> palabras = new HashSet<String>();
```

Para agregar elementos al HashSet, se puede utilizar el método "add()":

```
palabras.add("perro");
palabras.add("gato");
palabras.add("ratón");
```

Para verificar si un elemento está en el HashSet, se puede utilizar el método "contains()":

```
if (palabras.contains("perro")) {
    System.out.println("El conjunto contiene la palabra perro");
}
```

Para recorrer todos los elementos de un HashSet, se puede utilizar un iterador:

```
for (String palabra : palabras) {
    System.out.println(palabra);
}
```

Para eliminar un elemento del HashSet, se puede utilizar el método "remove()":

```
palabras.remove("ratón");
```

Un HashSet es una estructura de datos eficiente para buscar, añadir y eliminar elementos. Sin embargo, debido a que los elementos no están ordenados, no se pueden recorrer en un orden específico.

Un HashSet en Java es una implementación de un conjunto que utiliza una función de hash para almacenar elementos únicos. A continuación se presentan algunos de los métodos más comunes de HashSet en Java:

    add(element): Este método se utiliza para agregar un nuevo elemento al conjunto. Ejemplo:

```
HashSet<Integer> set = new HashSet<>();
set.add(1);
set.add(2);
```

    remove(element): Este método se utiliza para eliminar un elemento específico del conjunto. Ejemplo:

```
set.remove(1);
```

    contains(element): Este método se utiliza para determinar si un elemento específico está presente en el conjunto. Ejemplo:

```
boolean contains = set.contains(2);
```

    clear(): Este método se utiliza para eliminar todos los elementos del conjunto. Ejemplo:

```
set.clear();
```

    size(): Este método se utiliza para obtener el número de elementos en el conjunto. Ejemplo:

```
int size = set.size();
```

    isEmpty(): Este método se utiliza para determinar si el conjunto está vacío. Ejemplo:

```
boolean isEmpty = set.isEmpty();
```

    iterator(): Este método se utiliza para obtener un iterador para recorrer todos los elementos del conjunto. Ejemplo:

```
Iterator<Integer> iterator = set.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

    toArray(): Este método se utiliza para obtener un arreglo con todos los elementos del conjunto. Ejemplo:

```
Object[] array = set.toArray();
```

    addAll(collection): Este método se utiliza para agregar todos los elementos de una colección específica al conjunto. Ejemplo:

```
HashSet<Integer> otherSet = new HashSet<>();
otherSet.add(3);
otherSet.add(4);
set.addAll(otherSet);
```

    retainAll(collection): Este método se utiliza para conservar solo los elementos que están presentes tanto en el conjunto y en una colección específica. Ejemplo:

```
HashSet<Integer> otherSet = new HashSet<>();
otherSet.add(2);
otherSet.add(3);
set.retainAll(otherSet);
```

Es importante mencionar que todos los métodos mencionados anteriormente son parte de la interface Set.

https://www.javatpoint.com/java-hashset

https://www.w3schools.com/java/java_hashset.asp

## Genéricos ##

[Genéricos]

Los tipos genéricos en Java son un mecanismo de programación que permite crear clases y métodos parametrizados. Esto significa que en lugar de especificar un tipo específico de datos, se especifica un parámetro de tipo que puede ser reemplazado por un tipo específico al crear una instancia de la clase o al invocar el método.

Por ejemplo, la clase ArrayList en Java es una clase genérica que permite crear una lista de cualquier tipo de datos. En lugar de tener que crear una clase específica para cada tipo de datos, se puede crear una clase ArrayList<E> donde E es el parámetro de tipo. Al crear una instancia de ArrayList, se especifica el tipo de datos que se utilizará, como ArrayList<Integer> o ArrayList<String>

```
ArrayList<Integer> numbers = new ArrayList<>();
numbers.add(1);
numbers.add(2);

ArrayList<String> words = new ArrayList<>();
words.add("Hola");
words.add("Mundo");
```

También se pueden utilizar tipos genéricos en métodos, por ejemplo, se puede crear un método genérico que intercambie dos elementos en una lista:

```
public static <E> void swap(List<E> list, int i, int j) {
    E temp = list.get(i);
    list.set(i, list.get(j));
    list.set(j, temp);
}
```

En este ejemplo, el método swap() es parametrizado con el tipo genérico E, que puede ser reemplazado por cualquier tipo de datos al invocar el método.

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<String> words = Arrays.asList("Hola", "Mundo", "Java", "Genéricos");

swap(numbers, 0, 1);
swap(words, 1, 2);
```

Los tipos genéricos proporcionan una forma de escribir código más genérico y reusable, ya que se pueden crear clases y métodos que funcionen con cualquier tipo de datos sin tener que crear una clase o un método específico para cada tipo de datos.

Para crear una clase genérica en Java, se especifican los parámetros de tipo entre los corchetes < > después del nombre de la clase. Por ejemplo, para crear una clase genérica que represente un par de valores, se puede utilizar el siguiente código:

```
class Pair<T, U> {
    private T first;
    private U second;

    public Pair(T first, U second) {
        this.first = first;
        this.second = second;
    }

    public T getFirst() {
        return first;
    }

    public U getSecond() {
        return second;
    }
}
```

En este ejemplo, la clase Pair está parametrizada con dos tipos genéricos T y U. Estos tipos genéricos pueden ser reemplazados por cualquier tipo de datos al crear una instancia de la clase.

```
Pair<Integer, String> pair = new Pair<>(1, "Hola");
System.out.println(pair.getFirst()); // Output: 1
System.out.println(pair.getSecond()); // Output: "Hola"

También se pueden especificar restricciones en los tipos genéricos utilizando la keyword "extends", por ejemplo:

class MyClass<T extends Number> {
    // class implementation here
}
```

En este ejemplo, el tipo genérico T solo puede ser reemplazado por tipos que extienden de la clase Number, como Integer, Double, etc.

Es importante notar que los tipos genéricos son una característica de Java desde la versión 5.0, antes de esta versión se podían usar clases como Vector o ArrayList pero no se podía especificar el tipo de dato que almacenaba.

https://www.tutorialspoint.com/java/java_generics.htm

https://www.javatpoint.com/generics-in-java


### Ejercicios ###

Crea un ArrayList de cadenas y añade 10 nombres de personas. Luego, utiliza un ciclo para imprimir todos los nombres en orden inverso.

Crea un ArrayList de números enteros y añade 15 números aleatorios. Utiliza el método sort() para ordenar los números en orden ascendente y luego imprime todos los números.

Crea un ArrayList de objetos de una clase personalizada que tenga un nombre y una edad. Añade 5 objetos a la lista y utiliza un ciclo for para imprimir todos los objetos y sus detalles.

Crea un ArrayList de cadenas y añade 20 palabras. Utiliza el método removeIf() para eliminar todas las palabras que tengan más de 5 caracteres y luego imprime todas las palabras restantes.

Crea un ArrayList de números decimales y añade 10 números. Utiliza el método toArray() para convertir el ArrayList en un arreglo y luego utiliza un ciclo para imprimir todos los números en el arreglo.

Crea una LinkedList de cadenas y añade 10 nombres de ciudades. Utiliza el método addFirst() para añadir otro nombre al principio de la lista y luego utiliza un ciclo para imprimir todos los nombres en orden inverso.

Crea una LinkedList de objetos de una clase personalizada que tenga un título y un autor. Añade 5 objetos a la lista y utiliza el método removeFirst() para eliminar el primer objeto en la lista. A continuación, utiliza un ciclo for para imprimir todos los objetos y sus detalles.

Crea una LinkedList de números enteros y añade 15 números aleatorios. Utiliza el método getFirst() para obtener el primer número en la lista y luego utiliza un ciclo for para imprimir todos los números en la lista excepto el primero.

Crea una LinkedList de cadenas y añade 20 palabras. Utiliza el método remove() para eliminar todas las palabras que comienzan con una letra específica y luego imprime todas las palabras restantes.

Crea una LinkedList de objetos de una clase personalizada que tenga un nombre y una edad. Añade 5 objetos a la lista y utiliza el método clear() para eliminar todos los elementos de la lista. A continuación, utiliza el método isEmpty() para comprobar si la lista está vacía y luego añade otros 3 objetos a la lista.

Crear un programa que permita almacenar los nombres y teléfonos de contactos en un HashMap, y luego permita al usuario buscar y mostrar el teléfono de un contacto específico a través de su nombre.

Crear un programa que almacene una lista de productos con sus precios en un HashMap, y luego permita al usuario buscar y mostrar el precio de un producto específico a través de su nombre.

Crear un programa que utilice un HashMap para almacenar las calificaciones de un estudiante en diferentes materias, y luego calcule y muestre el promedio de calificaciones del estudiante.

Crear un programa que utilice un HashMap para almacenar las palabras de una oración y sus respectivas frecuencias de aparición, y luego muestre las palabras ordenadas por frecuencia de aparición.

Crear un programa que utilice un HashMap para almacenar un diccionario de palabras y sus definiciones, y luego permita al usuario buscar y mostrar la definición de una palabra específica.

Crear un programa que permita al usuario ingresar una lista de números y utilice un HashSet para almacenarlos de manera única, luego mostrar los números ingresados en orden inverso.

Crear un programa que permita al usuario ingresar una lista de palabras y utilice un HashSet para almacenarlas de manera única, luego mostrar las palabras ingresadas en orden alfabético.

Crear un programa que utilice un HashSet para almacenar los nombres de varios estudiantes en un curso, y luego permita al usuario ingresar un nombre y determinar si ese estudiante está matriculado en el curso.

Crear un programa que utilice un HashSet para almacenar los números de una lotería y determinar si un número específico ha sido sorteado en el pasado.

Crear un programa que utilice un HashSet para almacenar las direcciones IP de una red y determinar si una dirección IP específica está siendo utilizada actualmente.

Crear una clase genérica "Stack" que permita almacenar elementos en un orden LIFO (Last In First Out) y proporcione métodos para agregar, eliminar y obtener elementos.

Crear una clase genérica "Queue" que permita almacenar elementos en un orden FIFO (First In First Out) y proporcione métodos para agregar, eliminar y obtener elementos.

Crear una clase genérica "Pair" que represente un par de valores y proporcione métodos para obtener y establecer ambos valores.

Crear una clase genérica "MyList" que extienda de la clase ArrayList y proporcione un método adicional para buscar y eliminar el primer elemento que cumpla con una condición específica.

Crear una clase genérica "MyMap" que extienda de la clase HashMap y proporcione un método adicional para obtener una lista de todos los valores ordenados por clave.