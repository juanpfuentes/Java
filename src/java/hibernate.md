# Java Hibernate #

## ORM ##

ORM (Object-Relational Mapping) es una técnica de programación que permite trabajar con bases de datos relacionales utilizando objetos de programación en lugar de utilizar consultas SQL. Esto significa que en lugar de escribir consultas SQL para interactuar con la base de datos, se utilizan objetos de programación para guardar, actualizar y recuperar datos de la base de datos.

Hibernate es una herramienta de ORM muy popular para Java. A continuación te muestro un ejemplo sencillo de cómo se puede utilizar Hibernate para guardar un objeto en una tabla de una base de datos:

java

```
//Clase de entidad
@Entity
@Table(name = "employee")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private String department;
    //getter y setters
}

//Clase de DAO
public class EmployeeDAO {
    private SessionFactory sessionFactory;

    public void saveEmployee(Employee employee) {
        Session session = sessionFactory.openSession();
        Transaction transaction = null;
        try {
            transaction = session.beginTransaction();
            session.save(employee);
            transaction.commit();
        } catch (HibernateException e) {
            if (transaction != null) {
                transaction.rollback();
            }
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}

//En alguna clase de negocio
public class EmployeeBusiness {
    private EmployeeDAO employeeDAO;
    public void addEmployee(String name, String department) {
        Employee employee = new Employee();
        employee.setName(name);
        employee.setDepartment(department);
        employeeDAO.saveEmployee(employee);
    }
}
```

En este ejemplo, estamos utilizando Hibernate para guardar un objeto "Employee" en una tabla de base de datos llamada "employee". La clase Employee está anotada con @Entity y @Table, lo que indica a Hibernate que esta clase representa una tabla en la base de datos. El atributo "id" está anotado con @Id y @GeneratedValue, lo que indica que este atributo es la clave primaria de la tabla y que su valor se generará automáticamente.

La clase EmployeeDAO es una clase de acceso a datos que utiliza Hibernate para guardar el objeto Employee en la base de datos. La clase EmployeeBusiness es una clase de negocio que utiliza la clase EmployeeDAO para guardar un nuevo empleado en la base de datos.

Este es solo un ejemplo básico de cómo utilizar Hibernate para guardar un objeto en una base de datos. 

## DAO ##

DAO (Data Access Object) es un patrón de diseño que se utiliza para separar la lógica de acceso a datos de la lógica de negocio de una aplicación. El objetivo es proporcionar una interfaz común para acceder a diferentes fuentes de datos, como bases de datos, archivos o servicios web.

Un ejemplo de cómo crear un DAO en Java sería:

Crear una interfaz DAO que define los métodos que se utilizarán para acceder a los datos:
java

```
public interface EmployeeDAO {
    public Employee getEmployeeById(int id);
    public void addEmployee(Employee employee);
    public void updateEmployee(Employee employee);
    public void deleteEmployee(int id);
}
```

Crear una clase DAO concreta que implementa la interfaz DAO y contiene la lógica de acceso a datos:
java


```
public class EmployeeDAOImpl implements EmployeeDAO {
    // lógica de acceso a datos para obtener, agregar, actualizar y eliminar empleados
}
```

Utilizar la clase DAO en la lógica de negocio de la aplicación:
java

```
public class EmployeeService {
    private EmployeeDAO employeeDAO;
    public EmployeeService() {
        employeeDAO = new EmployeeDAOImpl();
    }
    public Employee getEmployeeById(int id) {
        return employeeDAO.getEmployeeById(id);
    }
    // otros métodos de negocio
}
```

En este ejemplo, la clase EmployeeDAOImpl es la clase concreta que se encarga de acceder a los datos, mientras que la interfaz EmployeeDAO proporciona una interfaz común para todas las implementaciones de acceso a datos. Esto permite cambiar fácilmente la implementación de acceso a datos sin afectar a la lógica de negocio de la aplicación.

Otro ejemplo de como hacer DAO en Java con JPA(Java Persistence API) sería:

```
@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private String email;
    // getters and setters
}

public interface EmployeeDAO extends JpaRepository<Employee, Integer> {
}
```

En este caso estamos utilizando JPA y extender de la interfaz JpaRepository, esto nos permite tener acceso a métodos como save, findAll, findById, entre otros, sin tener que escribir la lógica de acceso a datos.

