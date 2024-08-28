---
title : "Controller"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.3.1 </b> "
---

In Spring Boot, **Controller** layer is responsible for receiving and processing HTTP requests from the client.

**Controller** receives requests from users, implements the necessary logic (usually by calling methods from the **Service** layer), and returns the corresponding results (response).

This layer mainly handles HTTP GET, POST, PUT, DELETE, etc. requests.

In terms of code, **Controller** is a bean marked with `@Controller` or `@RestController`.
- **@Controller**:
    + Used to mark a class as a Spring MVC Controller.
    + This class is often used in traditional web applications, where controller methods return HTML pages.
- **@RestController**:
    + Inheriting from **@Controller** and **@ResponseBody**, **@RestController** is used for RESTful APIs, where data returns as JSON or XML instead of an HTML page.
    + **@RestController** automatically converts the Java object to JSON or XML and sends it as an HTTP response.

``` java 
@RestController
public class ProductController {
    // Inside Controller there will be many methods, each of which will map a specific request
}
```
____

### Controller Mapping
![Controller](/Dung_aws/images/2.1/0005.png)

- **@RequestMapping**: 
    + Used to map URL to processing methods in controller.
    + **@RequestMapping** can be applied at both the class and method levels, allowing you to specify base URL and specific URL for each action.
    
    ``` java
    @RestController
    @RequestMapping(path = "/api/products")
    public class ProductController {
        @RequestMapping(value = "/get", method = RequestMethod.GET)
        public Product getProduct() {
            // Code
        }
    }
    ```

- **@GetMapping**, **@PostMapping**, **@PutMapping**, **@DeleteMapping**:
    + These are specific annotations, corresponding to HTTP GET, POST, PUT, and DELETE requests.
    + These are short forms of **@RequestMapping(method = RequestMethod.GET/POST/PUT/DELETE)**.
    
    ``` java
    @RestController
    @RequestMapping(path = "/api/products")
    public class ProductController {
        @GetMapping("/get")
        public Product getProduct() {
            // Code
        }

        @PostMapping("/insert")
        public Product getProduct() {
            // Code
        }

        @PutMapping("/update")
        public Product getProduct() {
            // Code
        }

        @DeleteMapping("/delete")
        public Product getProduct() {
            // Code
        }
    }
    ```

    + It is often recommended to use the correct HTTP method with corresponding `CRUD` actions:
        + **Create**: Use POST method
        + **Read**: Use GET method
        + **Update**: Use PUT method
        + **Delete**: Use DELETE method

### Receive request data in Controller
**Controller** receives data from request. Depending on where the data is located, we have different ways to retrieve it:
- **PathVariable**: Used to receive parameters in the URL, often used when you need to map part of the URL to a method variable.
    ``` java
    @RestController
    @RequestMapping("/api/products")
    public class ProductController {
        @GetMapping("/{productId}")
        public Product getProductById(@PathVariable Long productId) {
            // Variable productId have the corresponding data
        }
    }
    ```

- **RequestParam**: Used to receive parameters from the query string of the URL.
    ``` java
    @RestController
    @RequestMapping("/api/products")
    public class ProductController {
        @GetMapping
        public Product getProductsByPriceRange(@RequestParam("minPrice") Double minPrice,
                                               @RequestParam("maxPrice") Double maxPrice) {
            // Now two variables minPrice and maxPrice have corresponding data
        }

        @GetMapping
        public Product getProductsByPriceRange2(@RequestParam(value = "minPrice", required = false) Double minPrice,
                                                @RequestParam(value = "maxPrice", required = false) Double maxPrice) {
            // Now two variables minPrice and maxPrice have corresponding data
            // Both variables are optional
            // Default value is NULL
        }

        @GetMapping(params = {"minPrice", "maxPrice"})
        public Product getProductsByPriceRange3(Double minPrice, Double maxPrice) {
            // Now two variables minPrice and maxPrice have corresponding data
        }

        @GetMapping(params = "category")
        public Product getProductsByCategoryId(Long categoryId) {
            // Variable categoryId have corresponding data
        }
    }
    ```

- **RequestBody**: Used to map the content of an HTTP request (usually JSON) to a Java object.
    ``` java
    @RestController
    @RequestMapping("/api/products")
    public class ProductController {
        @PostMapping
        public void insertProduct(@RequestBody Product product) {
            // Code
        }
    }
    ```



