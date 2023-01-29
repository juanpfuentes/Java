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


https://www.javatpoint.com/hibernate-tutorial

https://www.tutorialspoint.com/hibernate/index.htm

https://www.digitalocean.com/community/tutorials/hibernate-tutorial-for-beginners

https://www.w3schools.blog/hibernate-tutorial