En ambos casos, se está separando la lógica de acceso a datos de la lógica de negocio.

## Anotaciones entidades ##

Algunas de las anotaciones más comunes que se utilizan en Hibernate son las siguientes:

@Entity: Anotación que se utiliza para especificar que una clase Java es una entidad y que debe ser mapeada a una tabla de la base de datos.

@Id: Anotación que se utiliza para especificar el atributo de la entidad que representa la clave primaria de la tabla.

@GeneratedValue: Anotación que se utiliza para especificar cómo se generará el valor de la clave primaria, por ejemplo, utilizando una secuencia de la base de datos.

@Column: Anotación que se utiliza para especificar el mapeo entre un atributo de la entidad y una columna de la tabla.

@Table: Anotación que se utiliza para especificar el mapeo entre una entidad y una tabla de la base de datos.

@OneToOne, @OneToMany, @ManyToOne, @ManyToMany: Anotaciones que se utilizan para especificar las relaciones entre entidades, por ejemplo, una relación de uno a uno, uno a muchos, muchos a uno o muchos a muchos.

@JoinColumn: Anotación que se utiliza para especificar la columna de unión entre dos entidades en una relación.

La anotación @Entity se utiliza para marcar una clase Java como una entidad, lo que significa que esta clase representa una tabla en una base de datos relacional. La anotación @Entity debe ser colocada encima de la declaración de la clase Java, como se muestra en el siguiente ejemplo:

```

@Entity
@Table(name = "employee")
public class Employee {
    ...
}
```

En este ejemplo, la clase Java Employee representa la tabla "employee" en una base de datos relacional. La anotación @Table se utiliza para especificar el nombre de la tabla en la base de datos que la clase Java debe representar.

La anotación @Column se utiliza para mapear un atributo de una clase Java a una columna de la tabla correspondiente en la base de datos. La anotación @Column debe ser colocada encima del atributo que se desea mapear, como se muestra en el siguiente ejemplo:

```
@Entity
@Table(name = "employee")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
 
    @Column(name = "first_name")
    private String firstName;
 
    @Column(name = "last_name")
    private String lastName;
 
    @Column(name = "email")
    private String email;
    ...
}
```

En este ejemplo, los atributos "firstName", "lastName" y "email" de la clase Java Employee están mapeados a las columnas correspondientes en la tabla "employee" de la base de datos. La anotación @Id se utiliza para marcar el atributo "id" como la clave primaria de la tabla, mientras que la anotación @GeneratedValue se utiliza para especificar cómo se generará el valor de la clave primaria automáticamente.

La anotación @OneToMany en Hibernate se utiliza para establecer una relación uno a muchos entre dos entidades. Esto significa que una entidad tiene una colección de otra entidad. La anotación @OneToMany se coloca encima de la propiedad de la colección en la entidad principal y se especifica la propiedad mappedBy en la anotación @OneToMany para indicar la propiedad en la entidad secundaria que mapea la relación.

Aquí hay un ejemplo de cómo usar la anotación @OneToMany en Hibernate:

Supongamos que tenemos dos entidades: Book y Author. Cada libro tiene un solo autor, pero cada autor puede escribir muchos libros. Por lo tanto, hay una relación uno a muchos entre las entidades Book y Author. La entidad Book tiene una propiedad author que es una instancia de la entidad Author.

La clase Book sería algo así:

```

@Entity
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToOne
    @JoinColumn(name = "author_id")
    private Author author;

    // getters and setters
}
```

La clase Author sería algo así:

```
@Entity
public class Author {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
    private List<Book> books = new ArrayList<>();

    // getters and setters
}
```

En este ejemplo, la entidad Book tiene una propiedad author que se mapea a la entidad Author mediante una relación ManyToOne. En la entidad Author, la propiedad books es una colección de libros que se mapea a la entidad Book mediante una relación OneToMany.

La propiedad mappedBy en la anotación @OneToMany se establece en "author" para indicar que la propiedad author en la entidad Book mapea esta relación. La propiedad cascade = CascadeType.ALL se utiliza para indicar que todas las operaciones de persistencia (guardar, actualizar, eliminar) realizadas en la entidad Author también se aplicarán a la colección de libros en la entidad Book.

