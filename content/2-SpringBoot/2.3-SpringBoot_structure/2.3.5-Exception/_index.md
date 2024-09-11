---
title : "Exception"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 2.3.5 </b> "
---

#### Introduction to Exception layer
**Exception** layer in Spring Boot is responsible for handling exceptions that arise in the application.

Organizing and managing exceptions properly helps the application become stable, easy to maintain, and provides clear feedback to users and other system components.

#### Role of Exception layer
- **Consistent error handling**: **Exception** layer provides a consistent error handling mechanism, helping to manage and report errors in a controlled manner.
- **Improved user experience**: Instead of making users to receive confusing technical error messages, **Exception** layer helps create friendly and meaningful error messages.
- **Increased maintainability**: With a clear Exception layer, exceptions are managed in a single place, making it easy to test and maintain.

![Exception](/Dung_aws/images/2.1/0007.png)

#### Components in the Exception Layer
**Exception** layer usually includes the following components:
- **Custom Exception Classes**: To represent specific error types, you can create custom exception classes. These classes inherit from `RuntimeException` or `Exception`.

- **Global Exception Handler**: This is where all exceptions that arise in the application are handled, usually done with the `@ControllerAdvice` and `@ExceptionHandler` annotations.


#### Custom Exception
Here is an example of how to create a custom exception to handle **Business Exception**:
```java
@Getter
public class BusinessException extends RuntimeException {
    private final Resource resource;

    public BusinessException(Resource resource) {
        super(resource.getResourceName());  // resourceName stands for each error's message
        this.resource = resource;           // resource stands for specific error
    }
}
```

According to that, here is the **Resource** class:
```java
@Getter
public enum Resource {
    PRODUCT_ID_NOT_FOUND(1000,"Product ID not found"),
    CATEGORY_ID_NOT_FOUND(1001,"Category ID not found"),
    ITEM_ID_NOT_FOUND(1002,"Item ID not found"),
    CUSTOMER_ID_NOT_FOUND(1003,"Customer ID not found"),

    private final Integer code;
    private final String resourceName;

    Resource(Integer code, String resourceName) {
        this.code = code;
        this.resourceName = resourceName;
    }
}
```

#### Global Exception Handler
Global Exception Handler is a central component for managing all exceptions in the application.

```java
@RestControllerAdvice 
public class GlobalExceptionHandler {
    @ExceptionHandler(Exception.class)
    public ResponseEntity<ResponseObject> handleException(Exception e) {
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(
                new ResponseObject(
                        500,
                        e.getMessage(),
                        null
                )
        );
    }

    @ResponseStatus(HttpStatus.BAD_REQUEST)
    @ExceptionHandler(BusinessException.class)
    public ResponseEntity<ResponseObject> handleNotFoundException(BusinessException e) {
        return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(
                new ResponseObject(
                        e.getResource().getCode(),
                        e.getMessage(),
                        null
                )
        );
    }
}
```




