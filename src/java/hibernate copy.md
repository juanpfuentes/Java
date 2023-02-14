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

Estas son solo algunas de las anotaciones más comunes que se utilizan en Hibernate para crear una entidad. Hay muchas otras anotaciones disponibles que se pueden utilizar para personalizar y optimizar el mapeo entre entidades y tablas de la base de datos.

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

https://www.javatpoint.com/hibernate-tutorial

https://www.tutorialspoint.com/hibernate/index.htm

https://www.digitalocean.com/community/tutorials/hibernate-tutorial-for-beginners

https://www.w3schools.blog/hibernate-tutorial



