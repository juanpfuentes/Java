# Excepciones en Java  #

## Introducción ##

En Java, las excepciones son eventos que se producen en tiempo de ejecución que pueden interrumpir el flujo normal del programa. Se utilizan para manejar situaciones anómalas, como errores de entrada/salida, errores de red, errores de memoria, etc.

Java proporciona varios mecanismos para manejar excepciones, incluyendo:

try-catch: El bloque try-catch se utiliza para capturar excepciones. El código que puede lanzar una excepción se coloca dentro del bloque try, y el código que maneja la excepción se coloca dentro del bloque catch. Ejemplo:

```
try {
    // Código que puede lanzar una excepción
    int result = 1 / 0;
} catch (ArithmeticException e) {
    // Código que maneja la excepción
    System.out.println("No se puede dividir por cero!");
}
```

try-catch-finally: El bloque try-catch-finally se utiliza para capturar excepciones y especificar código que debe ejecutarse independientemente de si se produjo una excepción o no. Ejemplo:

```
try {
    // Código que puede lanzar una excepción
    int result = 1 / 0;
} catch (ArithmeticException e) {
    // Código que maneja la excepción
    System.out.println("No se puede dividir por cero!");
} finally {
    // Código que se ejecuta siempre
    System.out.println("Código ejecutado independientemente de si se produjo una excepción o no");
}
```

throw: El comando throw se utiliza para lanzar una excepción manualmente. Ejemplo:

```
if (num < 0) {
    throw new IllegalArgumentException("El número debe ser mayor o igual a cero");
}
```

throws: La palabra clave "throws" en Java se utiliza en la declaración de un método para indicar que el método puede lanzar ciertas excepciones. Esto significa que el método no maneja la excepción dentro de su cuerpo, sino que la deja para que sea manejada por el código que llama al método.

Por ejemplo, el siguiente método "readFile" declara que puede lanzar una excepción de tipo IOException:

```
public void readFile() throws IOException {
    FileInputStream inputStream = new FileInputStream("example.txt");
    // ...
}
```

De esta manera, el código que llama al método "readFile" debe incluir un bloque try-catch para manejar la excepción de IOException:

```
try {
    readFile();
} catch (IOException e) {
    e.printStackTrace();
}
```

También se puede propagar la excepción hacia el método que llama al método actual, utilizando el mismo mecanismo de throws, el método que llama debe incluir un bloque try-catch para manejar la excepción o propagarla hacia el siguiente método y así sucesivamente hasta que se llegue a un método que maneje la excepción o se llegue al main.

Es importante tener en cuenta que utilizar throws para propagar excepciones puede hacer que el código sea menos legible y difícil de mantener, por lo que se recomienda utilizarlo sólo cuando sea absolutamente necesario.

https://www.javatpoint.com/try-catch-block