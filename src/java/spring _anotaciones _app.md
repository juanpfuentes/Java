# Java Programación orientada a objetos #

## Spring ##

### Anotaciones App ###

 Aquí hay algunas anotaciones comunes de Spring que se utilizan en las aplicaciones Spring Boot:

@SpringBootApplication: Esta es una anotación compuesta que combina varias anotaciones en una sola. Se utiliza para marcar la clase principal de una aplicación Spring Boot y le indica a Spring que la escanee en busca de componentes. La anotación incluye @Configuration, @EnableAutoConfiguration y @ComponentScan. Aquí hay un ejemplo:

```
@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

@RestController: Esta anotación se utiliza en una clase para indicar que se trata de un controlador REST que procesa solicitudes HTTP y devuelve respuestas HTTP en formato JSON o XML. Aquí hay un ejemplo:

```
@RestController
public class MyRestController {
    @GetMapping("/hello")
    public String hello() {
        return "Hello, World!";
    }
}
```

@Service: Esta anotación se utiliza para marcar una clase que proporciona servicios. Se utiliza para separar la lógica de negocio de la capa de controlador y la capa de persistencia. Aquí hay un ejemplo:

```
@Service
public class MyService {
    public void doSomething() {
        // código de lógica de negocio aquí
    }
}
```

@Repository: Esta anotación se utiliza para marcar una clase que proporciona acceso a la capa de persistencia. Se utiliza para separar la lógica de persistencia de la capa de controlador y la capa de servicios. Aquí hay un ejemplo:

```
@Repository
public class MyRepository {
    public List<MyEntity> findAll() {
        // código para buscar todas las entidades en la base de datos aquí
    }
}
```

@Autowired: Esta anotación se utiliza para inyectar una dependencia en una clase. Spring busca un objeto correspondiente en el contexto de la aplicación y lo proporciona al campo o al método marcado con esta anotación. Aquí hay un ejemplo:

```
@Service
public class MyService {
    private final MyRepository repository;

    @Autowired
    public MyService(MyRepository repository) {
        this.repository = repository;
    }

    // métodos de lógica de negocio que utilizan la dependencia aquí
}
```

Estas son solo algunas de las anotaciones comunes que se utilizan en las aplicaciones Spring Boot. 

La anotación @EnableJpaRepositories es una anotación de configuración de Spring que se utiliza para habilitar el soporte de Spring Data JPA en una aplicación Spring Boot.

Para utilizar Spring Data JPA en una aplicación Spring Boot, primero debes agregar la dependencia spring-boot-starter-data-jpa a tu archivo pom.xml o build.gradle. Una vez que se ha agregado la dependencia, puedes habilitar Spring Data JPA en tu aplicación agregando la anotación @EnableJpaRepositories a tu clase de configuración.

Por ejemplo, aquí hay una clase de configuración de ejemplo que habilita Spring Data JPA:

```
@Configuration
@EnableJpaRepositories(basePackages = "com.example.myapp.repositories")
public class JpaConfig {
    // Configuración adicional de JPA aquí
}
```

En este ejemplo, @EnableJpaRepositories habilita el soporte de Spring Data JPA en la aplicación y especifica el paquete base donde se encuentran los repositorios de Spring Data JPA.

Una vez habilitado Spring Data JPA, puedes crear interfaces de repositorio de Spring Data JPA para interactuar con tus entidades JPA. Por ejemplo, aquí hay una interfaz de repositorio de ejemplo para la entidad Book:

```
public interface BookRepository extends JpaRepository<Book, Long> {
    List<Book> findByTitleContaining(String title);
}
```

En este ejemplo, BookRepository extiende JpaRepository de Spring Data JPA y define un método personalizado findByTitleContaining para buscar libros por título. Spring Data JPA genera automáticamente la implementación de este método, lo que te permite interactuar con la base de datos de manera más fácil y sin tener que escribir código de SQL personalizado.

En resumen, la anotación @EnableJpaRepositories es una anotación de configuración de Spring que se utiliza para habilitar el soporte de Spring Data JPA en una aplicación Spring Boot. Una vez habilitado Spring Data JPA, puedes crear interfaces de repositorio de Spring Data JPA para interactuar con tus entidades JPA y realizar operaciones en la base de datos de manera más fácil y sin tener que escribir código de SQL personalizado.


La anotación @EnableJpaAuditing es una anotación de configuración de Spring que se utiliza para habilitar la funcionalidad de auditoría de JPA en una aplicación Spring Boot. La auditoría de JPA permite registrar automáticamente quién creó o modificó una entidad JPA y cuándo se realizó esa acción.

Para utilizar la funcionalidad de auditoría de JPA, primero debes agregar la dependencia spring-boot-starter-data-jpa a tu archivo pom.xml o build.gradle. Una vez que se ha agregado la dependencia, puedes habilitar la auditoría de JPA en tu aplicación agregando la anotación @EnableJpaAuditing a tu clase de configuración.

Por ejemplo, aquí hay una clase de configuración de ejemplo que habilita la auditoría de JPA y configura una entidad JPA para que utilice la funcionalidad de auditoría:

```
@Configuration
@EnableJpaAuditing
public class JpaConfig {

    @Bean
    public AuditorAware<String> auditorProvider() {
        // Configura el proveedor de auditoría que devuelve el nombre de usuario del usuario actualmente autenticado
        return new SpringSecurityAuditorAware();
    }
}
```

En este ejemplo, @EnableJpaAuditing habilita la auditoría de JPA en la aplicación y la clase JpaConfig proporciona la configuración adicional necesaria. La clase SpringSecurityAuditorAware es una implementación personalizada de la interfaz AuditorAware que devuelve el nombre de usuario del usuario actualmente autenticado.

Una vez que se ha habilitado la auditoría de JPA, puedes agregar las anotaciones @CreatedBy, @LastModifiedBy, @CreatedDate y @LastModifiedDate a tus entidades JPA para registrar quién creó o modificó la entidad y cuándo se realizó esa acción.

Por ejemplo, aquí hay una entidad de ejemplo que utiliza las anotaciones de auditoría de JPA:

```
@Entity
@Table(name = "books")
@EntityListeners(AuditingEntityListener.class)
public class Book {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String title;

    @CreatedBy
    @Column(nullable = false, updatable = false)
    private String createdBy;

    @LastModifiedBy
    @Column(nullable = false)
    private String lastModifiedBy;

    @CreatedDate
    @Column(nullable = false, updatable = false)
    private LocalDateTime createdDate;

    @LastModifiedDate
    @Column(nullable = false)
    private LocalDateTime lastModifiedDate;

    // constructores, getters y setters aquí
}
```

En este ejemplo, @EntityListeners(AuditingEntityListener.class) habilita la auditoría de JPA para la entidad Book. Las anotaciones @CreatedBy, @LastModifiedBy, @CreatedDate y @LastModifiedDate se utilizan para registrar quién creó o modificó la entidad y cuándo se realizó esa acción.

En resumen, la anotación @EnableJpaAuditing es una anotación de configuración de Spring que se utiliza para habilitar la funcionalidad de auditoría de JPA en una aplicación Spring Boot. Una vez habilitada la auditoría de JPA, puedes agregar las anotaciones de auditoría de JPA a tus entidades JPA para registrar quién creó o modificó la entidad