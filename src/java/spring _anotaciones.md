# Java Programación orientada a objetos #

## Spring ##

### Anotaciones ###

 continuación, te explico algunas de las anotaciones de entidades más comunes en Spring:

@Entity: Esta es la anotación principal que se utiliza para marcar una clase como una entidad de base de datos. La anotación @Entity se coloca en la parte superior de una clase que representa una tabla de base de datos. Aquí hay un ejemplo de cómo se puede utilizar @Entity en una clase de entidad:

```
@Entity
public class MyEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    
    // getters and setters
}
```

En este ejemplo, MyEntity está marcado como una entidad mediante la anotación @Entity. El campo id se marca como la clave principal de la entidad mediante la anotación @Id. La anotación @GeneratedValue se utiliza para generar automáticamente un valor para la clave principal.

@Table: Esta anotación se utiliza para especificar el nombre de la tabla de la base de datos que se corresponde con una entidad. Si no se especifica el nombre de la tabla, se utiliza el nombre de la clase como nombre de la tabla por defecto. Aquí hay un ejemplo de cómo se puede utilizar @Table en una clase de entidad:

```
@Entity
@Table(name = "my_table")
public class MyEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    
    // getters and setters
}
```

En este ejemplo, MyEntity está marcado como una entidad mediante la anotación @Entity. La anotación @Table se utiliza para especificar que la entidad se corresponde con la tabla "my_table".

@Column: Esta anotación se utiliza para especificar el nombre de una columna de base de datos que se corresponde con un campo de una entidad. Si no se especifica el nombre de la columna, se utiliza el nombre del campo como nombre de la columna por defecto. Aquí hay un ejemplo de cómo se puede utilizar @Column en una clase de entidad:

```
@Entity
public class MyEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "full_name")
    private String name;
    
    // getters and setters
}
```

En este ejemplo, MyEntity está marcado como una entidad mediante la anotación @Entity. El campo name se corresponde con la columna "full_name" en la tabla de la base de datos.

@ManyToOne y @OneToMany: Estas anotaciones se utilizan para especificar relaciones de uno a muchos entre entidades. @ManyToOne se coloca en el campo de la entidad secundaria, mientras que @OneToMany se coloca en el campo de la entidad principal. Aquí hay un ejemplo de cómo se pueden utilizar estas anotaciones:

```
@Entity
public class Order {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @OneToMany(mappedBy = "order")
    private List<OrderItem> orderItems;
    
    // getters and setters
}

@Entity
public class OrderItem {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToOne
    @JoinColumn(name = "order_id")
    private Order order;
    
    // getters and setters
}
```

En este ejemplo, Order tiene una relación de uno a muchos con OrderItem. 

@EntityListeners: Esta anotación se utiliza para especificar una o más clases que deben ser notificadas cuando ocurren eventos de ciclo de vida en una entidad. Por ejemplo, se puede utilizar @EntityListeners para enviar un correo electrónico cuando se crea o actualiza una entidad. La anotación se puede aplicar a una clase de entidad o a un campo individual de la entidad. Aquí hay un ejemplo de cómo se puede utilizar @EntityListeners en una clase de entidad:

```
@Entity
@EntityListeners(MyEntityListener.class)
public class MyEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    
    // getters and setters
}
```

En este ejemplo, MyEntity tiene un oyente (MyEntityListener.class) especificado mediante la anotación @EntityListeners. Cuando se producen eventos de ciclo de vida en MyEntity, el oyente correspondiente será notificado.

@JsonIgnoreProperties: Esta anotación se utiliza para ignorar propiedades específicas de una entidad durante la serialización y deserialización JSON. Por ejemplo, si una entidad tiene un campo que no se debe incluir en la representación JSON, se puede utilizar @JsonIgnoreProperties para omitir ese campo. Aquí hay un ejemplo de cómo se puede utilizar @JsonIgnoreProperties en una clase de entidad:

```
@Entity
public class MyEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    
    @JsonIgnoreProperties({"fieldToIgnore"})
    private String fieldToInclude;
    
    // getters and setters
}
```

En este ejemplo, MyEntity tiene un campo (fieldToInclude) que se debe incluir en la entidad pero se debe omitir en la representación JSON. Se utiliza @JsonIgnoreProperties para especificar que el campo fieldToIgnore debe ignorarse durante la serialización y deserialización JSON.

Espero que estos ejemplos te ayuden a entender cómo se pueden utilizar @EntityListeners y @JsonIgnoreProperties en Spring. 

A continuación, te mostraré algunas de las anotaciones de entidades más comunes en Spring:

@Entity: Esta es la anotación principal que se utiliza para marcar una clase como una entidad de persistencia. La anotación se aplica a la clase y se utiliza para indicar que la clase es una entidad que se puede almacenar en una base de datos.

@Id: Esta anotación se utiliza para marcar un campo o propiedad como la clave principal de la entidad.

@GeneratedValue: Esta anotación se utiliza para especificar cómo se debe generar el valor de la clave principal. Hay varias opciones disponibles, como GenerationType.AUTO, GenerationType.IDENTITY, GenerationType.SEQUENCE, entre otras.

@Column: Esta anotación se utiliza para especificar la columna de la tabla de la base de datos que se debe utilizar para almacenar el valor del campo o propiedad de la entidad.

@Table: Esta anotación se utiliza para especificar el nombre de la tabla de la base de datos que se debe utilizar para almacenar la entidad. Si no se especifica, se utilizará el nombre de la clase de entidad.

@Temporal: Esta anotación se utiliza para especificar cómo se debe mapear un campo o propiedad de fecha/hora a una columna de la base de datos. Hay varias opciones disponibles, como TemporalType.DATE, TemporalType.TIME, TemporalType.TIMESTAMP, entre otras.

@Transient: Esta anotación se utiliza para marcar un campo o propiedad como no persistente. Los campos o propiedades marcados como @Transient no se guardarán en la base de datos.

@ManyToOne: Esta anotación se utiliza para especificar una relación muchos-a-uno entre dos entidades.

@OneToMany: Esta anotación se utiliza para especificar una relación uno-a-muchos entre dos entidades.

@ManyToMany: Esta anotación se utiliza para especificar una relación muchos-a-muchos entre dos entidades.

@JoinTable: Esta anotación se utiliza para especificar la tabla de unión que se debe utilizar para almacenar una relación muchos-a-muchos.

@JoinColumn: Esta anotación se utiliza para especificar la columna de la tabla de la base de datos que se debe utilizar para unir dos tablas en una relación de muchos-a-uno o uno-a-muchos.