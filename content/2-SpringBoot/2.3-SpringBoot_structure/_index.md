---
title : "Spring Boot Structure"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 2.3 </b> "
---

Spring Boot structure follow two models: Three-Tier architecture and MVC pattern.

As for Three-Tier architecture, the application is divided into 3 tiers as follows:
- **Presentation layer**: Interacts with the user, using View, Controller (in MVC) or API (if available).
- **Business logic layer**: Contains all program logic, most of the code is located here
- **Data access layer**: Interacts with the database, returns results to the business logic layer

In Spring Boot, there are several components that represent each class:
- **Service**: contains business logic code
- **Repository**: represents the data access layer

![Spring Boot](/Dung_aws/images/2.1/0004.png)

Combining the two models, you get a complete Spring Boot application, including the following components:
- **Controller**: returns View (containing available data, in the form of an HTML page), or Model expressed as an API for View (View written specifically in React, Vue, or Angular).
- **Service**: contains calculation and processing code. When Controller requests, the corresponding Service will receive and return data to the Controller (returning Model). Controller will send back View as above.
- **Repository**: Service can also interact with other services, or use Repository to call the DB. Repository directly interacts, reads and writes data in the DB and returns it to the service.

![Spring Boot](/Dung_aws/images/2.1/0006.png)

Spring Boot recommend package structure:
```
src/main/java/com/example/ProductManagerSystem/
├── controller/
├── service/
├── repository/
├── model/
└── exception/
```

## Reference
[Some reference to Spring Boot Structure](https://viblo.asia/p/luong-di-trong-spring-boot-ORNZqdELK0n)