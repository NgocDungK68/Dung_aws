---
title : "Service"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.3.2 </b> "
---

**Service** layer is one of the core components of a Spring Boot application. This is where the application's business logic is located, separate from other layers such as Controller (HTTP request processing) and Repository (interaction with database).

**Service** layer helps ensure that the source code is well organized, easy to maintain, and reusable.

- **@Service**:
    + Used to mark a class as a service in Spring. This annotation helps Spring detect and manage the class as a bean.
    + Using **@Service** helps the service class to be injected into other components such as Controllers or other services through Dependency Injection

    ``` java
    @Service
    public class ProductService {
        // Business logic
    }

- **@Autowired**: Used to inject dependencies into **Service** class. Spring will automatically inject appropriate beans into fields or constructor marked with @Autowired.
    ``` java
    @Service
    public class ProductService {
        private final ProductRepository productRepository;

        @Autowired
        public ProductService(ProductRepository productRepository) {
            this.productRepository = productRepository;
        }

        // Business logic
    }
    ```

    ``` java
    @Service
    public class ProductService {
        @Autowired
        private ProductRepository productRepository;

        // Business logic
    }
    ```
___

### Create Interface in Service Layer

1. Introduction
- **Interface** in Service layer defines the methods that the service must implement, but does not provide details on how they are implemented. This helps to clearly separate between contract and implementation.
- **Interface** provides a way to decouple components within an application, allowing business logic to be easily changed or extended without affecting other components.

2. Directory structure:
    ```
    src/main/java/com/example/ProductManagerSystem/
    └── service/
        ├── ProductService.java
        ├── CartItemService.java
        └── impl/
            ├── ProductServiceImpl.java
            └── CartItemServiceImpl.java

    ```

- Package **service**: Contains interfaces that define necessary methods for the service layer and package **impl**.
- Package **impl**: Contains classes that implement interfaces in the service package.

3. Create interface
For example: Create the ProductService interface to define product-related methods.
    ``` java
    public interface ProductService {
        List<Product> getAllProducts();

        Product getProductById(Long productId);

        void insertProduct(Product product);

        void updateProduct(Long productId, Product product);

        void deleteProduct(Long productId);
    }
    ```

4. Implement interface in package **impl**
    ``` java
    @Service
    public class ProductServiceImpl implements ProductService {
        @Autowired
        private ProductRepository productRepository;

        @Override
        public List<Product> getAllProducts() {
            // Code
        }

        @Override
        public Product getProductById(Long productId) {
            // Code
        }

        @Override
        public void insertProduct(Product product) {
            // Code
        }

        @Override
        public void updateProduct(Long productId, Product product) {
            // Code
        }

        @Override
        public void deleteProduct(Long productId) throws BusinessException {
            // Code
        }
    }
    ```

5. Benefits of using separate Interfaces and Implementations
- **Extensibility**: When you need to add new features or change the implementation, you just need to create a new implementation class without affecting other components.
- **Easy testing**: Interfaces make it easier to create mock objects in unit testing, allowing you to test components independently.
- **Flexibility**: A service's implementation can be changed flexibly using Dependency Injection (DI) without changing the source code of the components that use the service.

6. Code in Controller class
    

