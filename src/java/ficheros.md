# Ficheros en Java  #

## Introducción ##

Java proporciona varias clases para trabajar con archivos y flujos de datos. A continuación se describen algunas de las clases más comunes:

File: La clase File se utiliza para trabajar con archivos y directorios en el sistema de archivos. Con esta clase, se pueden crear, eliminar, renombrar y verificar la existencia de archivos y directorios. Ejemplo:

```
File file = new File("example.txt");
if (file.exists()) {
    System.out.println("El archivo existe");
} else {
    System.out.println("El archivo no existe");
}
```

FileInputStream: La clase FileInputStream se utiliza para leer datos de un archivo. Los datos se leen en forma de bytes. Ejemplo:

```
try (FileInputStream inputStream = new FileInputStream("example.txt")) {
    int data = inputStream.read();
    while (data != -1) {
        System.out.print((char) data);
        data = inputStream.read();
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

FileOutputStream: La clase FileOutputStream se utiliza para escribir datos en un archivo. Los datos se escriben en forma de bytes. Ejemplo:

```
try (FileOutputStream outputStream = new FileOutputStream("example.txt")) {
    String message = "Hello World!";
    outputStream.write(message.getBytes());
} catch (IOException e) {
    e.printStackTrace();
}
```

### File ###

Algunos de los métodos más comunes de la clase File en Java son:

    createNewFile(): Este método se utiliza para crear un nuevo archivo vacío en el sistema de archivos. Ejemplo:

```
File file = new File("example.txt");
if (!file.exists()) {
    try {
        file.createNewFile();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

    delete(): Este método se utiliza para eliminar un archivo o directorio del sistema de archivos. Ejemplo:

```
File file = new File("example.txt");
if (file.exists()) {
    file.delete();
}
```

    mkdir(): Este método se utiliza para crear un nuevo directorio en el sistema de archivos. Ejemplo:

```
File directory = new File("example");
if (!directory.exists()) {
    directory.mkdir();
}
```

    list(): Este método se utiliza para obtener una lista de los archivos y directorios contenidos en un directorio. Ejemplo:

```
File directory = new File("example");
if (directory.isDirectory()) {
    String[] files = directory.list();
    for (String file : files) {
        System.out.println(file);
    }
}
```

    renameTo(File dest): Este método se utiliza para cambiar el nombre de un archivo o directorio. Ejemplo:

```
File file = new File("example.txt");
File newFile = new File("newExample.txt");
if (file.exists()) {
    file.renameTo(newFile);
}
```

    length(): Este método se utiliza para obtener el tamaño de un archivo en bytes. Ejemplo:

```
File file = new File("example.txt");
if (file.exists()) {
    long size = file.length();
    System.out.println("Tamaño del archivo: " + size + " bytes");
}
```

Aquí tienes un ejemplo de un programa en Java que utiliza la clase File para recorrer todos los archivos de un directorio especificado:

```
import java.io.File;

public class FileExplorer {
    public static void main(String[] args) {
        // Directorio a explorar
        File directory = new File("/path/to/directory");
        // Verifica que el directorio existe y es un directorio
        if (directory.exists() && directory.isDirectory()) {
            // Obtiene una lista de los archivos y directorios contenidos en el directorio
            File[] files = directory.listFiles();
            // Recorre cada archivo o directorio
            for (File file : files) {
                if (file.isFile()) {
                    // Si es un archivo, imprime su nombre
                    System.out.println(file.getName());
                } else if (file.isDirectory()) {
                    // Si es un directorio, llama recursivamente al método
                    exploreDirectory(file);
                }
            }
        } else {
            System.out.println("El directorio especificado no existe o no es un directorio");
        }
    }

    public static void exploreDirectory(File directory) {
        // Obtiene una lista de los archivos y directorios contenidos en el directorio
        File[] files = directory.listFiles();
        // Recorre cada archivo o directorio
        for (File file : files) {
            if (file.isFile()) {
                // Si es un archivo, imprime su nombre
                System.out.println(file.getName());
            } else if (file.isDirectory()) {
                // Si es un directorio, llama recursivamente al método
                exploreDirectory(file);
            }
        }
    }
}
```

Este programa utiliza un método recursivo llamado "exploreDirectory" para recorrer todos los archivos y subdirectorios dentro del directorio especificado. El método toma un objeto File como argumento y utiliza el método "listFiles()" para obtener una lista de los archivos y directorios contenidos en el directorio. Luego, el método recorre cada archivo o directorio utilizando un bucle for y verifica si es un archivo o un directorio utilizando los metodos isFile() y isDirectory(). Si es un archivo imprime su nombre y si es un directorio llama de nuevo al metodo de manera recursiva. Este programa se puede refactorizar para hacerlo más eficiente ¿Te animas?

Es importante recordar que para utilizar estos métodos se deben manejar las excepciones correspondientes ya que algunos de ellos pueden lanzar excepciones de tipo IOException.

### Leer archivos de texto ###

La mejor manera de leer un archivo de texto en Java y procesar su contenido depende de las necesidades específicas del programa y del tamaño del archivo. Sin embargo, aquí te presento algunas opciones comunes:

Utilizando la clase FileReader y BufferedReader: Esta es una forma básica de leer un archivo de texto caracter a caracter o línea a línea. Ejemplo:

```
FileReader fileReader = new FileReader("example.txt");
BufferedReader bufferedReader = new BufferedReader(fileReader);
String line;
while ((line = bufferedReader.readLine()) != null) {
    // Procesar cada línea
    System.out.println(line);
}
bufferedReader.close();
```

    Utilizando la clase Scanner: Esta clase proporciona una forma fácil de leer un archivo de texto utilizando métodos como nextLine(), nextInt(), etc. Ejemplo:

```
Scanner scanner = new Scanner(new File("example.txt"));
while (scanner.hasNextLine()) {
    // Procesar cada línea
    String line = scanner.nextLine();
    System.out.println(line);
}
scanner.close();
```

    Utilizando la clase Files de Java 7 o superior: Esta clase proporciona una forma simple de leer un archivo completo en una sola línea de código, convirtiéndolo en una lista de líneas, que pueden ser procesadas de manera sencilla. Ejemplo:

```
List<String> lines = Files.readAllLines(Paths.get("example.txt"));
for (String line : lines) {
    // Procesar cada línea
    System.out.println(line);
}
```

Utilizando la clase Stream: Java 8 introdujo una nueva forma de procesar archivos de texto, utilizando streams. Esto permite procesar un archivo linea por linea de manera eficiente, y se pueden aplicar operaciones intermedias y finales. Ejemplo:

```
try (Stream<String> stream = Files.lines(Paths.get("example.txt"))) {
    stream.forEach(line -> System.out.println(line));
} catch (IOException e) {
    e.printStackTrace();
}
```

Cualquiera de estas opciones es una buena forma de leer un archivo de texto en Java y procesar su contenido. La elección dependerá de las necesidades específicas de tu programa y de tu preferencia personal.

### Escribir texto en un archivo ###

Imaginemos que tenemos un ArrayList de cadenas y queremos guardarlo en un archivo de texto. Aquí te presento algunas opciones comunes:

Utilizando la clase FileWriter y BufferedWriter: Esta es una forma básica de escribir un archivo de texto caracter a caracter o línea a línea. Ejemplo:

```
FileWriter fileWriter = new FileWriter("example.txt");
BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);
for (String line : arrayList) {
    bufferedWriter.write(line);
    bufferedWriter.newLine();
}
bufferedWriter.close();
```

Utilizando la clase PrintWriter: Esta clase proporciona una forma fácil de escribir un archivo de texto utilizando métodos como println(), print(), etc. Ejemplo:

```
PrintWriter writer = new PrintWriter("example.txt", "UTF-8");
for (String line : arrayList) {
    writer.println(line);
}
writer.close();
```

Utilizando la clase Files de Java 7: Esta clase proporciona una forma fácil de escribir un ArrayList de Strings en un archivo de texto en una sola línea de código. Ejemplo:

```
Files.write(Paths.get("example.txt"), arrayList, StandardCharsets.UTF_8);
```

Utilizando la clase Stream de Java 8: Esta clase proporciona una forma eficiente de escribir un ArrayList de Strings en un archivo de texto, utilizando operaciones intermedias y finales. Ejemplo:

```
try (BufferedWriter writer = Files.newBufferedWriter(Paths.get("example.txt"))) {
    arrayList.stream().forEach(s -> {
        try {
            writer.write(s);
            writer.newLine();
        } catch (IOException e) {
            e.printStackTrace();
        }
    });
} catch (IOException e) {
    e.printStackTrace();
}
```

https://www.tutorialspoint.com/java/java_files_io.htm

https://www.javatpoint.com/java-fileoutputstream-class

https://www.w3schools.com/java/java_files.asp)
