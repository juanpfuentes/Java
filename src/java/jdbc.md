# Java Bases de datos con JDBC #

## JDBC ##

### Conectividad ###

La conexión a una base de datos desde Java utilizando JDBC (Java Database Connectivity) se realiza mediante los siguientes pasos:

Importar las librerías necesarias: se deben importar las librerías JDBC correspondientes al driver de la base de datos que se va a utilizar. Ejemplo para conectarse a una base de datos MySQL:

```
import java.sql.DriverManager;
import java.sql.Connection;
```

Cargar el driver: se debe cargar el driver correspondiente a la base de datos que se va a utilizar. Ejemplo para cargar el driver de MySQL:

```
Class.forName("com.mysql.jdbc.Driver");
```

Establecer la conexión: se debe establecer la conexión utilizando el driver cargado anteriormente y los detalles de la conexión (URL, usuario y contraseña). Ejemplo para conectarse a una base de datos MySQL:

```
Connection con = DriverManager.getConnection("jdbc:mysql://host:port/dbname", "username", "password");
```

Realizar operaciones: una vez establecida la conexión, se pueden realizar operaciones en la base de datos (consultas, inserciones, actualizaciones, etc.) utilizando objetos como Statement o PreparedStatement. 

https://www.javatpoint.com/steps-to-connect-to-the-database-in-java

### Conexión ###

En Java, el interface java.sql.Connection es parte de la API JDBC (Java Database Connectivity) y proporciona una interfaz para establecer y gestionar conexiones a una base de datos. El objeto Connection es utilizado para realizar operaciones en la base de datos como ejecutar consultas, transacciones, etc.

Algunos de los métodos más comunes del interface Connection son:

createStatement(): Este método se utiliza para crear un objeto Statement, el cual se utiliza para ejecutar consultas en la base de datos. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM Employee");
```

prepareStatement(String sql): Este método se utiliza para crear un objeto PreparedStatement, el cual se utiliza para ejecutar consultas con parámetros. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
PreparedStatement pstmt = con.prepareStatement("SELECT * FROM Employee WHERE id = ?");
pstmt.setInt(1, 123);
ResultSet rs = pstmt.executeQuery();
```

setAutoCommit(boolean autoCommit): Este método se utiliza para establecer si las operaciones en la base de datos deben ser automáticamente confirmadas o no. Por defecto, el autoCommit está habilitado. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
con.setAutoCommit(false); // Deshabilitar el autoCommit
```

commit(): Este método se utiliza para confirmar las operaciones realizadas en la base de datos. Este método solo es necesario si el autoCommit está deshabilitado. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
con.setAutoCommit(false);
```

// Realizar operaciones en la base de datos

con.commit(); // Confirmar las operaciones

close(): Este método se utiliza para cerrar la conexión con la base de datos
	
Algunos ejemplos de cómo utilizar el interface Connection en Java son:

    Establecer una conexión a una base de datos MySQL:

```
try {
    Class.forName("com.mysql.jdbc.Driver");
    Connection con = DriverManager.getConnection("jdbc:mysql://host:port/dbname", "username", "password");
    System.out.println("Conexión establecida");
} catch (SQLException e) {
    System.out.println("Error al establecer conexión: " + e.getMessage());
} catch (ClassNotFoundException e) {
    System.out.println("Error al cargar el driver: " + e.getMessage());
}
```

    Realizar una consulta a una tabla de una base de datos y recorrer el resultado:

```
try {
    Connection con = DriverManager.getConnection(url, user, password);
    Statement stmt = con.createStatement();
    ResultSet rs = stmt.executeQuery("SELECT * FROM Employee");
    while (rs.next()) {
        System.out.println("ID: " + rs.getInt(1));
        System.out.println("Nombre: " + rs.getString(2));
        System.out.println("Cargo: " + rs.getString(3));
    }
    con.close();
} catch (SQLException e) {
    System.out.println("Error al realizar la consulta: " + e.getMessage());
}
```

https://www.javatpoint.com/Connection-interface

### Comandos ###

En Java, el interface java.sql.Statement es parte de la API JDBC (Java Database Connectivity) y proporciona una interfaz para ejecutar sentencias SQL en una base de datos. El objeto Statement se utiliza para realizar operaciones simples en una base de datos como ejecutar consultas, insertar, actualizar o eliminar registros.

Algunos de los métodos más comunes del interface Statement son:

    executeQuery(String sql): Este método se utiliza para ejecutar una consulta SELECT en la base de datos y devuelve un objeto ResultSet con el resultado de la consulta. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM Employee");