Entonces, si quisieras agregar un nuevo libro para un autor en particular, simplemente crearías un nuevo objeto Book, lo establecerías en la colección books en el objeto Author correspondiente y guardarías el objeto Author. Hibernate se encargará de las relaciones entre las dos entidades. Por ejemplo:

```

Author author = new Author();
author.setName("J.K. Rowling");

Book book1 = new Book();
book1.setTitle("Harry Potter and the Philosopher's Stone");
book1.setAuthor(author);

Book book2 = new Book();
book2.setTitle("Harry Potter and the Chamber of Secrets");
book2.setAuthor(author);

author.getBooks().add(book1);
author.getBooks().add(book2);

session.save(author);
```

En este ejemplo, creamos un nuevo autor y dos libros, y los agregamos a la colección de libros en el autor. Luego guardamos el objeto Author en la base de datos. Hibernate automáticamente establecerá las claves externas y guardará los registros en las tablas correspondientes.

La anotación @ManyToMany en Hibernate se utiliza para establecer una relación muchos a muchos entre dos entidades. Esto significa que una entidad tiene una colección de otra entidad y viceversa. La anotación @ManyToMany se coloca en ambas entidades para indicar la relación.

Aquí hay un ejemplo de cómo usar la anotación @ManyToMany en Hibernate:

Supongamos que tenemos dos entidades: Book y Genre. Cada libro puede tener varios géneros, y cada género puede estar asociado con muchos libros. Por lo tanto, hay una relación muchos a muchos entre las entidades Book y Genre. La entidad Book tiene una colección de instancias de la entidad Genre, y la entidad Genre tiene una colección de instancias de la entidad Book.

La clase Book sería algo así:

```

@Entity
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToMany(cascade = { CascadeType.ALL })
    @JoinTable(
        name = "book_genre",
        joinColumns = { @JoinColumn(name = "book_id") },
        inverseJoinColumns = { @JoinColumn(name = "genre_id") }
    )
    private Set<Genre> genres = new HashSet<>();

    // getters and setters
}
```

La clase Genre sería algo así:

```
@Entity
public class Genre {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToMany(mappedBy = "genres")
    private Set<Book> books = new HashSet<>();

    // getters and setters
}
```

En este ejemplo, la entidad Book tiene una colección de géneros que se mapea a la entidad Genre mediante una relación ManyToMany. En la entidad Genre, la propiedad books es una colección de libros que se mapea a la entidad Book mediante una relación ManyToMany.

La anotación @JoinTable se utiliza para especificar la tabla de unión que se utiliza para mapear la relación ManyToMany. Las columnas joinColumns y inverseJoinColumns se utilizan para especificar las columnas que se utilizan para mapear la relación.

La propiedad mappedBy en la anotación @ManyToMany en la entidad Genre se establece en "genres" para indicar que la colección de géneros en la entidad Book mapea esta relación.

Entonces, si quisieras agregar un nuevo género para un libro en particular, simplemente crearías un nuevo objeto Genre, lo agregarías a la colección genres en el objeto Book correspondiente y guardarías el objeto Book. Hibernate se encargará de las relaciones entre las dos entidades. Por ejemplo:

```
Book book = new Book();
book.setTitle("The Lord of the Rings");

Genre genre1 = new Genre();
genre1.setName("Fantasy");

Genre genre2 = new Genre();
genre2.setName("Adventure");

book.getGenres().add(genre1);
book.getGenres().add(genre2);

genre1.getBooks().add(book);
genre2.getBooks().add(book);

session.save(book);
```

En este ejemplo, creamos un nuevo libro y dos géneros, y los agregamos a la colección de géneros en el libro. También agregamos el libro a la colección de libros en cada uno de los géneros correspondientes. Luego guardamos el objeto Book en la base de datos. Hibernate automáticamente establecerá las claves externas y guardará los registros en las tablas correspondientes.


## Crear sesión ##

Para crear una clase HibernateUtil que conecte con MySQL, puedes seguir los siguientes pasos:

Asegúrate de tener el controlador JDBC de MySQL en tu proyecto. Puedes descargarlo desde el sitio web de MySQL.

