# Java DAO #

## POJO ##

POJO es el acrónimo de Plain Old Java Object. Es un término utilizado para describir un objeto de Java estándar que no tiene ninguna dependencia ni implementa ninguna interfaz específica. Es decir, una clase Java que no tiene ninguna anotación especial ni ninguna dependencia de un framework o librería específica. Los POJO son simples, fáciles de entender y de usar, y pueden ser utilizados para representar cualquier cosa en una aplicación Java.

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

http://acodigo.blogspot.com/2016/03/data-access-object-dao-con-jdbc.html

https://javajhon.blogspot.com/2019/10/dao.html

## Un ejemplo ##

POJO

```
// el pojo PRESTAMOS sólo nos sirve para almacenar valores de la base de datos
// Es como un 'pack' donde yo meto toda la información de un registro
public class Prestamos {
	// Lo importante son las propiedades, porque en un POJO el resto de cosas
	// Se generan automáticamente
	private int idprestamos;
	private String nombre;
	private String titulo;
	private Date fecha;
	
	
	@Override
	public String toString() {
		return "Prestamos [idprestamos=" + idprestamos + ", nombre=" + nombre + ", titulo=" + titulo + ", fecha="
				+ fecha + "]";
	}
	
	public Prestamos(int idprestamos, String nombre, String titulo, Date fecha) {
		super();
		this.idprestamos = idprestamos;
		this.nombre = nombre;
		
		this.titulo = titulo;
		this.fecha = fecha;
	}
	/**
	 * @return the idprestamos
	 */
	public int getIdprestamos() {
		return idprestamos;
	}
	/**
	 * @param idprestamos the idprestamos to set
	 */
	public void setIdprestamos(int idprestamos) {
		this.idprestamos = idprestamos;
	}
	/**
	 * @return the nombre
	 */
	public String getNombre() {
		return nombre;
	}
	/**
	 * @param nombre the nombre to set
	 */
	public void setNombre(String nombre) {
		this.nombre = nombre;
	}
	/**
	 * @return the titulo
	 */
	public String getTitulo() {
		return titulo;
	}
	/**
	 * @param titulo the titulo to set
	 */
	public void setTitulo(String titulo) {
		this.titulo = titulo;
	}
	/**
	 * @return the fecha
	 */
	public Date getFecha() {
		return fecha;
	}
	/**
	 * @param fecha the fecha to set
	 */
	public void setFecha(Date fecha) {
		this.fecha = fecha;
	}
	
	
	
}
```

DAO

