# JSON  #

## Introducción ##

JSON es un formato de intercambio de datos ligeros y de texto plano que es utilizado para representar objetos de manera estructurada en el desarrollo de aplicaciones. Se utiliza para transmitir datos a través de Internet, especialmente en aplicaciones basadas en la web.

JSON es fácil de leer y escribir tanto para humanos como para máquinas, lo que lo hace ideal para su uso en aplicaciones distribuidas. Además, es compatible con la mayoría de los lenguajes de programación, incluyendo Java, JavaScript, Python, Ruby, PHP y muchos otros.

## Conceptos ##

JSON (JavaScript Object Notation) es un formato de intercambio de datos ligero y fácil de leer y escribir. Es una alternativa al uso de XML y se utiliza ampliamente en aplicaciones web, especialmente en el desarrollo de APIs REST. Algunos de los conceptos más importantes de JSON incluyen:

Valores: los valores en JSON pueden ser números, cadenas, objetos, matrices, valores verdaderos y falsos y valores nulos. Por ejemplo:

```
{
  "name": "John Doe",
  "age": 30,
  "isMarried": true,
  "hobbies": ["reading", "traveling"],
  "address": null
}
```

Objetos: los objetos en JSON están compuestos por pares clave-valor. Cada clave es una cadena y cada valor puede ser cualquier tipo de valor en JSON. Por ejemplo:

```
{
  "name": "John Doe",
  "age": 30,
  "isMarried": true
}
```

Matrices: las matrices en JSON son una lista ordenada de valores. Por ejemplo:

```
["apple", "banana", "cherry"]
```

Anidamiento: los objetos y matrices en JSON pueden anidarse mutuamente. Por ejemplo:

```
{
  "person": {
    "name": "John Doe",
    "age": 30
  },
  "hobbies": ["reading", "traveling"]
}
```

Formato: el formato de JSON es fácil de leer y escribir y se utiliza comúnmente en aplicaciones web para el intercambio de datos entre el cliente y el servidor.

## Usos ##

 Se puede usar en JavaScript para parsear y manipular datos JSON. Aquí hay un ejemplo de cómo leer un archivo JSON en JavaScript y acceder a sus datos:

```
// Supongamos que tenemos un archivo JSON llamado "datos.json" con el siguiente contenido:
// {
//   "nombre": "Juan",
//   "edad": 30,
//   "direccion": {
//     "calle": "Calle 123",
//     "ciudad": "Ciudad A"
//   }
// }

// Primero, debemos cargar el archivo JSON en nuestro código JavaScript
var xhr = new XMLHttpRequest();
xhr.open("GET", "datos.json", true);
xhr.onreadystatechange = function() {
  if (xhr.readyState === 4 && xhr.status === 200) {
    // Cuando la respuesta esté lista, parseamos el contenido como JSON
    var datos = JSON.parse(xhr.responseText);
    console.log("Nombre: " + datos.nombre);
    console.log("Edad: " + datos.edad);
    console.log("Dirección: " + datos.direccion.calle + ", " + datos.direccion.ciudad);
  }
};
xhr.send();
```

En este ejemplo, usamos XMLHttpRequest para hacer una solicitud HTTP GET a un archivo JSON. Luego, usamos JSON.parse para parsear el contenido de la respuesta como un objeto JavaScript y acceder a sus datos mediante notación de punto.

## JSON en Java ## 

La librería más comúnmente usada para manejar JSON en Java es Gson. Es una librería open source desarrollada por Google que permite fácilmente convertir objetos Java en formato JSON y viceversa.

Ejemplo de uso de Gson para convertir un objeto Java en formato JSON:

```
import com.google.gson.Gson;

public class Main {
    public static void main(String[] args) {
        // Crear objeto Java
        Student student = new Student("John", "Doe", 23);

        // Convertir objeto Java en formato JSON
        Gson gson = new Gson();
        String json = gson.toJson(student);

        // Imprimir formato JSON
        System.out.println(json);
    }
}

class Student {
    private String firstName;
    private String lastName;
    private int age;

    public Student(String firstName, String lastName, int age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}
```

Ejemplo de uso de Gson para convertir formato JSON en objeto Java:

```
import com.google.gson.Gson;

public class Main {
    public static void main(String[] args) {
        // Formato JSON
        String json = "{\"firstName\":\"John\",\"lastName\":\"Doe\",\"age\":23}";

        // Convertir formato JSON en objeto Java
        Gson gson = new Gson();
        Student student = gson.fromJson(json, Student.class);

        // Imprimir objeto Java
        System.out.println(student.firstName + " " + student.lastName + " " + student.age);
    }
}

class Student {
    private String firstName;
    private String lastName;
    private int age;
}
```