Crea una clase llamada "HibernateUtil" y agrega los siguientes imports:

```
import org.hibernate.SessionFactory;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
import org.hibernate.cfg.Configuration;
import org.hibernate.service.ServiceRegistry;
Dentro de la clase "HibernateUtil", crea un método estático llamado "getSessionFactory" que devuelva un objeto "SessionFactory". Este método debe contener la siguiente lógica:
java
Copy code
public static SessionFactory getSessionFactory() {
    Configuration configuration = new Configuration();
    configuration.configure("hibernate.cfg.xml");
    configuration.setProperty("hibernate.connection.driver_class", "com.mysql.jdbc.Driver");
    configuration.setProperty("hibernate.connection.url", "jdbc:mysql://localhost:3306/nombre_base_datos");
    configuration.setProperty("hibernate.connection.username", "nombre_usuario");
    configuration.setProperty("hibernate.connection.password", "contraseña_usuario");
    ServiceRegistry serviceRegistry = new StandardServiceRegistryBuilder()
            .applySettings(configuration.getProperties()).build();
    SessionFactory sessionFactory = configuration.buildSessionFactory(serviceRegistry);
    return sessionFactory;
}
```

Donde "nombre_base_datos", "nombre_usuario" y "contraseña_usuario" deben ser reemplazados por los datos correspondientes de tu base de datos MySQL.

Crea un archivo "hibernate.cfg.xml" en la carpeta "src/main/resources" de tu proyecto con la siguiente información:

```
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
    </session-factory>
</hibernate-configuration>
```

Ahora, puedes llamar al método "getSessionFactory" en tu código para obtener la sesión de Hibernate y realizar operaciones con la base de datos MySQL.

## Sesiones en Hibernate ##

En Hibernate, una sesión (Session) representa una conexión a la base de datos y proporciona una interfaz para trabajar con los objetos persistentes. Algunas de las principales características de una sesión en Hibernate son:

Transacciones: Las sesiones permiten trabajar con transacciones para asegurar la integridad de los datos y mantener la consistencia en la base de datos. Puedes iniciar una transacción, realizar operaciones de persistencia y, finalmente, confirmar o revertir la transacción.

Cache de primer nivel: La sesión de Hibernate mantiene una caché de primer nivel que almacena los objetos persistentes que se han recuperado de la base de datos. Esta caché evita realizar consultas adicionales a la base de datos cuando se accede a los objetos persistentes.

Operaciones CRUD: Las sesiones de Hibernate proporcionan una serie de métodos para realizar operaciones CRUD (crear, leer, actualizar y eliminar) en la base de datos a través de objetos persistentes.

Gestión del ciclo de vida de los objetos persistentes: La sesión es responsable de gestionar el ciclo de vida de los objetos persistentes, desde la creación hasta la eliminación. También proporciona métodos para actualizar, cargar y refrescar los objetos persistentes.

Control de concurrencia: La sesión de Hibernate controla la concurrencia en la base de datos, mediante la implementación de bloqueos de lectura y escritura. Esto garantiza que los cambios en los objetos persistentes se sincronicen correctamente en la base de datos.

En resumen, la sesión de Hibernate proporciona una interfaz para trabajar con los objetos persistentes y manejar la comunicación con la base de datos de manera eficiente y segura.

## CRUD en Sesión ##

Los comandos CRUD (Crear, Leer, Actualizar y Eliminar) en una sesión de Hibernate son:

Crear: Para crear un nuevo objeto persistente en Hibernate, primero debemos abrir una sesión y, a continuación, utilizar el método save() o persist() para guardar el objeto en la base de datos. El método save() devuelve el identificador del objeto persistente, mientras que el método persist() no devuelve nada. Ejemplo:

```
Session session = HibernateUtil.getSessionFactory().openSession();
Transaction tx = session.beginTransaction();

Person person = new Person("John", "Doe", 30);
Long personId = (Long) session.save(person); // or session.persist(person);

tx.commit();
session.close();
```

Leer: Para leer un objeto persistente en Hibernate, debemos abrir una sesión y utilizar el método get() o load() para obtener el objeto de la base de datos. El método get() devuelve el objeto persistente o null si no existe, mientras que el método load() devuelve una instancia del objeto persistente, aunque esta pueda estar inicialmente en estado "lazy". Ejemplo:

