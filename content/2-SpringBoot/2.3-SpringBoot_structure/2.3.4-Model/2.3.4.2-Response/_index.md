---
title : "Response"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.3.4.2 </b> "
---

**Response** classes are recommended to help user get the object's return appropriately.

- Example of **Response object**:
    ```java
    @AllArgsConstructor
    @NoArgsConstructor
    @Data
    public class ResponseObject {
        private Integer code;
        private String message;
        private Object data;
    }
    ```

- Example in **Controller class**:
    ``` java
    @RestController
    @RequestMapping("/api/products")
    public class ProductController {
        @Autowired
        private ProductService productService;

        @GetMapping("/{productId}")
        public ResponseEntity<ResponseObject> getProductById(@PathVariable Long productId) throws BusinessException {
            return ResponseEntity.status(HttpStatus.OK).body(
                new ResponseObject(
                    200,
                    "Successfully get Product by Id: " + productId,
                     productService.getProductById(productId)
                )
            );
        }
    }
    ```