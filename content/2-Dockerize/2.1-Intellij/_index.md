---
title : "Open Intellij"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

## On Intellij

1. Open **Intellij** - **Maven** - **Lifecycle** - **clean** - **install**

![Dockerize](/images/1/0001.png)

**!!!** ***Make sure there is no error when running the above process***

* If it is **Build Success** then go to the next step

![Dockerize](/images/1/0002.png)

2. Running JAR file

- After **Build Success**, copy JAR file and open terminal

![Dockerize](/images/1/0003.png)

- Run **java -jar *JAR file***

![Dockerize](/images/1/0004.png)


3. Deploy

- Open file **Dockerfile**
- Copy the following code:
   ```
   FROM eclipse-temurin:17-jdk-focal
   WORKDIR /app
   COPY .mvn/ .mvn
   COPY mvnw pom.xml ./
   RUN ./mvnw dependency:go-offline
   COPY src ./src
   CMD ["./mvnw", "spring-boot:run"]

   ```

![Dockerize](/images/1/0005.png)

- Build Docker Image
- Run **docker build -f Dockerfile -t spring-boot .**

![Dockerize](/images/1/0006.png)

4. Open **Docker**
- After build successfully, open **Docker Desktop** - **Images**
- Check if there is **spring-boot** file as you named

![Dockerize](/images/1/0007.png)
