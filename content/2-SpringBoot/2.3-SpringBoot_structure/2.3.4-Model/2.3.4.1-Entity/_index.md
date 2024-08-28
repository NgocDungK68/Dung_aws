---
title : "Entity"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.3.4.1 </b> "
---

#### Concept
**Entity** represents the data objects in your application.

In Spring Boot, classes in this layer are often mapped to tables in database, and they contain fields that represent columns in the table.

#### Role
- **Representing data structure**: Each Entity class represents a table in the database, and the class's field correspond to columns in the table.
- Entity class objects are used to store and transmit data between application layers.

#### Example of Entity class
``` java
@AllArgsConstructor
@NoArgsConstructor
@Data
@Entity    // marks that this class is an entity mapped to a table in the database
public class Product {
    @Id    // Mark that this field is primary key
    @GeneratedValue(strategy = GenerationType.IDENTITY)   // generate value automatically
    private Long productId;

    private String name;

    private Double price;

    private String description;

    private Integer quantity;

    private Long categoryId;
}
```

Add **lombok** dependency to use **@AllArgsConstructor**, **@NoArgsConstrutor**, **@Data**