```

    executeUpdate(String sql): Este método se utiliza para ejecutar una sentencia SQL que modifica la base de datos (INSERT, UPDATE, DELETE) y devuelve el número de filas afectadas. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
int rowsAffected = stmt.executeUpdate("DELETE FROM Employee WHERE id = 123");
```

    getGeneratedKeys(): Este método se utiliza para obtener las claves generadas después de ejecutar una sentencia SQL de inserción. Ejemplo:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
stmt.executeUpdate("INSERT INTO Employee (name, job) VALUES ('John', 'Developer')", Statement.RETURN_GENERATED_KEYS);
ResultSet generatedKeys = stmt.getGeneratedKeys();
```

    close(): Este método se utiliza para cerrar el objeto Statement y liberar los recursos asociados. Es importante cerrar el objeto Statement una vez que ya no se utiliza. 



https://www.javatpoint.com/Statement-interface

### Manejar resultados ###

En Java, el interface java.sql.ResultSet es parte de la API JDBC (Java Database Connectivity) y proporciona una interfaz para acceder y recorrer el resultado de una consulta a una base de datos. El objeto ResultSet contiene un cursor que se mueve a través de los resultados de la consulta, permitiendo acceder a los valores de cada fila.

Algunos ejemplos de cómo utilizar el interface ResultSet en Java son:

    Recorrer un ResultSet y obtener los valores de cada columna:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM Employee");
while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
    String job = rs.getString("job");
    System.out.println("ID: " + id + ", Nombre: " + name + ", Cargo: " + job);
}
```

    Recorrer un ResultSet utilizando el índice de las columnas:

```
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM Employee");
while (rs.next()) {
    int id = rs.getInt(1);
    String name = rs.getString(2);
    String job = rs.getString(3);
    System.out.println("ID: " + id + ", Nombre: " + name + ", Cargo: " + job);
}
```

    getXXX(String columnName): Este conjunto de métodos es similar al anterior, pero en lugar de utilizar el índice de la columna, se utiliza el nombre de la columna. Ejemplo:

```
int id = rs.getInt("id");
String name = rs.getString("name");
String job = rs.getString("job");
```

https://www.javatpoint.com/ResultSet-interface

### Comandos preparados ###

En Java, el interface java.sql.PreparedStatement es una subclase de java.sql.Statement y proporciona una interfaz para ejecutar sentencias SQL precompiladas en una base de datos. El objeto PreparedStatement se utiliza para realizar operaciones más complejas en una base de datos, como ejecutar consultas con parámetros.

Algunos ejemplos de cómo utilizar PreparedStatement en Java son:

    Ejecutar una consulta SELECT con un parámetro:

```
String sql = "SELECT * FROM Employee WHERE id = ?";
PreparedStatement pstmt = con.prepareStatement(sql);
pstmt.setInt(1, 123);
ResultSet rs = pstmt.executeQuery();
while (rs.next()) {
    System.out.println("ID: " + rs.getInt("id"));
    System.out.println("Nombre: " + rs.getString("name"));
    System.out.println("Cargo: " + rs.getString("job"));
}
pstmt.close();
```

    Ejecutar una sentencia INSERT con varios parámetros:

```
String sql = "INSERT INTO Employee (name, job, salary) VALUES (?, ?, ?)";
PreparedStatement pstmt = con.prepareStatement(sql);
pstmt.setString(1, "John");
pstmt.setString(2, "Developer");
pstmt.setDouble(3, 50000);
pstmt.executeUpdate();
pstmt.close();
```

    Ejecutar una sentencia UPDATE con varios parámetros:

```
String sql = "UPDATE Employee SET salary = ? WHERE id = ? AND job = ?";
PreparedStatement pstmt = con.prepareStatement(sql);
pstmt.setDouble(1, 55000);
pstmt.setInt(2, 123);
pstmt.setString(3, "Developer");
pstmt.executeUpdate();
pstmt.close();
```

    Utilizar un PreparedStatement para ejecutar una transacción:

```
con.setAutoCommit(false);
String sql1 = "INSERT INTO Employee (name, job) VALUES (?, ?)";
PreparedStatement pstmt1 = con.prepareStatement(sql1);
pstmt1.setString(1, "John");
pstmt1.setString(2, "Developer");
pstmt1.executeUpdate();

String sql2 = "UPDATE Employee SET salary = ? WHERE name = ?";
PreparedStatement pstmt2 = con.prepareStatement(sql2);
pstmt2.setDouble(1, 55000);
pstmt2.setString(2, "John");
pstmt2.executeUpdate();
con.commit();
```

https://www.javatpoint.com/PreparedStatement-interface