```
Session session = HibernateUtil.getSessionFactory().openSession();
Transaction tx = session.beginTransaction();

Person person = (Person) session.get(Person.class, 1L); // or session.load(Person.class, 1L);

tx.commit();
session.close();
```

Actualizar: Para actualizar un objeto persistente en Hibernate, primero debemos abrir una sesión y, a continuación, utilizar el método update() para realizar los cambios en el objeto. Si el objeto no existe en la base de datos, se lanzará una excepción. Ejemplo:

```
Session session = HibernateUtil.getSessionFactory().openSession();
Transaction tx = session.beginTransaction();

Person person = (Person) session.get(Person.class, 1L);
person.setAge(31);
session.update(person);

tx.commit();
session.close();
```

Eliminar: Para eliminar un objeto persistente en Hibernate, primero debemos abrir una sesión y, a continuación, utilizar el método delete() para eliminar el objeto de la base de datos. Si el objeto no existe en la base de datos, se lanzará una excepción. Ejemplo:

```
Session session = HibernateUtil.getSessionFactory().openSession();
Transaction tx = session.beginTransaction();

Person person = (Person) session.get(Person.class, 1L);
session.delete(person);

tx.commit();
session.close();
```

Estos son los principales comandos CRUD en una sesión de Hibernate.

```
import java.util.List; 
import java.util.Date;
import java.util.Iterator; 
 
import org.hibernate.HibernateException; 
import org.hibernate.Session; 
import org.hibernate.Transaction;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class ManageEmployee {
   private static SessionFactory factory; 
   public static void main(String[] args) {
      
      try {
         factory = new Configuration().configure().buildSessionFactory();
      } catch (Throwable ex) { 
         System.err.println("Failed to create sessionFactory object." + ex);
         throw new ExceptionInInitializerError(ex); 
      }
      
      ManageEmployee ME = new ManageEmployee();

      /* Add few employee records in database */
      Integer empID1 = ME.addEmployee("Zara", "Ali", 1000);
      Integer empID2 = ME.addEmployee("Daisy", "Das", 5000);
      Integer empID3 = ME.addEmployee("John", "Paul", 10000);

      /* List down all the employees */
      ME.listEmployees();

      /* Update employee's records */
      ME.updateEmployee(empID1, 5000);

      /* Delete an employee from the database */
      ME.deleteEmployee(empID2);

      /* List down new list of the employees */
      ME.listEmployees();
   }
   
   /* Method to CREATE an employee in the database */
   public Integer addEmployee(String fname, String lname, int salary){
      Session session = factory.openSession();
      Transaction tx = null;
      Integer employeeID = null;
      
      try {
         tx = session.beginTransaction();
         Employee employee = new Employee(fname, lname, salary);
         employeeID = (Integer) session.save(employee); 
         tx.commit();
      } catch (HibernateException e) {
         if (tx!=null) tx.rollback();
         e.printStackTrace(); 
      } finally {
         session.close(); 
      }
      return employeeID;
   }
   
   /* Method to  READ all the employees */
   public void listEmployees( ){
      Session session = factory.openSession();
      Transaction tx = null;
      
      try {
         tx = session.beginTransaction();
         List employees = session.createQuery("FROM Employee").list(); 
         for (Iterator iterator = employees.iterator(); iterator.hasNext();){
            Employee employee = (Employee) iterator.next(); 
            System.out.print("First Name: " + employee.getFirstName()); 
            System.out.print("  Last Name: " + employee.getLastName()); 
            System.out.println("  Salary: " + employee.getSalary()); 
         }
         tx.commit();
      } catch (HibernateException e) {
         if (tx!=null) tx.rollback();
         e.printStackTrace(); 
      } finally {
         session.close(); 
      }
   }
   
   /* Method to UPDATE salary for an employee */
   public void updateEmployee(Integer EmployeeID, int salary ){
      Session session = factory.openSession();
      Transaction tx = null;
      
      try {
         tx = session.beginTransaction();
         Employee employee = (Employee)session.get(Employee.class, EmployeeID); 
         employee.setSalary( salary );
		 session.update(employee); 
         tx.commit();
      } catch (HibernateException e) {
         if (tx!=null) tx.rollback();
         e.printStackTrace(); 
      } finally {
         session.close(); 
      }
   }
   
   /* Method to DELETE an employee from the records */
   public void deleteEmployee(Integer EmployeeID){
      Session session = factory.openSession();
      Transaction tx = null;
      
      try {
         tx = session.beginTransaction();
         Employee employee = (Employee)session.get(Employee.class, EmployeeID); 
         session.delete(employee); 
         tx.commit();
      } catch (HibernateException e) {
         if (tx!=null) tx.rollback();
         e.printStackTrace(); 
      } finally {
         session.close(); 
      }
   }
}
```

