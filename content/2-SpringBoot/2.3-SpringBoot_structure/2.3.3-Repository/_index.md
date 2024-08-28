---
title : "Repository"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 2.3.3 </b> "
---

#### Introduction
**Repository** layer in Spring Boot is responsible for direct interaction with the database. It provides an abstraction layer to perform CRUD (Create, Read, Update, Delete) operations without having to write complex SQL statements.

This layer uses mechanisms provided by Spring Data JPA, making retrieving and storing data easier and more intuitive.

#### Role of repository layer
- **Data Access**: Repository is the class responsible for retrieving data from the database and storing data into the database.
- **Separate data retrieval logic from business logic**: By decoupling data operations from business logic (handled in the Service layer), the code becomes more maintainable and flexible.
- **Use Spring Data JPA features**: Repository layer takes advantage of Spring Data JPA such as querying based on method names, custom queries, and built-in CRUD methods.

#### Important Interfaces in the Repository Layer
Spring Data JPA provides several core interfaces that you can use to create repositories. These interfaces can be extended to suit application needs:
- **JpaRepository<T, ID>**:
    + This is the most popular interface, providing standard CRUD methods like **save**, **findById**, **findAll**, **deleteById**, etc.
    + **JpaRepository** also includes sorting and pagination methods.

- **CrudRepository<T, ID>**: The basic interface provides simple CRUD methods. JpaRepository is an extension of CrudRepository.
- **PagingAndSortingRepository<T, ID>**: Extends CrudRepository to add methods that support paging and sorting.

#### Create interface repository
The example below illustrates how to create an interface repository for the Product entity.
``` java
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {
    Product findByProductId(Long productId);
    List<Product> findAllByPriceBetween(Double minPrice, Double maxPrice);
}
```

**Explanation**:
- **@Repository**: Marks that this class is a Data Access Object (DAO) bean. This annotation not only helps Spring identify repository classes but also provides exception translation capabilities.
- **ProductRepository extends JpaRepository<Product, Long>**: **Product** is the entity and **Long** is the data type of the primary key.
- **findByProductId(Long productId)**: Define a method to find products by ID.
- **findAllByPriceBetween(Double minPrice, Double maxPrice)**: Define a method to find all products have the price between minPrice and maxPrice.

#### Custom Queries
In some cases, you can use **@Query** annotation to define custom SQL queries or JPQL queries.
``` java
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {
    @Query("from Product where price = :price")
    List<Product> getProductsByPrice(Double price);
}
```

#### Code in Service layer
``` java
@Service
public class ProductServiceImpl implements ProductService {
    @Autowired
    private ProductRepository productRepository;

    @Override
    public Product getByProductId(Long productId) {
        Optional<Product> product = productRepository.findByProductId(productId);
        if (product.isPresent()) {
            return product.get();
        }
        return null;
    }

    @Override
    public List<Product> getProductsByPriceRange(Double minPrice, Double maxPrice) {
        return this.productRepository.findAllByPriceBetween(minPrice, maxPrice);
    }
}
```

 