# E-Commerce Platform  - Java Maven Project

This repository contains a minimal Java-based e-commerce backend prototype
- OOP implementation (models, encapsulation, toString)
- Collections & Generics (Order uses Map<Integer,Integer> to hold items)
- Multithreading & Synchronization (OrderProcessor runs on separate threads; DB updates use JDBC transactions)
- Classes for database operations (ProductDAO)
- Database connectivity (JDBC using H2 embedded database)
- Implement JDBC for database connectivity and CRUD operations

## Requirements
- Java 17+
- Maven 3.6+

## Project Structure
- `pom.xml` - Maven build file (includes H2 dependency)
- `src/main/java/com/galgotias/ecommerce/...` - Java source files
  - `model` - Product, Order models
  - `db` - DBManager (JDBC connection)
  - `dao` - ProductDAO (CRUD, prepared statements)
  - `service` - OrderProcessor (Runnable to process orders concurrently)
  - `Main.java` - Example seeding and concurrent order processing

## How to build & run
1. Open terminal in project root (where `pom.xml` is).
2. Build:
```
mvn clean package
```
3. Run:
```
java -cp target/ecommerce-review1-1.0-SNAPSHOT.jar:~/.m2/repository/com/h2database/h2/2.1.214/h2-2.1.214.jar com.galgotias.ecommerce.Main
```
(Alternatively run via `mvn exec:java` or run from your IDE which will download dependencies automatically.)


