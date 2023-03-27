# Java Programación orientada a objetos #

## Spring ##

### JPA ###


JpaRepository y CrudRepository son interfaces proporcionadas por Spring Data JPA que se utilizan para simplificar el acceso a la base de datos en aplicaciones Java que utilizan JPA (Java Persistence API) para la capa de persistencia.

CrudRepository es la interfaz base que define los métodos CRUD básicos (Create, Read, Update y Delete) para operaciones de persistencia de datos. Esta interfaz proporciona métodos como save(), delete() y findById() que se utilizan para realizar operaciones básicas de CRUD.

Por otro lado, JpaRepository extiende CrudRepository y agrega más métodos para realizar operaciones avanzadas de consulta en la base de datos. Estos métodos incluyen métodos como findAll(), findByProperty() y deleteByProperty() que se utilizan para realizar consultas complejas en la base de datos.

En resumen, CrudRepository proporciona una funcionalidad básica de CRUD para la capa de persistencia, mientras que JpaRepository extiende esta funcionalidad para proporcionar una amplia variedad de operaciones de consulta.

Ejemplo CrudRepository:

Supongamos que tenemos una entidad llamada "Producto" que queremos guardar en una base de datos utilizando JPA. Podemos crear un repositorio utilizando CrudRepository de la siguiente manera:

```
import org.springframework.data.repository.CrudRepository;

public interface ProductoRepository extends CrudRepository<Producto, Long> {
}
```

Aquí, estamos extendiendo la interfaz CrudRepository y proporcionando la entidad "Producto" y el tipo de datos de su clave primaria (en este caso, Long).

Una vez que se ha creado el repositorio, podemos utilizar sus métodos para realizar operaciones básicas de CRUD en la base de datos. Por ejemplo, podemos guardar un nuevo producto utilizando el método save() de la siguiente manera:

```
Producto producto = new Producto();
producto.setNombre("Camiseta");
producto.setPrecio(20.0);
productoRepository.save(producto);
```

Ejemplo JpaRepository:

Supongamos que ahora queremos realizar una consulta más compleja en la base de datos para obtener todos los productos cuyo precio es mayor a $15. Podemos hacer esto utilizando JpaRepository de la siguiente manera:

```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByPrecioGreaterThan(Double precio);
}
```

Aquí, estamos extendiendo la interfaz JpaRepository y agregando un método personalizado llamado "findByPrecioGreaterThan" que toma un Double como parámetro y devuelve una lista de productos cuyo precio es mayor a ese valor.

Una vez que se ha creado el repositorio, podemos utilizar este método para obtener los productos deseados de la siguiente manera:

```
List<Producto> productos = productoRepository.findByPrecioGreaterThan(15.0);
```

En resumen, mientras que CrudRepository proporciona métodos básicos de CRUD para operaciones simples de persistencia de datos, JpaRepository extiende esta funcionalidad para proporcionar métodos de consulta avanzados para operaciones de búsqueda más complejas.

Buscar por varios campos:
```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByNombreAndPrecio(String nombre, Double precio);
}
```

Este método buscará todos los productos que tengan el nombre y precio dados.

Buscar por un campo que contenga una cadena:

```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByNombreContaining(String cadena);
}
```

Este método buscará todos los productos cuyo nombre contenga la cadena dada.

Buscar por un rango de valores:

```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByPrecioBetween(Double precioInicial, Double precioFinal);
}
```

Este método buscará todos los productos cuyo precio se encuentre entre los valores dados.

Buscar por un campo que comience con una cadena:

```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByNombreStartingWith(String cadena);
}
```

Este método buscará todos los productos cuyo nombre comience con la cadena dada.

Buscar por un campo que termine con una cadena:

```
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductoRepository extends JpaRepository<Producto, Long> {
    List<Producto> findByNombreEndingWith(String cadena);
}
```

Este método buscará todos los productos cuyo nombre termine con la cadena dada.

Estos son solo algunos ejemplos de los muchos métodos de consulta que se pueden utilizar en JpaRepository. La clave es entender que JpaRepository proporciona métodos de consulta avanzados que pueden ser utilizados para buscar y recuperar datos específicos de la base de datos de manera más eficiente.

https://docs.spring.io/spring-data/jpa/docs/current/api/org/springframework/data/jpa/repository/JpaRepository.html

https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#reference