## Consultas ##

En Hibernate, podemos utilizar la API de Session para crear consultas personalizadas para recuperar datos de la base de datos. La forma más común de crear consultas personalizadas es a través del método createQuery de la interfaz Session.

La sintaxis básica para crear una consulta con createQuery es la siguiente:

```

Query query = session.createQuery("FROM MiEntidad WHERE propiedad = :valor");
query.setParameter("valor", valor);
List<MiEntidad> resultados = query.list();
```

En este ejemplo, estamos creando una consulta personalizada para la entidad MiEntidad, donde queremos recuperar todos los registros donde la propiedad es igual a un valor específico. Usamos la sintaxis de JPQL (Java Persistence Query Language) para definir la consulta, que es similar a SQL pero utiliza nombres de entidad y propiedad en lugar de nombres de tabla y columna.

La consulta personalizada se asigna a un objeto Query, que podemos usar para establecer parámetros de consulta y ejecutar la consulta. En este caso, estamos estableciendo un parámetro llamado "valor" y luego usando el método list para recuperar los resultados de la consulta como una lista de objetos MiEntidad.

Veamos algunos ejemplos más detallados de cómo utilizar createQuery en Hibernate:

Consulta básica

```
Query query = session.createQuery("FROM MiEntidad");
List<MiEntidad> resultados = query.list();
```

Este ejemplo muestra cómo recuperar todos los registros de la entidad MiEntidad sin ningún filtro específico. La consulta JPQL es simplemente "FROM MiEntidad".

Consulta con filtro de propiedad

```

Query query = session.createQuery("FROM MiEntidad WHERE propiedad = :valor");
query.setParameter("valor", valor);
List<MiEntidad> resultados = query.list();
```

En este ejemplo, estamos recuperando todos los registros de la entidad MiEntidad donde la propiedad es igual a un valor específico. La consulta JPQL es "FROM MiEntidad WHERE propiedad = :valor". Usamos el método setParameter para establecer el valor del parámetro "valor".

Consulta con ordenamiento

```
Query query = session.createQuery("FROM MiEntidad ORDER BY propiedad DESC");
List<MiEntidad> resultados = query.list();
```

Este ejemplo muestra cómo recuperar todos los registros de la entidad MiEntidad y ordenarlos por una propiedad específica en orden descendente. La consulta JPQL es "FROM MiEntidad ORDER BY propiedad DESC".

Consulta con paginación
```
Query query = session.createQuery("FROM MiEntidad");
query.setFirstResult(0);
query.setMaxResults(10);
List<MiEntidad> resultados = query.list();
```

En este ejemplo, estamos recuperando los primeros 10 registros de la entidad MiEntidad utilizando la paginación. La consulta JPQL es "FROM MiEntidad". Usamos los métodos setFirstResult y setMaxResults para especificar la posición inicial de los resultados y el número máximo de resultados a recuperar.

Consulta con agregación
```
Query query = session.createQuery("SELECT COUNT(*) FROM MiEntidad");
Long cantidad = (Long) query.uniqueResult();
```

Este ejemplo muestra cómo recuperar la cantidad de registros de la entidad MiEntidad utilizando una consulta de agregación. La consulta JPQL es "SELECT COUNT(*) FROM MiEntidad". Usamos el método uniqueResult para obtener el resultado de la consulta como un objeto Long.

https://www.javatpoint.com/hibernate-tutorial

https://www.tutorialspoint.com/hibernate/index.htm

https://www.digitalocean.com/community/tutorials/hibernate-tutorial-for-beginners

https://www.w3schools.blog/hibernate-tutorial