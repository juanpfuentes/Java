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

## Path ##

La clase Path en Java es una parte de la API de Java NIO 2 y se utiliza para trabajar con rutas de archivos y directorios. La clase Path se puede usar para manipular rutas de archivos y directorios independientemente de la sintaxis específica del sistema operativo.

A continuación, se presentan algunos ejemplos de cómo se puede utilizar la clase Path de Files en Java:

    Crear un objeto Path para una ruta de archivo:

```


Path path = Paths.get("C:/Users/Username/Documents/example.txt");
```

    Obtener la ruta absoluta de un archivo o directorio:

```
Path path = Paths.get("example.txt");
Path absolutePath = path.toAbsolutePath();
```

    Obtener la ruta de un archivo o directorio relativo a otro archivo o directorio:
```

Path base = Paths.get("C:/Users/Username/Documents");
Path relativePath = base.relativize(Paths.get("C:/Users/Username/Documents/example.txt"));
```
    Obtener el nombre de un archivo o directorio de una ruta:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
Path fileName = path.getFileName();
```

    Obtener el directorio padre de una ruta:
```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
Path parentDir = path.getParent();
```

    Combinar dos rutas para formar una nueva ruta:

```

Path basePath = Paths.get("C:/Users/Username/Documents");
Path filePath = Paths.get("example.txt");
Path combinedPath = basePath.resolve(filePath);
```

    Comprobar si una ruta representa un archivo o un directorio:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
boolean isFile = Files.isRegularFile(path);
boolean isDirectory = Files.isDirectory(path);
```

Estos son solo algunos ejemplos de cómo se puede utilizar la clase Path de Files en Java. La API de Java NIO 2 ofrece muchas más funciones para trabajar con rutas de archivos y directorios en Java.

## Files ##

La clase Files en Java proporciona varios métodos útiles para trabajar con archivos y directorios en el sistema de archivos. A continuación se presentan algunos ejemplos de cómo se puede utilizar la clase Files en Java:

    Comprobar si un archivo o directorio existe:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
boolean exists = Files.exists(path);
```

    Crear un nuevo archivo:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
Files.createFile(path);
```

    Crear un nuevo directorio:

```

Path path = Paths.get("C:/Users/Username/Documents/newdir");
Files.createDirectory(path);
```

    Copiar un archivo:

```

Path source = Paths.get("C:/Users/Username/Documents/example.txt");
Path target = Paths.get("C:/Users/Username/Documents/example-copy.txt");
Files.copy(source, target);
```

    Copiar un directorio y todo su contenido:

```

Path source = Paths.get("C:/Users/Username/Documents/old-dir");
Path target = Paths.get("C:/Users/Username/Documents/new-dir");
Files.copy(source, target, StandardCopyOption.REPLACE_EXISTING);
```

    Mover un archivo:

```

Path source = Paths.get("C:/Users/Username/Documents/example.txt");
Path target = Paths.get("C:/Users/Username/Documents/new-location/example.txt");
Files.move(source, target);
```

    Eliminar un archivo o directorio:

```
Path path = Paths.get("C:/Users/Username/Documents/example.txt");
Files.delete(path);
```

    La clase Files en Java también proporciona métodos para leer y escribir archivos de texto. A continuación se presentan algunos ejemplos de cómo se puede utilizar la clase Files para leer y escribir archivos de texto:

    Leer todo el contenido de un archivo de texto en una lista de cadenas:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
List<String> lines = Files.readAllLines(path, StandardCharsets.UTF_8);
```

    Leer todo el contenido de un archivo de texto en una cadena:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
String content = new String(Files.readAllBytes(path), StandardCharsets.UTF_8);
```

    Escribir una cadena en un archivo de texto:

```

Path path = Paths.get("C:/Users/Username/Documents/example.txt");
String content = "Esto es un ejemplo de texto que se va a escribir en un archivo.";
Files.write(path, content.getBytes());
```

    Escribir una lista de cadenas en un archivo de texto:

```
Path path = Paths.get("C:/Users/Username/Documents/example.txt");
List<String> lines = Arrays.asList("Primera línea", "Segunda línea", "Tercera línea");
Files.write(path, lines, StandardCharsets.UTF_8);
```

En todos estos ejemplos, se utiliza la clase Paths para obtener un objeto Path que representa el archivo que se va a leer o escribir. Luego, se utiliza el método apropiado de la clase Files para leer o escribir el archivo.

Es importante tener en cuenta que estos métodos no manejan explícitamente la codificación de caracteres. Por lo tanto, es importante especificar la codificación correcta al leer o escribir archivos de texto. En los ejemplos anteriores, se utiliza StandardCharsets.UTF_8 para especificar la codificación UTF-8.

https://www.tutorialspoint.com/java/java_files_io.htm

https://www.javatpoint.com/java-fileoutputstream-class

https://www.w3schools.com/java/java_files.asp)
