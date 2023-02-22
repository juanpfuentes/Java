# Java Comparadores #

En Java, un Comparator es una interfaz que se utiliza para ordenar objetos. Un Comparator compara dos objetos y devuelve un valor que indica si el primer objeto es menor, igual o mayor que el segundo objeto en términos de ordenamiento.

La interfaz Comparator tiene un único método, compare(), que se utiliza para comparar dos objetos. Este método toma dos argumentos y devuelve un número entero que indica la relación de orden entre los dos objetos. Si el primer objeto es menor que el segundo objeto, el método debe devolver un número negativo. Si el primer objeto es mayor que el segundo objeto, el método debe devolver un número positivo. Si los dos objetos son iguales en términos de ordenamiento, el método debe devolver cero.

Aquí hay un ejemplo de cómo se puede utilizar la interfaz Comparator para ordenar objetos de una clase personalizada llamada Person en función de su edad:

```
import java.util.Comparator;

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();
        people.add(new Person("Alice", 25));
        people.add(new Person("Bob", 20));
        people.add(new Person("Charlie", 30));

        // Ordena la lista de personas por edad usando un Comparator
        people.sort(new Comparator<Person>() {
            @Override
            public int compare(Person p1, Person p2) {
                return Integer.compare(p1.getAge(), p2.getAge());
            }
        });

        // Imprime la lista ordenada de personas
        for (Person person : people) {
            System.out.println(person.getName() + " (" + person.getAge() + ")");
        }
    }
}
```

En este ejemplo, el método compare() del Comparator compara dos objetos Person basándose en su edad utilizando el método Integer.compare(). Luego, la lista de objetos Person se ordena usando este Comparator, lo que resulta en la lista ordenada por edad. La salida del programa sería:

```

Bob (20)
Alice (25)
Charlie (30)
```

Este es solo un ejemplo básico de cómo se puede utilizar la interfaz Comparator en Java para ordenar objetos. Hay muchas formas de utilizar un Comparator para ordenar objetos en función de diferentes criterios de ordenamiento.

https://www.baeldung.com/java-comparator-comparable
https://www.javatpoint.com/Comparator-interface-in-collection-framework

## Comparing ##

n Java, Comparator.comparing es un método de conveniencia que permite crear un comparador utilizando una función que extrae una clave de ordenamiento de los objetos que se van a comparar. Este método devuelve un Comparator que compara objetos utilizando la clave de ordenamiento extraída.

La sintaxis básica del método Comparator.comparing es la siguiente:

```

Comparator.comparing(keyExtractor)
```

donde keyExtractor es una función que toma un objeto y devuelve la clave de ordenamiento. La clave de ordenamiento debe ser un tipo que implemente la interfaz Comparable, ya que el comparador que se crea utilizará el método compareTo para comparar las claves de ordenamiento.

Aquí hay un ejemplo de cómo se puede utilizar Comparator.comparing para ordenar objetos de una clase personalizada llamada Person en función de su edad:

```

import java.util.Comparator;

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();
        people.add(new Person("Alice", 25));
        people.add(new Person("Bob", 20));
        people.add(new Person("Charlie", 30));

        // Ordena la lista de personas por edad usando Comparator.comparing
        people.sort(Comparator.comparing(Person::getAge));

        // Imprime la lista ordenada de personas
        for (Person person : people) {
            System.out.println(person.getName() + " (" + person.getAge() + ")");
        }
    }
}
```

En este ejemplo, se utiliza Comparator.comparing para crear un Comparator que compara objetos Person basándose en su edad utilizando la función Person::getAge, que es una referencia de método que extrae la edad de un objeto Person. Luego, la lista de objetos Person se ordena utilizando este Comparator, lo que resulta en la lista ordenada por edad. La salida del programa sería:

```

Bob (20)
Alice (25)
Charlie (30)
```

## Comparable ##

Para implementar la interfaz Comparable en una clase personalizada en Java, debes definir el método compareTo en la clase. El método compareTo toma un objeto de la misma clase como argumento y devuelve un número entero que indica si el objeto actual es menor, igual o mayor que el objeto pasado como argumento. El número entero debe ser negativo si el objeto actual es menor que el objeto pasado como argumento, cero si son iguales y positivo si el objeto actual es mayor que el objeto pasado como argumento.

Aquí hay un ejemplo de cómo se puede implementar Comparable en una clase personalizada llamada Person:

```

public class Person implements Comparable<Person> {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age);
    }
}
```


En este ejemplo, la clase Person implementa la interfaz Comparable con el tipo de parámetro genérico Person. La implementación del método compareTo compara dos objetos Person basándose en su edad utilizando el método Integer.compare(). La implementación devuelve un número negativo si el objeto actual es menor que el objeto pasado como argumento, cero si son iguales y positivo si el objeto actual es mayor que el objeto pasado como argumento.

Con la implementación de Comparable, podemos ordenar fácilmente una lista de objetos Person utilizando el método sort() de la clase Collections:

```

List<Person> people = new ArrayList<>();
people.add(new Person("Alice", 25));
people.add(new Person("Bob", 20));
people.add(new Person("Charlie", 30));

Collections.sort(people);

for (Person person : people) {
    System.out.println(person.getName() + " (" + person.getAge() + ")");
}
```

En este ejemplo, creamos una lista de objetos Person y la ordenamos utilizando Collections.sort(). Debido a que la clase Person implementa la interfaz Comparable, el método sort() puede comparar objetos Person utilizando el método compareTo definido en la clase. La salida del programa sería:

## Ordenar un arraylist ##

```
List<Alumno> clase=new ArrayList<>();
		clase.add(new Alumno("a",1));
		clase.add(new Alumno("b",6));
		clase.add(new Alumno("c",2));
		clase.add(new Alumno("d",8));
		clase.sort(Comparator.comparing(x->x.getNota()));
		
		System.out.println(clase);
```
```
public class Alumno  implements Comparable<Alumno>{
	private String nombre;
	private int nota;

[...]

public int compareTo(Alumno o) {
		return Integer.compare(getNota(), o.getNota());
	}
    ```

    https://www.javatpoint.com/how-to-sort-arraylist-in-java