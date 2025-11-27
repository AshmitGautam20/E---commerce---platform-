# E-Commerce Platform (Review 1) - Java Maven Project

This repository contains a minimal Java-based e-commerce backend prototype intended to satisfy the Review-1 rubric items:
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

## Notes for reviewers
- The `ProductDAO` uses `PreparedStatement` and `MERGE` to insert/update products, illustrating JDBC usage and prepared statements (mitigating SQL injection).
- The `OrderProcessor` demonstrates multithreading: two orders are submitted concurrently to an `ExecutorService` to show how stock updates may contend.
- Collections: `Order` uses a `HashMap` for items and demonstrates generics.
- OOP: Models are well-encapsulated and have clear responsibilities.
- The DB is H2 embedded (file at `./data/ecommerce_db.mv.db`) so reviewers can inspect persisted data between runs.

## Rubric mapping (Review-1)
- OOP Implementation: Product, Order classes, encapsulation, constructors, toString -> **10 marks**
- Collections & Generics: Order uses `Map<Integer,Integer>`, usage in processing -> **6 marks**
- Multithreading & Synchronization: `OrderProcessor` + thread pool -> **4 marks**
- Classes for DB operations: `ProductDAO` and `DBManager` -> **7 marks**
- Database Connectivity (JDBC): H2 + JDBC usage -> **3 marks**
- Implement JDBC: PreparedStatement, transactions -> **3 marks**

## Deliverables
This zip includes ready-to-build source and this README. You may extend to add servlets/web integration for final submission.