```
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.ArrayList;
import java.util.List;

public class PrestamosDAO {

	// En esta variable almacenamos la conexión a la base de datos
	private Connection con;

	public PrestamosDAO() {
		try {
			// Esta línea registra el driver
			Class.forName("com.mysql.cj.jdbc.Driver");
			// Aquí creamos la conexión con:
			// driver: jdbc:mysql
			// url del servidor: localhost
			// Puerto del servidor: 3306
			// Base de datos: prestamos
			// Usuario: root
			// Contraseña: ""
			con = DriverManager.getConnection("jdbc:mysql://localhost:3306/prestamos", "root", "");

		} catch (Exception ex) {
			System.out.println(ex);
		}
	}

	/**
	 * Paso al método el id del préstamo que quiero obtener Me devuelve un POJO que
	 * almacena los datos del registro de la base de datos
	 * 
	 * @param id del registro de la base de datos
	 * @return Prestamos (pojo con los datos)
	 */
	public Prestamos getPrestamo(int id) {
		try {

			// Ir a la base de datos, recuperar el registro que tenga el id
			// Meterlo dentro de un POJO y devolverlo

			// Me creo la sentencia sql que recupera un préstamo con un id
			// Y le pongo un parámetro que será el id. Se representa con un ?
			String sql = "select * from prestamos where idprestamos=?";

			// Una vez tengo el sql me creo la sentencia preparada
			PreparedStatement stmt = con.prepareStatement(sql);

			// Poniendo en el primer parámetro el valor que me están pasando del id
			stmt.setInt(1, id);

			// Recuperamos los resultados dentro de un ResultSet
			ResultSet rs = stmt.executeQuery();

			// El resultset NO COGE todos los registros del select y los tiene como en un
			// array
			// El resultset es como si fuera un puntero, una flecha que nos apunta al primer
			// Registro del select. Para recuperar hay que usar next
			if (rs.next()) {
				// Si hemos podido obtener un registro en rs tenemos todos los datos
				// del registro de la base de datos. ¿Cómo? con rs.get del tipo y nombre
				// de la columna. Ej. rs.getInt(1) o rs.getInt("idprestamos")

				// ¿Qué hago con estos datos? Empaquetarlos dentro de un POJO para poder
				// devolverlos
				Prestamos resultado = new Prestamos(rs.getInt("idprestamos"), rs.getString("nombre"),
						rs.getString("titulo"), rs.getDate("fecha"));

				return resultado;

			} else {
				return null;
			}

		} catch (Exception ex) {
			System.out.println(ex);
			return null;
		}
	}

	public List<Prestamos> getPrestamos() {
		try {

			String sql = "select * from prestamos";

			PreparedStatement stmt = con.prepareStatement(sql);

			ResultSet rs = stmt.executeQuery();

			// Para almacenar todos los registros tengo que crear un arraylist
			List<Prestamos> resultado = new ArrayList<Prestamos>();

			// En esta ocasión no tengo un if porque son varios registros.
			// Tengo que hacer un bucle hasta que no haya registros o lo que es lo mismo
			// MIENTRAS tengamos registros vamos recorriendo
			while (rs.next()) {
				Prestamos elemento = new Prestamos(rs.getInt("idprestamos"), rs.getString("nombre"),
						rs.getString("titulo"), rs.getDate("fecha"));
				resultado.add(elemento);
			}
			return resultado;

		} catch (Exception ex) {
			System.out.println(ex);
			return null;
		}

	}

	public int addPrestamo(Prestamos prestamo) {
		try {

			// Igual que en los métodos anteriores tengo que poner el sql
			// De lo que quiero hacer. En este caso es un insert y... tengo tres parámetros
			String sql="insert into prestamos (nombre,titulo,fecha) values (?,?,?)";
			
			PreparedStatement stmt = con.prepareStatement(sql);

			// Tengo que pasar los parámetros
			stmt.setString(1,prestamo.getNombre() );
			stmt.setString(2, prestamo.getTitulo());
			stmt.setDate(3, prestamo.getFecha());
			
			// Utilizo executeUpdate porque modifico los datos, no obtengo resultados
			// Devuelvo lo que me devuelve el método que son el número de filas afectadas
			return stmt.executeUpdate();
			
		} catch (Exception ex) {
			System.out.println(ex);
			return 0;
		}

	}
	
	public int deletePrestamo(int id) {
		try {

			// Igual que en los métodos anteriores tengo que poner el sql
			// De lo que quiero hacer. En este caso es un delete y... tengo un parámetro
			String sql="delete from prestamos where idprestamos=?";
			
			PreparedStatement stmt = con.prepareStatement(sql);

			// Tengo que pasar los parámetros
			stmt.setInt(1, id);
			
			// Utilizo executeUpdate porque modifico los datos, no obtengo resultados
			// Devuelvo lo que me devuelve el método que son el número de filas afectadas
			return stmt.executeUpdate();
			
		} catch (Exception ex) {
			System.out.println(ex);
			return 0;
		}

	}
	
	public int updatePrestamo(Prestamos prestamo) {
		try {

			// Igual que en los métodos anteriores tengo que poner el sql
			// De lo que quiero hacer. En este caso es un update y... tengo cuatro parámetros
			String sql="update prestamos set nombre=?,titulo=?,fecha=? where idprestamos=?";
			
			PreparedStatement stmt = con.prepareStatement(sql);

			// Tengo que pasar los parámetros
			stmt.setString(1,prestamo.getNombre() );
			stmt.setString(2, prestamo.getTitulo());
			stmt.setDate(3, prestamo.getFecha());
			stmt.setInt(4, prestamo.getIdprestamos());
			
			// Utilizo executeUpdate porque modifico los datos, no obtengo resultados
			// Devuelvo lo que me devuelve el método que son el número de filas afectadas
			return stmt.executeUpdate();
			
		} catch (Exception ex) {
			System.out.println(ex);
			return 0;
		}

	}
	
	
}
```
