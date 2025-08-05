
# Why Learn JPA?

### Widely Used

The thing about enterprise applications is that they connect to the database. 
The database, most of the time, is a relational database (RDBMS).

When you look at Java applications, the most widely used way to connect to RDBMS is using **JPA**. 
An alternative is called **JDBC**, which is considered low-level and primitive.

### Common Scenarios for Using JPA:

1. **Spring Boot Applications for Databases** (Most popular choice).
2. **Java/Jakarta EE Applications** with database integration.
3. **Microservices Architecture**:
   - Each service has its own database.
   - Smaller apps or services could be Spring Boot or Jakarta EE applications.
4. **Desktop and Mobile Applications** (less widely used).


### What is JPA?

**Java Persistence API (JPA)** is a specification in Java for managing relational data in applications. It provides a way to map Java objects to database tables and vice versa, enabling seamless interaction with a database using object-oriented paradigms.

---

### Key Features of JPA:

1. **Object-Relational Mapping (ORM)**:
   - Maps Java objects (entities) to database tables.
   - Simplifies database operations by abstracting SQL queries.

2. **Standardized API**:
   - Defines a set of interfaces and annotations to manage persistence in Java applications.
   - Works independently of the underlying database.

3. **Query Language**:
   - Provides JPQL (Java Persistence Query Language), a database-independent query language that resembles SQL but operates on entities instead of tables.

4. **Transaction Management**:
   - Offers built-in support for managing database transactions, ensuring consistency and reliability.

---

### JPA vs. JDBC:

| Feature           | JPA                                    | JDBC                           |
|-------------------|----------------------------------------|--------------------------------|
| **Abstraction**   | High-level ORM, no need to write SQL.  | Low-level, manual SQL writing. |
| **Ease of Use**   | Simple and declarative.                | Complex and verbose.           |
| **Query Language**| JPQL (abstracted).                    | Plain SQL (direct).            |
| **Scalability**   | Better for large-scale applications.   | Limited abstraction, less scalable. |

---

### Common Implementations of JPA:

JPA itself is a specification, meaning it defines rules but doesn't provide concrete implementations. Popular implementations include:

1. **Hibernate** (most widely used).
2. **EclipseLink**.
3. **Apache OpenJPA**.

---

### Why Use JPA?

- **Simplified Code**: No need to write boilerplate SQL for common operations.
- **Cross-Database Compatibility**: Abstracts database-specific queries.
- **Maintainability**: Reduces complexity in handling database interactions.
- **Integration with Frameworks**: Works seamlessly with frameworks like **Spring Boot**.

JPA is a must-learn tool for Java developers aiming to build scalable, maintainable, and efficient database-driven applications.

# Object-Relational Mapping (ORM) and JPA

### How a Standard Java Application Connects to a Database:

1. **JDBC Drivers**: Used to connect to the database.
2. **Data Access Service**: Accesses data using these drivers.
3. **DAO (Data Access Objects)**: Instances of objects that contain database data.

### Typical Flow of a Java Application:

![image](https://github.com/user-attachments/assets/1c9da148-e3dc-4dcf-b1d9-b003ec4ea372)

- **Business Service** → Makes a call to the Data Service.
- **Data Service** → Connects to the database using JDBC drivers and fetches data.
- Data Service then packs the data into DTOs (Data Transfer Objects) and returns it to the Business Service.

### JPA's Role in Data Interaction:

JPA replaces the interaction between the **Data Service** and **JDBC**. Instead of using JDBC, JPA allows developers to use API calls, which simplifies database operations.

---

### Why Use JPA?

#### Mismatch Between Java Classes and Database Tables:

- **Relational World**: Data is stored as rows in tables.
- **Java World**: Data is represented as objects.

**Example: Employee Data**

- A single **row in a database table** corresponds to an **Employee object** in Java.

#### Problems Without JPA (Manual Mapping):

**Read Operation**:
1. Prepare an SQL query.
2. Run the query.
3. Retrieve a result set.
4. Loop through the result set and create Java objects for each row.
5. Extract each column's data and assign it to the object's properties.
6. Collect the objects in a list.
7. Handle errors.

**Write Operation**:
1. Extract object attributes.
2. Prepare an SQL query.
3. Manage keys and relationships.
4. Run the query.
5. Manage transactions.
6. Handle errors.

Without JPA, developers must manually map Java objects to relational tables and vice versa.

---

### How JPA Solves This Problem:

- Provides annotations to map Java properties to database columns.
- Handles the creation of objects from database rows automatically.
- Ensures each instance of a Java class corresponds to a row in the table.

**Example of Mapping**:
- Java's `Employee` class with a property `address` can map to a separate `Address` table in the database.
- JPA manages complex relationships like foreign keys and composite tables automatically.

---

### Impedance Mismatch in ORM:

- **Scenario 1**: Employee table has a foreign key to the Address table.
  - In Java: `address` is just a property in the `Employee` class. Where Address is a seprate class.
  - In the database: `Employee` and `Address` are separate tables with a foreign key relationship.
 
    ![image](https://github.com/user-attachments/assets/6fcf72a7-2cac-4fa1-82dc-224619da45e2)

- **Scenario 2**: Employee-Manager Relationship.
  - In Java: `manager` is a property in the `Employee` class (self-referential).
  - In the database: A foreign key in the `Employee` table refers to the `Manager`.


### How JPA Helps:

- JPA provides APIs and annotations to define and manage these relationships seamlessly.
- Automatically maps Java properties to database relationships.

---

JPA bridges the gap between how data is represented in Java and relational databases, making development faster, easier, and less error-prone.


### Understanding the Difference:



Think of it with this analogy:

- **JPA**: Like a Java interface (a blueprint for APIs).

- **Hibernate**: An implementation class of that interface.



Hibernate is an open-source Object-Relational Mapping (ORM) framework that knows how to perform ORM operations.



---



### How to Use Hibernate:



1. Add the Hibernate library to your classpath.

2. Map your classes to database tables.

3. Map your member variables to the columns of the table.

4. Use Hibernate APIs to save, update, or retrieve data.



#### Mapping in Hibernate:

- Use Java annotations to map classes and their properties to corresponding database tables and columns.



**Example Workflow:**  

1. Define entity classes.  

2. Annotate the classes and fields for mapping.  

3. Use Hibernate APIs to handle database operations.  



![Mapping Example](https://github.com/user-attachments/assets/460f3902-8a93-4f0b-8e50-9766776cb400)



---



### Role of Hibernate in Application Architecture:



In an application, Hibernate acts as a layer between your application and JDBC.  

- It automates all the JDBC calls based on the mappings provided.



**Simplified Picture:**  

![Hibernate Architecture](https://github.com/user-attachments/assets/34b9291b-31bc-488a-97fe-cbadc7cba7e0)



---



### Why JPA Was Introduced:



- Hibernate is just **one** ORM solution, and there are other implementations as well.  

- **JPA** was introduced to standardize ORM mappings so that developers are not tied to a single ORM implementation.

- If Hibernate were discontinued tomorrow, applications using JPA could easily switch to another JPA-compliant implementation without major changes.



**Popular JPA Implementations:**  

1. Hibernate.  

2. EclipseLink.  

3. OpenJPA.



---



### Conclusion:



- **JPA** provides a standard and flexible API for ORM.  

- **Hibernate** is a specific implementation of the JPA specification.  

- By using JPA, you ensure portability and flexibility while benefiting from Hibernate's powerful ORM capabilities.

# Java Persistence API (JPA) Overview



### What is JPA?



- **JPA** describes the API for Object-Relational Mapping (ORM), not the implementation.

- It defines a standard way to interact with relational databases in Java, focusing on working with objects and classes rather than SQL tables and rows.



---



### Steps to Add JPA to a Java Project:



1. **Add an Implementation**:  

   JPA requires an implementation (also called a persistence provider). Examples include Hibernate, EclipseLink, or OpenJPA.  



   ![Implementation Example](https://github.com/user-attachments/assets/206e022a-1047-47a0-bb18-c12cecab7ba0)





---



### Popular JPA Implementations:



Some widely used JPA implementations:  



![Popular Implementations](https://github.com/user-attachments/assets/d7eaeca1-7e99-46cf-a192-1ebc1f2bf1fa)



---



### Why Use the JPA API?



- You call JPA APIs in your code, not specific implementation APIs like Hibernate or TopLink.

- This abstraction ensures that switching between implementations is easy.



**Example API Usage:**  

- **Retrieve data**: "Hey JPA, get me all employees."  

  - **Result**: A list of all `Employee` instances.  

- **Save data**: "Hey JPA, save this employee instance."  

  - **Input**: An `Employee` object.  

  - **Result**: A corresponding row is inserted/updated in the database.



---



### Benefits of JPA Over SQL:



1. **Developer Productivity**: Faster and more intuitive development with JPA.

2. **Database Independence**: The JPA API remains consistent across all RDBMS systems.

3. **Caching and Performance**: JPA implementations often provide built-in caching.

4. **Large Applications**: Developers can focus on the problem domain instead of writing SQL.



---



### Learning JPA:



- Learn how to map Java objects to database tables (ORM).

- Understand how to perform CRUD operations on objects.



#### Tricky Parts:

- Modeling relationships (e.g., one-to-many, many-to-one).

- Interacting with tables efficiently.

- Implementing transactions.

- Writing object queries using JPQL (Java Persistence Query Language) for flexible querying.



---



JPA simplifies working with relational databases in Java, enabling developers to focus on the application's domain rather than database intricacies.


# Setting Up a JPA Implementation

### Types of JPA Projects:

1. **Using Spring/Spring Boot Integration**:  
   - Provides high-level abstractions for JPA.  
   - Simplifies setup but hides much of JPA's internal workings.

2. **Using Java EE/Jakarta EE Server**:  
   - Similar to Spring Boot, offers abstractions over JPA.

### Why Understand JPA with Barebones Java?

Frameworks provide convenience but hide the "magic" of how JPA works. To fully understand JPA, setting it up in a simple Java project is recommended.

---

### Steps to Set Up JPA in a Barebones Java Project:

1. **Create a Simple Java Project**:

2. **Add JPA Libraries as Maven Dependencies**:
   - Include dependencies for a JPA implementation (e.g., Hibernate) in the `pom.xml` file.

3. **Configure Database Connection**
  
4. **Perform Entity-Relationship Mapping**:
   - Define entity classes and annotate them with JPA annotations.

5. **Use JPA API to Persist an Entity Instance**:


### Summary:

This approach sets up JPA in a minimalistic way, without relying on frameworks.  
By following these steps, you will understand the core functionality of JPA and its interaction with the database.


# Setting Up and Using H2 Database

### Why Use H2 Database?

H2 is a lightweight, fast, and easy-to-setup relational database. It is ideal for testing and development purposes due to its simplicity and versatility.

---

### Modes of Operation:

1. **In-Memory Database**:
   - The database resides in the memory of the Java application.
   - Consumes the same processing capacity as the application.
   - Data is lost when the application shuts down.

2. **Server Mode**:
   - Runs as a separate database server.
   - Applications connect to it like a regular database server.
   - Data persists beyond the application's lifecycle.

---

### Installing H2 Database

1. Visit the [H2 Database official website](https://www.h2database.com/html/main.html).
2. Download the installer for your operating system.
3. Install the application to spin up the database in server mode.

---

### Default Credentials:

- **Username**: `sa`  
- **Password**: (empty by default)

These can be configured based on your requirements.


### Summary

H2 Database is a great choice for quick setups, testing, and development environments. It can be seamlessly integrated with Java applications, especially with JPA and Hibernate.

# Creating a Barebone Java App with Maven



### Step 1: Create a New Maven Project in IntelliJ



1. Open **IntelliJ IDEA**.

2. Click on **New Project**.

3. Select **Maven** as the project type.

4. Set the project name and group ID, then finish to create a barebone Java project.



---



### Step 2: Add Required Dependencies



In the `pom.xml` file of the project, add the following dependencies:



1. **JPA Implementation (Hibernate)**:  

   Hibernate implements JPA, so adding Hibernate automatically includes the JPA API.



```xml

   <dependency>

       <groupId>org.hibernate</groupId>

       <artifactId>hibernate-entitymanager</artifactId>

       <version>5.6.15.Final</version>

   </dependency>
```
H2 Database Driver:
- JPA relies on JDBC to connect to the database, and JDBC requires database drivers.
```

<dependency>

    <groupId>com.h2database</groupId>

    <artifactId>h2</artifactId>

    <version>2.2.224</version>

    <scope>compile</scope>

</dependency>
```

# Complete Dependencies Section:

Your dependencies section should look like this:

```
    <dependencies>

        <dependency>

            <groupId>org.hibernate</groupId>

            <artifactId>hibernate-entitymanager</artifactId>

            <version>5.6.15.Final</version>

        </dependency>

        <dependency>

            <groupId>com.h2database</groupId>

            <artifactId>h2</artifactId>

            <version>2.2.224</version>

            <scope>compile</scope>

        </dependency>

    </dependencies>
```

Step 3: Configure Database Connection : We will do that in the next step.


# Setting Up JPA with Persistence.xml and Creating an Entity

## Overview
In this tutorial, we configure JPA to connect to a database using the `persistence.xml` file and create a simple `Employee` entity to persist data.

---

## **Step 1: Configuring `persistence.xml`**

### Path
`src/main/resources/META-INF/persistence.xml`

### Purpose
The `persistence.xml` file is used to define a **persistence context**, which contains:
- Information about the database.
- The connection string (JDBC URL), username, and password.
- Behavior for database schema updates, transaction management, and caching.

### Content
Here is the content of the `persistence.xml` file:

```xml
<persistence xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://java.sun.com/xml/ns/persistence http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd"
             version="2.0" xmlns="http://java.sun.com/xml/ns/persistence">
    <persistence-unit name="myApp" transaction-type="RESOURCE_LOCAL">
        <provider>org.hibernate.ejb.HibernatePersistence</provider>
        <properties>
            <property name="javax.persistence.jdbc.url" value="jdbc:h2:tcp://localhost/~/test"/>
            <property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/>
            <property name="javax.persistence.jdbc.user" value="sa"/>
            <property name="javax.persistence.jdbc.password" value=""/>
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
            <property name="hibernate.dialect" value="org.hibernate.dialect.H2Dialect"/>
            <property name="hibernate.hbm2ddl.auto" value="create-drop"/>
        </properties>
    </persistence-unit>
</persistence>
```

---

### Explanation
1. **`<persistence-unit>`**
   - Defines one database connection.
   - The `name` attribute (`myApp`) is used in the code to refer to this configuration.

2. **`<provider>`**
   - Specifies the JPA implementation. Here, we use Hibernate (`org.hibernate.ejb.HibernatePersistence`).

3. **`<properties>`**
   - Contains database connection details and configuration.

   | Property Name                              | Description                                      |
   |-------------------------------------------|--------------------------------------------------|
   | `javax.persistence.jdbc.url`              | JDBC URL of the database to connect to.         |
   | `javax.persistence.jdbc.driver`           | Fully qualified class name of the JDBC driver.  |
   | `javax.persistence.jdbc.user`             | Database username.                              |
   | `javax.persistence.jdbc.password`         | Database password.                              |
   | `hibernate.show_sql`                      | Logs SQL queries in the console (for debugging).|
   | `hibernate.format_sql`                    | Formats SQL output for readability.             |
   | `hibernate.dialect`                       | Defines the SQL dialect for Hibernate.          |
   | `hibernate.hbm2ddl.auto`                  | Behavior for schema updates (`create-drop`).    |

---

## **Step 2: Creating the `Employee` Entity**

### Purpose
To represent a database table as a Java class and allow JPA to persist instances of the class.

### Code
```java
package org.example;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "EMPLOYEE_DATA")
public class Employee {

    @Id
    @Column(name = "id")
    private int id;

    @Column(name = "name")
    private String name;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

---

### Explanation
 **Annotations**
   - `@Entity`: Marks the class as a JPA entity (maps to a database table).
   - `@Table(name = "EMPLOYEE_DATA")`: Specifies the table name for the entity.
   - `@Id`: Marks the primary key field.
   - `@Column(name = "column_name")`: Maps a class field to a database column.



# Getting Started with JPA: Saving an Entity to the Database

## Steps to Set Up JPA (Already seen previously)
1. **Connect to the Database**: Add the dependency for the database drivers.
2. **Define Connection Details**: Specify the connection URL, username, and password in `persistence.xml`.
3. **Map POJO to Database Table**: Annotate your POJO class as an entity.

## Using the JPA API to Save an Entity (Let's start here)
To save the entity, we need an `EntityManager`. 

### What is an Entity Manager?
An `EntityManager` is an object/service provided by JPA to manage entities, acting as a bridge between the database and Java objects.

### Obtaining an Entity Manager
As most things in java we get stiff from a factory.
We get the `EntityManager` from an `EntityManagerFactory`. To create this factory, we use the `Persistence` class.

```java
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;

public class JpaStarterMain {
    public static void main(String[] args) {
        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
    }
}
```

### Creating an Entity Manager from the Factory
```java
import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;

public class JpaStarterMain {
    public static void main(String[] args) {
        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
        EntityManager entityManager = entityManagerFactory.createEntityManager();
    }
}
```

## Saving the Entity
To save the entity, use the `persist()` method of the `EntityManager`.

```java
import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;

public class JpaStarterMain {
    public static void main(String[] args) {
        Employee employee = new Employee();
        employee.setId(1);
        employee.setName("Bob");

        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
        EntityManager entityManager = entityManagerFactory.createEntityManager();

        entityManager.persist(employee);
    }
}
```

### Automatic Table Creation
The `persistence.xml` configuration is written such that :
```xml
<property name="hibernate.hbm2ddl.auto" value="create-drop"/>
```
This will drop existing tables and create new ones based on the entities defined in the Java code.

### Transactions for Writing Operations
Before saving, we need transactions for write ops like these.
start a transaction. Commit it after calling `persist()`.

```java
package org.example;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.EntityTransaction;
import javax.persistence.Persistence;

public class JpaStarterMain {
    public static void main(String[] args) {
        Employee employee = new Employee();
        employee.setId(1);
        employee.setName("Bob");

        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
        EntityManager entityManager = entityManagerFactory.createEntityManager();

        EntityTransaction transaction = entityManager.getTransaction();
        
        transaction.begin();
        entityManager.persist(employee);
        transaction.commit();
    }
}
```

## Running the Application
On running the application, observe the console logs indicating the following steps:
1. The table is dropped if it exists.
2. A new table is created based on the entity definitions.
3. The entity is inserted into the table.

### Example Console Output:
```
Dec 02, 2024 7:03:18 PM org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl buildCreator
INFO: HHH10001005: using driver [org.h2.Driver] at URL [jdbc:h2:tcp://localhost/~/test]
Dec 02, 2024 7:03:18 PM org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl buildCreator
INFO: HHH10001001: Connection properties: {password=****, user=sa}
```

![Table Creation and Data Insertion](https://github.com/user-attachments/assets/e749d7c0-5a4b-4012-9ef9-428ebe82b105)

### Inserted Data:
![Inserted Data](https://github.com/user-attachments/assets/110b2434-ac1b-40e3-b0bc-c372c4289efc)


Let's break down the details of the `persistence.xml` file for a deeper understanding.

---

## **What is `persistence.xml`?**
`persistence.xml` is a configuration file that defines:
1. **Connection Details**: Where to connect (database URL, username, password).
2. **Behavior**: How JPA behaves when connected to the database (e.g., table creation, formatting SQL).
3. **Transaction Settings**: Specifies the type of transaction management.
4. **Provider Configuration**: Determines which JPA provider to use (e.g., Hibernate) and its behavior.

The configurations start with the **persistence unit**, which is a logical grouping of entity classes and connection details.

---

## **Structure of `persistence.xml`**

```xml
<persistence>
    <persistence-unit name="myApp" transaction-type="RESOURCE_LOCAL">
        <provider>org.hibernate.ejb.HibernatePersistence</provider>
        <properties>
            <property name="javax.persistence.jdbc.url" value="jdbc:h2:tcp://localhost/~/test"/>
            <property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/>
            <property name="javax.persistence.jdbc.user" value="sa"/>
            <property name="javax.persistence.jdbc.password" value=""/>
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
            <property name="hibernate.dialect" value="org.hibernate.dialect.H2Dialect"/>
            <property name="hibernate.hbm2ddl.auto" value="create-drop"/>
        </properties>
    </persistence-unit>
</persistence>
```

---

### Key Elements of `persistence.xml`

1. **`<persistence>`**  
   The root element that wraps all persistence units. You can define multiple `<persistence-unit>` tags here.

2. **`<persistence-unit name="myApp" transaction-type="RESOURCE_LOCAL">`**  
   - **`name`**: A unique identifier for the persistence unit. This name is referenced in the application (e.g., `Persistence.createEntityManagerFactory("myApp")`).
   - **`transaction-type`**: 
     - **`RESOURCE_LOCAL`**: Manual management of `EntityManager` and transactions by the application.  
     - **`JTA`**: The container manages transactions and `EntityManager` lifecycle (e.g., in a Java EE environment).

3. **`<provider>`**  
   Specifies the JPA provider implementation.  
   Example: Hibernate (`org.hibernate.ejb.HibernatePersistence`).

4. **`<properties>`**  
   Defines JPA and Hibernate-specific behaviors:
   - **JPA Properties** (start with `javax.persistence`):  
     - **`javax.persistence.jdbc.url`**: Database URL.  
     - **`javax.persistence.jdbc.driver`**: JDBC driver class.  
     - **`javax.persistence.jdbc.user`**: Database username.  
     - **`javax.persistence.jdbc.password`**: Database password.
   - **Hibernate Properties** (start with `hibernate`):  
     - **`hibernate.show_sql`**: Logs SQL statements to the console.  
     - **`hibernate.format_sql`**: Formats SQL for readability.  
     - **`hibernate.dialect`**: Specifies the SQL grammar for the database.  
       Example: `org.hibernate.dialect.H2Dialect` for H2 Database.  
     - **`hibernate.hbm2ddl.auto`**: Determines schema management behavior:  
       - `create-drop`: Drops and recreates tables based on the entity definitions.  
       - `update`: Updates the schema without dropping tables.  
       - `validate`: Validates the schema without making changes.  
       - `none`: No schema management.

---

### Example Behavior Explained
1. **Table Management**  
   The property `<property name="hibernate.hbm2ddl.auto" value="create-drop"/>` ensures:  
   - Tables corresponding to entities are dropped if they already exist.  
   - New tables are created based on the entity annotations.

2. **SQL Dialect**  
   Dialect defines nuances like syntax and data types based on the database.  
   Example: H2, MySQL, Oracle, SQL Server have subtle differences in SQL grammar. Hibernate adjusts queries accordingly.

3. **Logging SQL**  
   With `hibernate.show_sql` and `hibernate.format_sql` set to `true`, Hibernate logs well-formatted SQL statements during execution, making debugging easier.


### Mapping Java Classes to Database Tables in JPA

JPA provides annotations to map Java classes and their properties to database tables and columns. Here's how they work:

---

### **@Entity Annotation**
- Declares a Java class as an **entity** that will be managed by JPA.
- The class becomes a representation of a table in the database.

**Example:**
```java
@Entity
public class Employee {
    // fields and methods
}
```

---

### **@Table Annotation**
- Maps the entity class to a specific table in the database.  
- **Optional**: If not provided, the table name defaults to the class name.

**Attributes:**
1. **`name`**: Specifies the table name.  
   If not specified, the class name is used as the table name.  
   Example:  
   ```java
   @Table(name = "employee_table")
   ```
2. **`schema`**: Specifies the schema of the table. Useful when working with multiple schemas.  
   Example:  
   ```java
   @Table(schema = "company_schema")
   ```

**Example Usage:**
```java
@Entity
@Table(name = "employees", schema = "company_schema")
public class Employee {
    // fields and methods
}
```

---

### **@Column Annotation**
- Maps a class property to a table column.  
- **Optional**: If not provided, the column name defaults to the property name.

**Attributes:**
1. **`name`**: Maps the property to a specific column name in the table.  
   Example:  
   ```java
   @Column(name = "emp_id")
   private int id;
   ```
2. **`unique`**: Ensures the column's values are unique (e.g., Aadhar number, Passport number).  
   Example:  
   ```java
   @Column(unique = true)
   private String passportNumber;
   ```
   - If a duplicate value is inserted, a **constraint violation exception** will occur.
3. **`length`**: Specifies the maximum length for a column (default is 255).  
   Example:  
   ```java
   @Column(length = 10)
   private String passportNumber;
   ```
4. **`nullable`**: Determines if the column allows `NULL` values (default is `true`).  
   Example:  
   ```java
   @Column(nullable = false)
   private String name;
   ```
   - Setting `nullable = false` ensures that the column must have a value during insertion.

**Example Usage:**
```java
@Entity
@Table(name = "employees")
public class Employee {

    @Id
    private int id;

    @Column(name = "employee_name", nullable = false, length = 50)
    private String name;

    @Column(unique = true)
    private String aadharNumber;

    @Column(nullable = false)
    private String department;

    // Getters and Setters
}
```

---

### **Summary of Annotations**

| Annotation         | Purpose                                    | Key Attribute(s)               |
|--------------------|--------------------------------------------|---------------------------------|
| `@Entity`          | Declares a Java class as a JPA entity.     | -                               |
| `@Table`           | Maps an entity to a specific table.        | `name`, `schema`               |
| `@Column`          | Maps a property to a specific column.      | `name`, `unique`, `length`, `nullable` |

---

### **Example: Full Mapping**

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;
import javax.persistence.Column;

@Entity
@Table(name = "employee_details", schema = "company_schema")
public class Employee {

    @Id
    private int id;

    @Column(name = "full_name", nullable = false, length = 100)
    private String name;

    @Column(unique = true, nullable = false)
    private String aadharNumber;

    @Column(name = "dept_name", nullable = true)
    private String department;

    // Getters and Setters
}
```

This will create a table `employee_details` in the schema `company_schema` with the specified columns and constraints.


When dealing with custom types such as `Date` in JPA, the framework needs explicit instructions on how to map them to the corresponding SQL data type. For this purpose, JPA provides the `@Temporal` annotation.

---

### **The `@Temporal` Annotation**

The `@Temporal` annotation is used to specify the exact SQL temporal type for a `Date` or `Calendar` field in the entity. JPA uses the specified type to map the field to an appropriate column type in the database.

**Supported Temporal Types:**
1. **`TemporalType.DATE`**  
   Maps to a SQL `DATE` type, storing only the date (year, month, day).  
   Example: `2024-12-02`
2. **`TemporalType.TIME`**  
   Maps to a SQL `TIME` type, storing only the time (hours, minutes, seconds).  
   Example: `14:30:15`
3. **`TemporalType.TIMESTAMP`**  
   Maps to a SQL `TIMESTAMP` type, storing both date and time.  
   Example: `2024-12-02 14:30:15`

---

### **How to Use `@Temporal`**

**Example:**
```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Temporal;
import javax.persistence.TemporalType;

@Entity
public class Employee {

    @Id
    private int id;

    private String name;

    @Temporal(TemporalType.DATE)
    private Date dob;

    @Temporal(TemporalType.TIMESTAMP)
    private Date lastModified;

    // Getters and Setters
}
```

---

### **What Happens During Mapping**

- **`TemporalType.DATE`**:  
  JPA will map `dob` to a column with the SQL type `DATE`. This column stores only the date component.
  
- **`TemporalType.TIMESTAMP`**:  
  JPA will map `lastModified` to a column with the SQL type `TIMESTAMP`. This column stores both the date and time.

If you omit the `@Temporal` annotation on a `Date` or `Calendar` field, JPA will throw an exception because it cannot infer the desired mapping.

---

### **Differences in SQL Types**

| **Temporal Type**       | **SQL Type**       | **Purpose**                        | **Example**             |
|--------------------------|--------------------|-------------------------------------|-------------------------|
| `TemporalType.DATE`      | `DATE`            | Stores only the date.              | `2024-12-02`            |
| `TemporalType.TIME`      | `TIME`            | Stores only the time.              | `14:30:15`              |
| `TemporalType.TIMESTAMP` | `TIMESTAMP`       | Stores both date and time.         | `2024-12-02 14:30:15`   |

---

### **When to Use Each Temporal Type**

- **`TemporalType.DATE`**: Use for fields like **date of birth**, **hiring date**, or any field that only requires the date.
- **`TemporalType.TIME`**: Use for fields like **meeting time**, **alarm time**, or fields storing only the time of day.
- **`TemporalType.TIMESTAMP`**: Use for fields like **createdAt**, **updatedAt**, or any field requiring both date and time.

---

### **Full Example with Database Behavior**

**Entity:**
```java
@Entity
public class Event {

    @Id
    private int id;

    private String name;

    @Temporal(TemporalType.DATE)
    private Date eventDate;

    @Temporal(TemporalType.TIME)
    private Date eventTime;

    @Temporal(TemporalType.TIMESTAMP)
    private Date lastUpdated;

    // Getters and Setters
}
```

**Generated SQL:**
```sql
CREATE TABLE Event (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    eventDate DATE,
    eventTime TIME,
    lastUpdated TIMESTAMP
);
```

With this configuration, JPA will correctly map the `Date` fields to the appropriate SQL types based on the `@Temporal` annotation.


### Mapping Enumerations to Database Columns in JPA

When working with JPA (Java Persistence API), mapping an `enum` to a database column requires careful consideration to ensure consistency and prevent future issues.

---

#### Example Scenario

Consider the following enumeration for employee types:

```java
public enum EmployeeType {
    FULLTIME, PARTTIME
}
```

In our entity class, we include this as a property:

```java
private EmployeeType employeeType;
```

#### Default JPA Behavior

When we persist an entity with this setup, JPA by default maps the enum to an `integer` column in the database. The ordinal (index) of the enum value is stored:

```java
create table EMPLOYEE_DATA (
    id integer not null,
    dob date,
    employeeType integer,
    name varchar(255),
    primary key (id)
)
```

For example:
- `FULLTIME` → 0
- `PARTTIME` → 1

If the following code is executed:

```java
public class JpaStarterMain {
    public static void main(String[] args) {
        Employee employee = new Employee();
        employee.setId(1);
        employee.setName("Bob");
        employee.setDob(new Date());
        employee.setEmployeeType(EmployeeType.FULLTIME);

        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
        EntityManager entityManager = entityManagerFactory.createEntityManager();
        EntityTransaction transaction = entityManager.getTransaction();

        transaction.begin();
        entityManager.persist(employee);
        transaction.commit();
    }
}
```

The database would store the `employeeType` as `0` (ordinal of `FULLTIME`).

#### Problem with Default Behavior

The default ordinal mapping introduces a significant risk:
- **Changing the order of enum values:** If the enum order changes, e.g., `EmployeeType` becomes:
  ```java
  public enum EmployeeType {
      PARTTIME, FULLTIME
  }
  ```
  The database values become meaningless as the ordinals no longer align.

#### Using @Enumerated Annotation

To avoid the ordinal problem, use the `@Enumerated` annotation with `EnumType.STRING`:

```java
@Enumerated(EnumType.STRING)
private EmployeeType employeeType;
```

This tells JPA to store the name of the enum value (e.g., `FULLTIME`, `PARTTIME`) instead of its ordinal. The resulting table schema changes as follows:

```sql
create table EMPLOYEE_DATA (
    id integer not null,
    dob date,
    employeeType varchar(255),
    name varchar(255),
    primary key (id)
)
```

The database now stores `employeeType` as a string, ensuring data consistency if the order of enum values changes.

---

#### Limitations of EnumType.STRING

Even with `EnumType.STRING`, a potential issue remains:
- **Renaming enum values:** If an enum value's name changes, the database values will no longer match the updated enum, leading to errors or inconsistencies.

#### Best Practices for Enum Mapping

1. **Avoid Renaming Enum Values:** Enum values should remain consistent throughout the application's lifecycle.
2. **Document Enums Clearly:** Use comments or documentation to emphasize that enum values should not be reordered or renamed.


### Excluding Properties from Persistence in JPA

When working with entity classes in JPA, there may be cases where certain properties are useful for your Java code but should not be persisted in the database. Examples include debug information, derived properties, or temporary values used only at runtime. Here's how you can exclude such properties from persistence.

---

#### Example Scenario

Suppose you have an entity class with a property `debugString` that you don’t want to save to the database:

```java
@Entity
public class Employee {
    @Id
    private int id;

    private String name;

    private Date dob;

    private EmployeeType employeeType;

    private String debugString; // Useful for Java logic, not needed in the database
}
```

By default, JPA maps all fields in the entity class to database columns. Hence, the `debugString` field would also be included in the table schema and persisted.

---

### Ways to Exclude Properties from Persistence

#### 1. **Using JPA's `@Transient` Annotation**

The `@Transient` annotation (from `javax.persistence`) tells JPA explicitly not to persist the annotated field:

```java
@Transient
private String debugString;
```

When you use `@Transient`, JPA will ignore the field entirely, and it will not appear in the database schema or be persisted during runtime.

#### 2. **Using Java's `transient` Keyword**

The `transient` keyword in Java is typically used to exclude fields from being serialized when an object is converted to a stream. However, JPA also respects this keyword and will exclude such fields from persistence:

```java
private transient String debugString;
```

If you use `transient`, the field will not be persisted, but it might not be explicitly documented for JPA. This is more of a generic Java approach than a JPA-specific solution.

---

#### Key Differences

| Feature                    | `@Transient`                             | `transient`                           |
|----------------------------|-------------------------------------------|---------------------------------------|
| **Scope**                  | Specific to JPA                          | General Java serialization mechanism |
| **Usage**                  | Clear intention for persistence exclusion | May be less obvious for JPA use cases |
| **Serialization**          | Still included in Java serialization     | Excluded from Java serialization     |

---

#### Which Should You Use?

- Use **`@Transient`** when working explicitly with JPA and database-related code. It clearly communicates the intention to exclude the field from persistence.
- Use **`transient`** when dealing with non-persistence scenarios, such as object serialization, or when you want to combine both JPA exclusion and serialization exclusion.

---

#### Example Implementation

Here’s how you can combine both approaches for a `debugString` field:

```java
@Entity
public class Employee {
    @Id
    private int id;

    private String name;

    private Date dob;

    private EmployeeType employeeType;

    @Transient // JPA will ignore this field
    private transient String debugString; // Also excluded from serialization
}
```

With this setup:
- `debugString` will not appear in the database schema or be persisted by JPA.
- It will also be excluded if the `Employee` object is serialized (e.g., during Java serialization to a file or stream).


# Deep Dive into `@Id` Annotation in JPA

The `@Id` annotation marks a property as the **primary key** of a table. It ensures that the property is **unique** and **not null**. Below are some key points to consider:

## Supported Types for `@Id`
- **Primitive types** (e.g., `int`, `long`) can be used as primary keys.
- **Wrapper classes** (e.g., `Integer`, `Long`) are also valid for primary keys.
- **Strings** can be primary keys, but they may lead to performance implications.

### Note:
Using `long` as an ID is **not recommended** because it is not a **persistent type** and can have issues with **decimal points**.

---

## Automating ID Generation with `@GeneratedValue`

If you don't want to manually set the primary key, you can delegate the responsibility to the database using `@GeneratedValue`. Example:

```java
@Id
@Column(name = "id")
@GeneratedValue
private int id;
```

When this is configured, JPA in conjunction with the database will handle primary key generation. The ID will still be associated with the entity in the database.

---

### Strategies for `@GeneratedValue`

The `@GeneratedValue` annotation allows specifying strategies for ID generation. Here are the available strategies:

1. **AUTO**: 
   - The database decides the strategy to use based on the DB driver's specification.

2. **SEQUENCE**: 
   - The database maintains a **sequence object**.
   - For every new insert, it uses the sequence value and increments it for the next usage.
   - Example: A sequence object named `hibernate_sequence` is generated to keep track of IDs.
   - ![Sequence Table](https://github.com/user-attachments/assets/39222466-65aa-47b3-b9b7-1d815dea6acb)

3. **TABLE**:
   - A separate table is created in the database to keep track of the ID values.
   - This table is updated for every new ID generated.
   - ![Table Generation](https://github.com/user-attachments/assets/0d1b42de-1e57-468d-ab3d-ceb929314540)

4. **IDENTITY**:
   - Relies on the database's built-in **auto-increment** feature.
   - The database automatically generates a new ID for each insert operation.
   - Commonly used with databases like MySQL, SQL Server, and PostgreSQL that support auto-increment columns.
   - No additional tracking tables or sequences are required, as the ID is generated directly in the table itself.

---

## Best Practices
- In most cases, **AUTO** is preferred as JPA can determine the appropriate strategy based on the database.

Before diving into CRUD operations, we need to make changes to our `persistence.xml` file.

---

## Current Configuration in `persistence.xml`

The property currently set in `persistence.xml` is:

```xml
<property name="hibernate.hbm2ddl.auto" value="create-drop"/>
```

### What `create-drop` Does:
- **At application startup**: Drops the entity-related table if it exists, then creates it again.
- **At persistence context closure**: Drops the table.

This behavior is not desirable for applications where we want to maintain data across application restarts.

---

## Alternative Values for `hibernate.hbm2ddl.auto`

Here are the possible values for the `hibernate.hbm2ddl.auto` property and their behavior:

1. **validate**:
   - Verifies if the entity definitions in Java match the table definitions in the database.
   - Does **not** create, drop, or modify tables.
   - Assumes the database schema already exists.
   - Useful for enterprise applications where the database schema is pre-defined.

2. **update**:
   - Does **not** drop the table.
   - Updates the table schema when necessary.
     - Example: If the entity column length is updated from 50 to 100, this change will reflect in the database table.
   - Does **not** delete existing data.

3. **create**:
   - Similar to `create-drop`, but:
     - Drops the table at the start of the application.
     - Creates the table again.
     - **Does not drop the table** when the persistence context is closed.

4. **none**:
   - Performs no actions.
   - Does not create, drop, or validate tables.

---

## Closing the Persistence Context

To properly manage resources, always close the persistence context when you're done:

```java
entityManager.close();
entityManagerFactory.close();
```

This ensures efficient resource management and avoids potential memory leaks.

---

## Recommended Setting for CRUD Operations

To understand CRUD operations and avoid losing data, set the property to **update**:

```xml
<property name="hibernate.hbm2ddl.auto" value="update"/>
```

With this configuration:
- The database schema will be updated as needed.
- Existing data will remain intact.

# Reading Employee Instances from the Database with JPA

In this guide, we'll learn how to read persisted employee instances from the database using JPA. The process involves utilizing the `EntityManager` to fetch data from the database.

---

## Steps for Reading Data

### 1. Create an `EntityManagerFactory`
The `EntityManagerFactory` is created based on the configuration in `persistence.xml`. 

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
```

### 2. Create an `EntityManager`
The `EntityManager` is created using the factory. It is responsible for managing entities and is required for performing any entity operations.

```java
EntityManager entityManager = entityManagerFactory.createEntityManager();
```

---

## Using the `find()` Method

To read an entity from the database, we use the `find()` method provided by `EntityManager`. 

### Syntax
```java
entityManager.find(EntityClass, id);
```

- **EntityClass**: The class of the entity you want to fetch.
- **id**: The primary key of the entity to be retrieved.

This method is analogous to SQL queries like:
```sql
SELECT * FROM employee WHERE id = 1;
```

### Example: Reading an Employee
```java
Employee employee = entityManager.find(Employee.class, 1);
```

- The above code fetches the `Employee` instance with ID `1` from the database.
- The `find()` method returns an entity instance that is retrieved from the database.

---

## Key Notes

- **EntityManager**: Always use it to perform entity operations. It manages the lifecycle of entity instances.
- **No Transactions Required**: For read operations, transactions are not necessary.


# Console output:

![image](https://github.com/user-attachments/assets/96abecf1-2b1b-4e57-81d9-dc475f983d5b)


**Note :** What if we give id , that does not exist ? The employee instance will be null.


# Updating Data in the Database with JPA

In this guide, we’ll explore how to update data in the database using JPA. The process involves fetching an entity, modifying it, and saving the changes back to the database.

---

## SQL Analogy for Update

In SQL, updating a record involves fetching the rows you want to modify and applying the changes. For example:

```sql
UPDATE employee_data SET age = 20 WHERE id = 1;
```

Similarly, in Java, you:
1. Fetch the entity you want to update using the `find()` method.
2. Modify the entity by calling setters.
3. Persist the changes and commit the transaction.

---

## Steps for Updating an Entity in JPA

### 1. Fetch the Entity to Update
Use the `find()` method to retrieve the entity you want to modify.

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();
Employee employee = entityManager.find(Employee.class, 1);
```

### 2. Modify the Entity
Call the appropriate setter methods to make changes to the fetched entity.

```java
employee.setEmployeeType(EmployeeType.FULLTIME);
```

At this point, the entity is modified in memory but not yet saved to the database.

### 3. Persist the Changes
To save the updated entity to the database:
1. Start a transaction.
2. Use the `persist()` method.
3. Commit the transaction.
4. Close the `EntityManager` and `EntityManagerFactory`.

```java
EntityTransaction transaction = entityManager.getTransaction();
transaction.begin();
        
entityManager.persist(employee);  // Updates the existing entity in the database.
        
transaction.commit();
entityManager.close();
entityManagerFactory.close();
```

---

## How JPA Identifies an Existing Entity

When using `persist()`, JPA checks if the entity already exists in the database:
- It looks at the **primary key** of the entity.
- If the entity exists (i.e., the primary key is present in the database), it updates the record instead of inserting a new one.

---

## Key Points

- Always start a **transaction** for update operations.
- JPA uses the **primary key** to determine if the entity already exists in the database.
- Closing the `EntityManager` and `EntityManagerFactory` is necessary to release resources.


# Deleting Data in the Database with JPA

In this guide, we’ll learn how to delete records from the database using JPA. The process involves finding the entity to delete and instructing the `EntityManager` to remove it.

---

## SQL Analogy for Delete

In SQL, deleting a record involves selecting the rows you want to delete and performing a `DELETE` operation. For example:

```sql
DELETE FROM employee_data WHERE id = 1;
```

Similarly, in JPA:
1. Use the `find()` method to retrieve the entity you want to delete.
2. Use the `remove()` method of the `EntityManager` to delete the entity.

---

## Steps for Deleting an Entity in JPA

### 1. Fetch the Entity to Delete
Retrieve the entity using the `find()` method.

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Employee employee = entityManager.find(Employee.class, 1);
```

### 2. Start a Transaction
Since deleting a record involves modifying the database, a transaction is required.

```java
EntityTransaction transaction = entityManager.getTransaction();
transaction.begin();
```

### 3. Delete the Entity
Use the `remove()` method of the `EntityManager` to delete the fetched entity.

```java
entityManager.remove(employee);
```

### 4. Commit the Transaction and Close Resources
Commit the transaction and close the `EntityManager` and `EntityManagerFactory`.

```java
transaction.commit();
entityManager.close();
entityManagerFactory.close();
```

---

## Complete Example: Deleting an Employee

Below is a complete example of deleting an employee with ID `1`:

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Employee employee = entityManager.find(Employee.class, 1);

EntityTransaction transaction = entityManager.getTransaction();
transaction.begin();

entityManager.remove(employee);

transaction.commit();
entityManager.close();
entityManagerFactory.close();
```

---

## Key Points

- **`find()` Method**: Used to retrieve the entity you want to delete.
- **`remove()` Method**: Deletes the entity from the database.
- **Transaction Required**: Deleting data involves modifying the database, so a transaction must be started and committed.
- **Primary Key**: JPA uses the primary key to identify the entity in the database.



### Understanding Relationships Between Entities

To understand how relationships work between entities, we need at least two entities. In this note, we will create a new entity to demonstrate the relationship. Let's create an **Access Card** entity, where each employee has exactly one access card.

#### AccessCard Entity

Here is the definition of the `AccessCard` entity:

```java
@Entity
public class AccessCard {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int id;

    private Date issuedDate;
    private boolean isActive;
    private String firmwareVersion;
}
```

#### Key Points:
- **Entity**: `AccessCard` represents the access card of an employee.
- **Attributes**:
  - `id`: Unique identifier for the access card.
  - `issuedDate`: The date when the card was issued.
  - `isActive`: Indicates whether the access card is active or not.
  - `firmwareVersion`: The firmware version of the access card.
  
#### Next Steps:
To establish a relationship between `AccessCard` and another entity (e.g., `Employee`), we will need to define the mapping in the next steps.

# Mapping Employee to AccessCard in JPA
Let's explore how to map a relationship between two entities: `Employee` and `AccessCard`. We'll start by looking at the database (DB) perspective and then move to how we can implement the relationship using JPA (Java Persistence API).

## DB Perspective: How to Associate Employee with AccessCard

To establish a relationship between `Employee` and `AccessCard` in the database, we need to add a foreign key reference. There are multiple ways to achieve this, but let's look at the simple approach where we add the `accessCardId` to the `Employee` table.

### 1. No Foreign Key - Just Matching Values

In a scenario where there is no foreign key, we can store the `AccessCard` ID in the `Employee` entity, as shown below:

```java
private int accessCardId;

public int getAccessCardId() {
    return accessCardId;
}

public void setAccessCardId(int accessCardId) {
    this.accessCardId = accessCardId;
}
```

In the code where we create an `Employee` instance and associate it with an `AccessCard`:

```java
AccessCard accessCard1 = new AccessCard();
accessCard1.setActive(true);
accessCard1.setFirmwareVersion("1.0.0");
accessCard1.setIssuedDate(new Date());
accessCard1.setId(10);

Employee employee1 = new Employee();
employee1.setName("Bob");
employee1.setDob(new Date());
employee1.setEmployeeType(EmployeeType.LEAVE);
employee1.setAccessCardId(accessCard1.getId());
```

At this point, the database will store the `accessCardId` in the `Employee` table. However, this does **not** create a true relationship between `Employee` and `AccessCard`. If the `AccessCard` is deleted, the reference in the `Employee` table will still exist, leading to potential inconsistency.

### 2. Missing Relationship: Java Perspective

From a Java perspective, the `Employee` and `AccessCard` are separate instances. By only assigning the `accessCardId`, we're not establishing a true relationship between them. This can cause issues when we try to perform operations like cascading deletes or fetching related data. 

What if the `accessCardId` is auto-generated in the database? How will we assign it to the `Employee`? We need a stronger link between these two entities.

---

## JPA Perspective: Establishing the Relationship

Let's now move to JPA and see how we can establish a true relationship between `Employee` and `AccessCard`.

### 1. Using JPA Relationships

In Java, instead of using a primitive `int` to represent the `AccessCard`, we can use the `AccessCard` entity directly. This way, we're linking the two entities properly and telling JPA to handle the relationship.

First, we remove the `accessCardId` property from the `Employee` entity and introduce a reference to the `AccessCard` entity:

```java
// The actual card allocated for this employee
private AccessCard accessCard;

public AccessCard getAccessCard() {
    return accessCard;
}

public void setAccessCard(AccessCard accessCard) {
    this.accessCard = accessCard;
}
```

Now, when creating an `Employee` and linking it with an `AccessCard`, we do it like this:

```java
AccessCard accessCard1 = new AccessCard();
accessCard1.setActive(true);
accessCard1.setFirmwareVersion("1.0.0");
accessCard1.setIssuedDate(new Date());

Employee employee1 = new Employee();
employee1.setName("Bob");
employee1.setDob(new Date());
employee1.setEmployeeType(EmployeeType.LEAVE);
employee1.setAccessCard(accessCard1);
```

This establishes a true relationship where the `Employee` has an `AccessCard`. However, JPA still doesn't know how to map this relationship to the database.

---

### 2. Foreign Key and Relationship Mapping in JPA

We need to tell JPA that the `AccessCard` in the `Employee` entity represents a relationship and that `AccessCard` is a separate entity in its own right. This can be done using JPA annotations.

Since this is a one-to-one relationship (one employee can have one access card, and one access card is assigned to one employee), we use the `@OneToOne` annotation in the `Employee` entity:

```java
@OneToOne
private AccessCard accessCard;
```

This annotation tells JPA that the `AccessCard` is a separate entity and the relationship between `Employee` and `AccessCard` should be represented in the database with a foreign key.

---

### 3. JPA DDL Output

When JPA processes this mapping, it will generate the necessary database schema. The resulting `Employee` table will have a foreign key reference to the `AccessCard` table. Here is an example of the generated DDL (Data Definition Language):

```sql
Hibernate: 
    create table AccessCard (
       id integer not null,
        firmwareVersion varchar(255),
        isActive boolean not null,
        issuedDate timestamp,
        primary key (id)
    )

Hibernate: 
    create table EMPLOYEE_DATA (
       id integer not null,
        dob date,
        employeeType varchar(255),
        name varchar(255),
        accessCard_id integer,
        primary key (id)
    )

Hibernate: 
    alter table EMPLOYEE_DATA 
       add constraint FK7wgy5gh29n8s1ye66koxyfjja 
       foreign key (accessCard_id) 
       references AccessCard
```

Here, the `AccessCard` table is created, and the `EMPLOYEE_DATA` table is created with a foreign key constraint linking `accessCard_id` to `AccessCard`'s `id`.

---

## Conclusion

By using JPA annotations like `@OneToOne`, we've established a true relationship between `Employee` and `AccessCard`. JPA handles the foreign key mapping for us and ensures that both entities are linked properly. This relationship can now be used for various operations like cascading deletes, fetch operations, and maintaining data integrity between the two entities.

# Implications of Relationships When Fetching Data in JPA

When dealing with relationships in JPA, fetching data becomes a critical aspect. Unlike standalone entities, fetching related entities introduces nuances. Understanding these is key to ensuring efficient data retrieval and avoiding unnecessary database operations.

---

## Fetching Data with Relationships

### Example: Fetching an `Employee` with a One-to-One Relationship

Consider an `Employee` entity with a one-to-one relationship with `AccessCard`. When we fetch an `Employee` from the database:

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Employee employee = entityManager.find(Employee.class, 3);
System.out.println(employee);
```

Output:

```plaintext
Employee{id=3, name='Bob', dob=2024-12-07, employeeType=LEAVE}
```

The `AccessCard` data is not printed because it was not included in the `toString()` method of the `Employee` entity. If we include it, the output will display the `AccessCard` details:

```plaintext
Employee{id=3, name='Bob', dob=2024-12-07, employeeType=LEAVE, accessCard=AccessCard{id=5, issuedDate=2024-12-07 12:16:17.76, isActive=true, firmwareVersion='1.0.0'}}
```

**Observation:**  
JPA automatically fetches both the `Employee` and its associated `AccessCard`. The SQL query executed by JPA demonstrates this:

```sql
Hibernate: 
    select
        employee0_.id as id1_1_0_,
        employee0_.acessCard_id as acesscar5_1_0_,
        employee0_.dob as dob2_1_0_,
        employee0_.employeeType as employee3_1_0_,
        employee0_.name as name4_1_0_,
        acesscard1_.id as id1_0_1_,
        acesscard1_.firmwareVersion as firmware2_0_1_,
        acesscard1_.isActive as isactive3_0_1_,
        acesscard1_.issuedDate as issuedda4_0_1_ 
    from
        EMPLOYEE_DATA employee0_ 
    left outer join
        AcessCard acesscard1_ 
            on employee0_.acessCard_id=acesscard1_.id 
    where
        employee0_.id=?
```

---

### Fetching Data Eagerly vs. Lazily

By default, JPA fetches relationships *eagerly*, which means it retrieves related entities automatically when the parent entity is fetched. This behavior is convenient in some cases but can lead to performance issues if the parent entity has relationships with multiple other entities.

#### Scenario: Avoid Eager Fetching

If you only need the parent entity (e.g., `Employee`) and don’t want the related entity (e.g., `AccessCard`) data to be fetched automatically, you can use *lazy fetching*. This ensures related data is fetched only when explicitly accessed.

```java
@OneToOne(fetch = FetchType.LAZY)
private AccessCard accessCard;
```

With lazy fetching, the `AccessCard` data will only be retrieved when you call `employee.getAccessCard()`. This reduces the number of queries and optimizes performance.

---

### Importance of Lazy Fetching in One-to-Many Relationships

Lazy fetching is particularly important in relationships like **One-to-Many**, where one entity (e.g., `Department`) is related to multiple child entities (e.g., `Employees`). If the `Department` has hundreds of employees, eager fetching would load all employees even if only the department information is needed.

---

## Summary

- **Default Fetching**: JPA fetches relationships eagerly unless specified otherwise.
- **Eager Fetching**: Related entities are automatically retrieved with the parent entity.
  - Example: Fetching an `Employee` automatically retrieves its `AccessCard`.
- **Lazy Fetching**: Related entities are retrieved only when explicitly accessed.
  - Example: Use `FetchType.LAZY` to avoid unnecessary data retrieval.
- **One-to-Many**: Lazy fetching is critical to prevent loading large collections unnecessarily.

By understanding and configuring fetch types appropriately, you can optimize performance and control how relationships are handled during data retrieval.

---
# Understanding Relationship Ownership in JPA

In a relationship, the **direction of ownership** determines how JPA manages the entities and avoids circular fetches or redundant queries. This is particularly important in **bidirectional relationships**.

---

## Fetching Data and Ownership

### Example: Fetching an `AccessCard`

Previously, we saw that fetching an `Employee` also fetched its associated `AccessCard`. But what happens when we fetch an `AccessCard` and try to find the associated `Employee`?

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

AccessCard accessCard = entityManager.find(AccessCard.class, 5);
System.out.println(accessCard);
```

Output:

```plaintext
AccessCard{id=5, issuedDate=2024-12-07 12:16:17.76, isActive=true, firmwareVersion='1.0.0'}
```

Here, the `AccessCard` is fetched, but it doesn't have any reference to the associated `Employee`. This happens because the `AccessCard` entity does not yet have a property to identify the `Employee`.

---

## Establishing a Bidirectional Relationship

To fetch the `Employee` from an `AccessCard`, we need to add a reference to the `Employee` in the `AccessCard` entity.

### Updated `AccessCard` Entity:
```java
@OneToOne
private Employee employeeOwner;
```

### Updated Code to Establish Relationship:
```java
AccessCard accessCard1 = new AccessCard();
Employee employee1 = new Employee();

employee1.setAccessCard(accessCard1);
accessCard1.setEmployeeOwner(employee1);
```

This creates a **bidirectional relationship** where:
- The `Employee` references the `AccessCard`.
- The `AccessCard` references the `Employee`.

---

## The Problem: Circular Fetching

With the above setup, fetching either entity can lead to circular queries. For example, fetching an `AccessCard` will trigger a fetch for its associated `Employee`, which will in turn fetch the `AccessCard` again. This results in unnecessary queries, as shown below:

```sql
Hibernate: 
    select
        accesscard0_.id as id1_0_0_,
        accesscard0_.employeeOwner_id as employee5_0_0_,
        accesscard0_.firmwareVersion as firmware2_0_0_,
        accesscard0_.isActive as isactive3_0_0_,
        accesscard0_.issuedDate as issuedda4_0_0_,
        employee1_.id as id1_1_1_,
        employee1_.accessCard_id as accesscar5_1_1_,
        employee1_.dob as dob2_1_1_,
        employee1_.employeeType as employee3_1_1_,
        employee1_.name as name4_1_1_,
        accesscard2_.id as id1_0_2_,
        accesscard2_.employeeOwner_id as employee5_0_2_,
        accesscard2_.firmwareVersion as firmware2_0_2_,
        accesscard2_.isActive as isactive3_0_2_,
        accesscard2_.issuedDate as issuedda4_0_2_ 
    from
        AccessCard accesscard0_ 
    left outer join
        EMPLOYEE_DATA employee1_ 
            on accesscard0_.employeeOwner_id=employee1_.id 
    left outer join
        AccessCard accesscard2_ 
            on employee1_.accessCard_id=accesscard2_.id 
    where
        accesscard0_.id=?
```

You might be wondering, why did it not cause an infinite loop ? 

**Why Doesn’t It Cause an Infinite Loop?**
- Persistence Context Prevents Infinite Queries
- JPA (Hibernate) tracks entities within the persistence context. Once an entity is loaded, JPA doesn’t fetch it again.
```
Example:
You fetch AccessCard, and it triggers a fetch for Employee.
When Hibernate tries to fetch AccessCard again from Employee, it recognizes that the AccessCard entity is already in the persistence context.
Result: It stops querying the database and simply returns the already-fetched object.
```

---

## Solution: Define Ownership with `mappedBy`

To avoid circular fetching, we need to define the **owner of the relationship**. This is done using the `mappedBy` attribute. The entity owning the relationship directly manages the foreign key.

### Updated Entities:

#### `AccessCard` Entity:
```java
@Entity
public class AccessCard {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int id;

    private Date issuedDate;
    private boolean isActive;
    private String firmwareVersion;

    @OneToOne(mappedBy = "accessCard")
    private Employee employeeOwner;
}
```

#### `Employee` Entity:
```java
@Entity
@Table(name = "EMPLOYEE_DATA")
public class Employee {

    @Id
    @GeneratedValue
    private int id;

    @Column(name = "name")
    private String name;

    @Temporal(TemporalType.DATE)
    private Date dob;

    @OneToOne
    private AccessCard accessCard;
}
```

### Explanation:

- The `mappedBy` attribute in `AccessCard` tells JPA that the `Employee` entity owns the relationship.
- When fetching an `Employee`, JPA knows the `AccessCard` reference in `AccessCard` is already represented by the `accessCard` property in `Employee`.
- This avoids circular fetching.

---

If **AccessCard is not the owning side**, how does it still know which Employee it belongs to when we call `accessCard.getEmployeeOwner()`?  

Let’s break it down **step by step** in the simplest way possible. 🚀  

---

### **Step 1: Who Actually Stores the Relationship?**
- **Employee** is the **owning side**, so it has the actual foreign key in the database.
- **AccessCard** is just referring to `Employee`, but it doesn’t store the relationship directly.

Here’s how the `Employee` table is structured:  
```sql
EMPLOYEE_DATA Table
+----+-------+--------------+
| id | name  | accessCard_id |
+----+-------+--------------+
| 1  | John  | 101          |
| 2  | Alice | 102          |
+----+-------+--------------+
```
- This means **Employee knows which AccessCard it owns**.

Now, the `AccessCard` table **does NOT store any reference to Employee**:
```sql
ACCESS_CARD Table
+-----+------------+---------+
| id  | firmware   | isActive |
+-----+------------+---------+
| 101 | v1.2.3     | true    |
| 102 | v1.2.4     | false   |
+-----+------------+---------+
```
---

### **Step 2: What Happens When We Fetch an AccessCard?**
#### **Fetching AccessCard First**
```java
AccessCard accessCard = entityManager.find(AccessCard.class, 101);
Employee owner = accessCard.getEmployeeOwner();
System.out.println(owner.getName());
```
**How does Hibernate get the Employee when AccessCard doesn't store it?**  

1️⃣ **Hibernate Sees the `mappedBy = "accessCard"`**  
   - It understands **"Wait, the Employee table has a foreign key pointing to me!"**  
   - So, it **knows where to look for the Employee**.

2️⃣ **Lazy or Eager Fetch?**
   - If **`FetchType.EAGER`** (default for `@OneToOne`):
     - Hibernate **immediately** fetches the `Employee` when loading `AccessCard`.
     - SQL:
       ```sql
       SELECT a.*, e.* 
       FROM AccessCard a
       LEFT JOIN EMPLOYEE_DATA e ON e.accessCard_id = a.id
       WHERE a.id = 101;
       ```
     - Since `employeeOwner` is loaded along with `AccessCard`, calling `getEmployeeOwner()` just returns the already-loaded object.

   - If **`FetchType.LAZY`**:
     - Hibernate **only fetches `AccessCard` first**.
     - When `accessCard.getEmployeeOwner()` is called, **a new SQL query runs**:
       ```sql
       SELECT * FROM EMPLOYEE_DATA WHERE accessCard_id = 101;
       ```
     - Hibernate then links the found `Employee` to the `AccessCard` in memory.

---

### **Step 3: So, Why Can AccessCard Still Access Employee?**
Even though `AccessCard` does **not store a foreign key**, Hibernate **knows how to find Employee** because of:  

✅ **The `mappedBy = "accessCard"` mapping** → tells Hibernate that Employee is the owner.  
✅ **The foreign key in `Employee` table** → Employee stores the relationship, so Hibernate queries it when needed.  
✅ **Lazy or Eager fetching rules** → Depending on fetch type, Hibernate either **loads Employee immediately** or **fetches it later**.  

---

### **Final Answer:**
📝 **Even though AccessCard doesn’t own the relationship, Hibernate uses the `mappedBy` knowledge and looks into Employee's table to find the associated Employee when needed.**  

# Understanding One-to-Many and Many-to-One Relationships in JPA

In JPA, a **One-to-Many** relationship and a **Many-to-One** relationship are essentially the same thing, but their direction determines which entity owns the relationship. These relationships are commonly used when one entity is associated with multiple instances of another entity. Let's dive into the concept with an example of an **Employee** and their **Payslips**.

---

## Example: Employee and Payslip Relationship

### The Concept

An **Employee** can have multiple **Payslips**, and each **Payslip** belongs to one **Employee**. This represents a **One-to-Many** relationship from the **Employee** side and a **Many-to-One** relationship from the **Payslip** side.

### `Payslip` Entity

Let’s start by defining the `Payslip` entity:

```java
@Entity
public class Payslip {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int id;

    private Date payPeriodStart;

    private Date payPeriodEnd;

    private float salary;

    @ManyToOne
    private Employee employee;
}
```

In this case:
- The `Payslip` entity has a reference to the `Employee` entity.
- **Many `Payslip` entities belong to one `Employee` entity**. Hence, we use the `@ManyToOne` annotation on the `employee` field.


## How Foreign Key is Managed in the Database

### One-to-Many Relationship in the Database

In a **One-to-Many** relationship, the **"many" side** of the relationship holds the **foreign key**. This means that in the **Payslip** table, there will be an `employee_id` column that references the `Employee` table. This is because multiple `Payslips` can be associated with one `Employee`, but we don't want to repeat the `Employee` data in the `Payslip` table.

### Why Not a Foreign Key in the Employee Table?

Unlike the **Employee and AccessCard** relationship, where we had a foreign key in the **Employee** table, in a **One-to-Many** relationship, we can't store multiple foreign keys in the **Employee** table because that would break normalization. 

Instead, the **Payslip** table holds the foreign key (`employee_id`), ensuring the database remains normalized.

---

## Working with the Relationship in Code

### Setting up the Relationship

To associate a `Payslip` with an `Employee`, you set the `Employee` reference in the `Payslip` entity.

```java
Payslip payslip1 = new Payslip();
payslip1.setSalary(70000);
payslip1.setPayPeriodStart(new Date());
payslip1.setPayPeriodEnd(new Date());
payslip1.setEmployee(employee1);
```

This way, you can assign an `Employee` to a `Payslip` object. Since the `Payslip` entity already knows the `Employee` via the `employee` field, JPA will automatically insert the foreign key in the `Payslip` table.

### Fetching Payslip and it's associated Employee

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Payslip payslip = entityManager.find(Payslip.class, 5);
System.out.println(payslip.getEmployee());
```

This fetches the `playslip` and its associated `Employee`.

---

## Summary

- **One-to-Many** and **Many-to-One** relationships represent the same concept, but the direction of the relationship differs.
  - **One-to-Many**: One entity is associated with multiple entities (e.g., one `Employee` can have many `Payslips`).
  - **Many-to-One**: Many entities are associated with a single entity (e.g., each `Payslip` belongs to one `Employee`).
- In a **One-to-Many** relationship, the **"many" side** (e.g., `Payslip`) holds the **foreign key** to maintain database normalization.
- The `@ManyToOne` annotation is used on the **"many" side**, and the `@OneToMany` annotation is used on the **"one" side**.

This is the foundation of how **One-to-Many** and **Many-to-One** relationships work in JPA, especially in the context of associating entities like `Employee` and `Payslip`.

---

In JPA, to retrieve the **Payslips** associated with an **Employee**, you can follow a similar approach as we discussed earlier for accessing relationships, but with a focus on the **One-to-Many** side.

Let's walk through this with an example based on your given scenario.

---

## Fetching Payslips for an Employee

### Step 1: Mapping the Payslips to the Employee

As you mentioned, we can map the **Payslips** to the **Employee** using the `@OneToMany` relationship in the `Employee` entity. The `mappedBy` attribute tells JPA that the relationship is maintained by the `employee` field in the **Payslip** entity.

### Employee Entity

```java
@Entity
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int id;

    private String name;

    @OneToMany(mappedBy = "employee")
    private List<Payslip> payslips;
}
```

In the above code:
- The `mappedBy = "employee"` refers to the `employee` field in the **Payslip** entity, indicating that the **Employee** is the "one" side of the relationship, and **Payslip** is the "many" side.

### Step 2: Creating Payslips and Associating them with the Employee

When you create **Payslip** instances and associate them with an **Employee**, you do it as follows:

```java
Payslip payslip1 = new Payslip();
Payslip payslip2 = new Payslip();
payslip1.setSalary(70000);
payslip2.setSalary(75000);
payslip1.setPayPeriodStart(new Date());
payslip2.setPayPeriodStart(new Date());
payslip1.setPayPeriodEnd(new Date());
payslip2.setPayPeriodEnd(new Date());
payslip1.setEmployee(employee1);
payslip2.setEmployee(employee1);

List<Payslip> employee1PaySlips = List.of(payslip1, payslip2); 
employee1.setPayslips(employee1PaySlips);//ensures both sides are in sync (not required for Hibernate, but useful for logic).
```

### Step 3: Fetching the Payslips of an Employee

To retrieve the **Payslips** associated with an **Employee**, you simply fetch the **Employee** entity and access its `payslips` property, as shown below:

```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Employee employee = entityManager.find(Employee.class, 1);
employee.getPayslips().forEach(System.out::println);
```

### What Happens Internally?

- When you call `entityManager.find(Employee.class, 1)`, JPA retrieves the **Employee** entity with `id = 1` from the database.
- The `@OneToMany(mappedBy = "employee")` annotation ensures that the list of **Payslips** associated with this employee is fetched.
- The **Payslips** are fetched based on the foreign key `employee_id` in the **Payslip** table (the "many" side), which links back to the **Employee** entity.
  
### Output

After fetching the employee's payslips, the payslips will be printed. The output might look like:

```
Payslip{id=1, payPeriodStart=2024-12-01, payPeriodEnd=2024-12-31, salary=70000}
Payslip{id=2, payPeriodStart=2024-11-01, payPeriodEnd=2024-11-30, salary=75000}
```

Each payslip will have details such as its **pay period**, **salary**, and so on.

---

## Summary

- The **Employee** entity holds a list of **Payslips**, and you use the `@OneToMany` annotation to represent the relationship from the **Employee** side.
- The `mappedBy` attribute tells JPA which field owns the relationship on the **Payslip** side (in this case, it's the `employee` field).
- When you fetch an **Employee** entity, you can access its associated **Payslips** by calling the `getPayslips()` method.
- The **Payslips** are fetched based on the foreign key in the **Payslip** table, which points to the **Employee** entity.

This approach helps maintain the integrity of the relationship and ensures that JPA handles the relationship mapping efficiently.




# Lets first understand how does mapped by work ?
### How are we able to get the employee of an AccessCard when, there is not foreign key in the AcessCard table.

When the `AccessCard` table does not have a foreign key to reference the `Employee` table, JPA relies on the `mappedBy` configuration to manage the relationship in memory and during database queries. Here's how JPA ensures the `AccessCard` knows about the `Employee` when data is flushed to the database and accessed again:

---

### **How Relationships Work Without a Foreign Key in the `AccessCard` Table**

1. **MappedBy Role in JPA:**
   The `mappedBy` attribute in the `AccessCard` entity:
   ```java
   @OneToOne(mappedBy = "accessCard")
   private Employee employeeOwner;
   ```
   informs JPA that this relationship is controlled by the `Employee` entity, specifically its `accessCard` property. This means the `AccessCard` table itself does not need a foreign key column. Instead, the `Employee` table holds the foreign key (e.g., `access_card_id`).

2. **Database Schema:**
   - **`Employee` table**: Has a column like `access_card_id`, representing the foreign key to the `AccessCard` table.
   - **`AccessCard` table**: Does not have any reference to `Employee`. 

3. **How JPA Resolves the Relationship:**
   When JPA queries the database, it uses the mapping information from the `mappedBy` attribute to fetch the relationship. For example:
   - When you load an `AccessCard`, JPA knows that the `employeeOwner` is not directly represented in the `AccessCard` table.
   - Instead, it checks the `Employee` table to find an employee where `access_card_id` matches the current `AccessCard`'s primary key.

   This process is typically handled through a **join query** behind the scenes.

---

### **What Happens During Flush and Reload?**

When you flush the data to the database and reload it, JPA ensures the relationship is correctly established based on the owner-side configuration (`Employee`). Here's the process:

1. **Flush to Database:**
   - When you call `employee1.setAccessCard(accessCard1)`, JPA updates the `access_card_id` column in the `Employee` table to reference the primary key of the `AccessCard`.
   - No changes are made to the `AccessCard` table itself.

2. **Reload Entities:**
   - When you fetch the `AccessCard` entity again (e.g., `entityManager.find(AccessCard.class,id)`), JPA uses the mapping configuration to retrieve the associated `Employee`:
     - It executes a query like:  
       ```sql
       SELECT e.* , a.*
       FROM Employee e 
       JOIN AccessCard a ON e.access_card_id = a.id 
       WHERE a.id = :accessCardId;
       ```
   - JPA populates the `employeeOwner` field in the `AccessCard` entity based on the query result.

---

### **Why Doesn't the `AccessCard` Table Need a Foreign Key?**

The `AccessCard` table does not need a foreign key because:
1. The relationship is **owned by the `Employee` entity**, and the `access_card_id` column in the `Employee` table fully represents this association.
2. The `AccessCard` entity's `employeeOwner` field is a **logical inverse reference**, resolved at runtime by JPA using the `mappedBy` attribute.

---

### **Illustrative Example**

#### Database State After Persistence:
- `Employee` table:
   | id  | name      | access_card_id |
   |------|-----------|----------------|
   | 1    | John Doe  | 101            |

- `AccessCard` table:
   | id  | card_number | issue_date  |
   |-----|-------------|-------------|
   | 101 | 12345       | 2024-12-01  |

#### Fetching `AccessCard` and Resolving Employee:
When you fetch an `AccessCard`:
```java
AccessCard accessCard = accessCardRepository.findById(101);
Employee employee = accessCard.getEmployeeOwner();
```
1. JPA performs a **join query** to find the associated `Employee`:
   ```sql
   SELECT e.*
   FROM Employee e
   JOIN AccessCard a ON e.access_card_id = a.id
   WHERE a.id = 101;
   ```
2. The result is used to populate the `employeeOwner` field in the `AccessCard` entity.

---
### Now that we understand the mappedBy feature of JPA, you might be questioning, well if mappedBy will let JPA take care of fetching the Employee of a AccessCard when we do:
```
AccessCard accessCard= entityManager.find(AccessCard.class,1);
accessCard.getEmployee();
```

Why do we need to do this while persisting the AccessCard and Employee Entity ?

```
AcessCard acessCard1 = new AcessCard();
Employee employee1 = new Employee();
employee1.setAccessCard(acessCard1);
acessCard1.setEmployee(employee1);
```

Why are we explicity setting the employee for the acess card, when JPA while finding the access card knows how to populate the Employee using the mappedBy feature.

### Let's understand why ?

### **Understanding the Problem**
In JPA, when you set up a bidirectional relationship between two entities, like `Employee` and `AccessCard`, the goal is to ensure that changes in one entity reflect consistently in the other during the application's runtime. Here, the `Employee` entity is the **owner of the relationship**, as specified by the `mappedBy` attribute on the `AccessCard` entity.

#### **MappedBy Attribute**
The `mappedBy` attribute in the `AccessCard` entity:
```java
@OneToOne(mappedBy = "accessCard")
private Employee employeeOwner;
```
instructs JPA that the relationship is controlled by the `accessCard` property in the `Employee` entity. This means JPA will look at the `Employee`'s `accessCard` field to determine the relationship. Essentially:
- **Owner side (`Employee`)**: Controls the relationship and manages the foreign key in the database.
- **Inverse side (`AccessCard`)**: Provides a view of the relationship but does not directly manage it.

---

### **Why Do We Need to Set Both Sides?**

1. **Setting the Relationship on the Owner Side:**
   When you call `employee1.setAccessCard(accessCard1)`, you are establishing the relationship on the **owner side**, making `Employee` recognize the `AccessCard`. This is **necessary** because only the owner side (`Employee`) determines how the relationship is persisted to the database. Without this, the database will not associate the two entities.

2. **Setting the Relationship on the Inverse Side:**
   When you call `accessCard1.setEmployee(employee1)`, you are establishing the relationship on the **inverse side**, making the `AccessCard` entity aware of its `Employee`. Although this step does not affect database persistence directly (since the inverse side does not control the relationship), it ensures that the relationship is **consistent in memory**.

---

### **What Happens if You Don’t Set the Inverse Side?**
If you do not explicitly set the relationship on the inverse side (`accessCard1.setEmployee(employee1)`), the following may happen:
1. **Before Flush/Commit:**
   JPA does not immediately write changes to the database. It may delay the flush to optimize performance. If, during this period, you try to access the `employeeOwner` property of the `AccessCard` entity, you will get `null`. This is because the inverse side (`employeeOwner`) has not been explicitly initialized, and JPA does not infer it from the owner side (`Employee.accessCard`) at this point.

2. **After Flush/Commit:**
   Once the persistence context is synchronized with the database (i.e., after flush or transaction commit), JPA will correctly populate both sides of the relationship. If you then access the `employeeOwner` from the `AccessCard`, it will work as expected. However, relying on this behavior introduces **inconsistent states** during the runtime, which can lead to bugs and hard-to-debug issues.

---

### **Consistency in Memory**
Explicitly setting the relationship on both sides ensures that the state of the objects in memory remains **consistent**:
```java
AccessCard accessCard1 = new AccessCard();
Employee employee1 = new Employee();

// Set the relationship on both sides
employee1.setAccessCard(accessCard1);
accessCard1.setEmployee(employee1);
```
Here’s what happens:
- `Employee` knows which `AccessCard` it owns.
- `AccessCard` knows which `Employee` owns it.
- During runtime, even before a flush or commit, both sides reflect the relationship accurately.

This is especially important in a **long-running transaction** where objects might be manipulated in memory before being flushed to the database.

---

### **Super Detailed Example**

Consider the following scenario:
1. **Setup Entities:**
   ```java
   AccessCard accessCard1 = new AccessCard();
   Employee employee1 = new Employee();
   ```
2. **Set Relationship Only on Owner Side:**
   ```java
   employee1.setAccessCard(accessCard1);
   ```
   If you now try to access `accessCard1.getEmployeeOwner()`, it will return `null` because the inverse side has not been explicitly set.

3. **Set Relationship on Both Sides:**
   ```java
   accessCard1.setEmployee(employee1);
   ```
   Now, both `employee1.getAccessCard()` and `accessCard1.getEmployeeOwner()` return the correct references, ensuring consistency in memory.

---

### **Key Takeaways**

1. **Bidirectional Consistency:** Always set the relationship on both sides (owner and inverse) to ensure consistent in-memory state.
2. **Database Persistence:** Only the owner side determines the database relationship. The inverse side is ignored for persistence.
3. **Avoid Null References:** Explicitly setting both sides prevents null references when accessing the relationship in-memory before flush or commit.

---

By explicitly setting both sides of the relationship, you reduce the chances of inconsistent data, null pointers, and unexpected behavior during the application's runtime.

### **Customizing Column Names for Relationships in JPA**

When mapping a column from the database to Java code, we typically use the `@Column` annotation for basic properties. For example:

```java
@Column(name = "salary")
private float salary;
```

This maps the `salary` column in the database to the `salary` property in the Java entity.

---

### **How to Customize Column Names for Relationships**

For relationship properties (e.g., `@ManyToOne`, `@OneToOne`), JPA by default:
- Detects the relationship.
- Creates a foreign key column in the owning table (e.g., `employee_id` for an `Employee` relation).

However, if the database schema already defines a custom column name for the foreign key, you can map it using the `@JoinColumn` annotation.

#### **Example: Customizing the Foreign Key Column**

Consider the `Payslip` entity with a `ManyToOne` relationship to the `Employee` entity:
```java
@Entity
public class Payslip {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int id;

    @Column(name = "salary")
    private float salary;

    @ManyToOne
    @JoinColumn(name = "payslip_for_emp") // Maps to the custom column in the database
    private Employee employee;
}
```

Here’s what happens:
- The `@JoinColumn` annotation is used to specify the name of the foreign key column.
- The `name = "payslip_for_emp"` parameter ensures that the `payslip_for_emp` column in the `Payslip` table is used as the foreign key for the `Employee` relationship.

---

### **Database Table Schema Example**

#### **Database Table: `Payslip`**
| id  | salary | payslip_for_emp |
|------|--------|-----------------|
| 1    | 50000  | 101             |
| 2    | 60000  | 102             |

#### **Database Table: `Employee`**
| id  | name      |
|-----|-----------|
| 101 | John Doe  |
| 102 | Jane Smith|

---

### **Key Points**
1. Use `@JoinColumn` for relationships to customize the foreign key column name.
2. Default behavior appends `_id` to the related entity’s name (e.g., `employee_id`).
3. The `@JoinColumn(name = "custom_column_name")` overrides this default mapping.

This ensures that your Java code maps correctly to an existing database schema with custom foreign key column names.
### Understanding Many-to-Many Relationships with an Example of Email Groups

#### Scenario
- **Problem Statement**: An employee can be part of multiple email groups, and an email group can have multiple employees. 
- **Entity without Relationships**: 

```java
@Entity
public class EmailGroup {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int groupId;

    private String groupName;
}
```

### Database Perspective
- **Comparison with One-to-Many Relationship**:
  - For a one-to-many relationship (e.g., Employee and Payslip):
    - The **Payslip table** keeps a foreign key referencing the **Employee table**.
  - One payslip belongs to one employee, so a single foreign key is sufficient.

- **For Many-to-Many Relationship**:
  - **Employee table** can't have a foreign key for groups (one employee can have multiple groups).
  - **EmailGroup table** can't have a foreign key for employees (one group can have multiple employees).
  - **Solution**: Create a separate mapping table to store the combination of both.

#### Mapping Table
The mapping table represents the many-to-many relationship:
```
Employee_Group_Mapping
+--------+----------+
| EMP_ID | GROUP_ID |
+--------+----------+
|   1    |    1     |
|   1    |    2     |
|   2    |    2     |
+--------+----------+
```
This shows:
- Employee 1 is part of groups 1 and 2.
- Employee 2 is part of group 2.

---

### Java Perspective
In Java, the many-to-many relationship is similar to a one-to-many relationship but bidirectional. 

#### Employee Entity
```java
@Entity
public class Employee {
    @ManyToMany
    private List<EmailGroup> emailGroups;
}
```

#### EmailGroup Entity
```java
@Entity
public class EmailGroup {
    @ManyToMany
    private List<Employee> employeeList;
}
```

---

### The Role of `mappedBy`
#### Why is `mappedBy` Required?
If you define the relationship without `mappedBy`, JPA creates **two separate mapping tables**:
1. One for the relationship from `Employee` to `EmailGroup`.
2. Another for the relationship from `EmailGroup` to `Employee`.

Example Code:
```java
EmailGroup emailGroup1 = new EmailGroup();
emailGroup1.setGroupName("Legacy Team");

EmailGroup emailGroup2 = new EmailGroup();
emailGroup2.setGroupName("Testing Team");

employee1.setEmailGroups(List.of(emailGroup1, emailGroup2));
emailGroup1.setEmployeeList(List.of(employee1));
emailGroup2.setEmployeeList(List.of(employee1));
```
- Without `mappedBy`, JPA doesn't understand these two are the same relationship, resulting in duplicate mapping tables.

#### How to Use `mappedBy`
- **Purpose**: To link the two relationships as one and avoid duplicate tables.
- **Placement**: It can be placed in either entity, as long as it points to the field in the other entity that owns the relationship.

Example:
```java
@ManyToMany(mappedBy = "emailGroups")
private List<Employee> employeeList;
```
Now, only **one mapping table** is created to track the relationship.

---

### Summary
- **Many-to-Many DB Design**:
  - Use a separate mapping table (e.g., `Employee_Group_Mapping`).
- **Java Implementation**:
  - Define `@ManyToMany` relationships in both entities.
  - Use `mappedBy` in one entity to avoid duplicate mapping tables.
- **Key Concept**: `mappedBy` ensures both sides of the relationship are treated as one by JPA.


Table summarizing the **fetch types** (`FetchType.LAZY` and `FetchType.EAGER`) for all types of relationships in JPA:

| **Relationship Type**       | **Default Fetch Type** | **Description**                                                                                                                                                             | **Use Cases for Fetch Type**                                                                                                                  |
|------------------------------|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **`@OneToOne`**              | `EAGER`               | A single entity is associated with another single entity.                                                                                                                   | - Use `LAZY` if the related entity is not always needed to optimize performance. <br>- Use `EAGER` if the relationship is critical and always used. |
| **`@ManyToOne`**             | `EAGER`               | Multiple entities are associated with a single entity (e.g., Many employees -> One department).                                                                              | - Default `EAGER` works well when the relationship is frequently accessed.<br>- Use `LAZY` if loading the related entity is not always required.    |
| **`@OneToMany`**             | `LAZY`                | A single entity is associated with multiple entities (e.g., One department -> Many employees).                                                                              | - Default `LAZY` is optimal for large collections.<br>- Use `EAGER` if the child entities are always accessed with the parent.                     |
| **`@ManyToMany`**            | `LAZY`                | Many entities are associated with many other entities (e.g., Many employees -> Many email groups).                                                                          | - Default `LAZY` is preferred for large datasets.<br>- Use `EAGER` only when it is certain that the data is always accessed together.              |


### **Customizing Join Table Name**
By default, JPA creates a join table with a system-generated name, usually combining the names of the two entities involved. To customize the table name:

- Use the **`@JoinTable` annotation**.
- Specify the desired table name with the `name` attribute.

Example:
```java
@ManyToMany
@JoinTable(name = "EMAIL_GROUP_SUBSCRIPTIONS")
private List<EmailGroup> emailGroups;
```
This creates a join table explicitly named `EMAIL_GROUP_SUBSCRIPTIONS`.

---

### **Customizing Join Columns**
The join table contains two foreign key columns:
1. **Owning side column (`joinColumns`)**: Represents the foreign key for the owning entity.
2. **Inverse side column (`inverseJoinColumns`)**: Represents the foreign key for the related (inverse) entity.

To customize the column names:
- Use the **`@JoinColumn` annotation** for each column.
- Specify:
  - `name` for the column name.
  - Other optional properties like `nullable`, `unique`, etc., if needed.

Example:
```java
@ManyToMany
@JoinTable(
    name = "EMAIL_GROUP_SUBSCRIPTIONS", 
    joinColumns = @JoinColumn(name = "EMPLOYEE_ID"), // FK for Employee
    inverseJoinColumns = @JoinColumn(name = "GROUP_ID") // FK for EmailGroup
)
private List<EmailGroup> emailGroups;
```

#### Breakdown:
- **`joinColumns`**:
  - Defines the column representing the foreign key for the owning side (`Employee`).
  - Customized to `EMPLOYEE_ID`.
- **`inverseJoinColumns`**:
  - Defines the column representing the foreign key for the inverse side (`EmailGroup`).
  - Customized to `GROUP_ID`.

---

### **Final Output in the Database**
The customized join table `EMAIL_GROUP_SUBSCRIPTIONS` will look like this:

| **EMPLOYEE_ID** | **GROUP_ID** |
|------------------|--------------|
| 1                | 1            |
| 1                | 2            |
| 2                | 2            |

---

### **Key Points**
1. **Owning Side**:
   - The side without `mappedBy` is the **owning side**.
   - The `@JoinTable` is defined here since it controls the relationship.

2. **Customization Options**:
   - Table name: Use `name` in `@JoinTable`.
   - Column names: Use `@JoinColumn` for `joinColumns` and `inverseJoinColumns`.

3. **Code Example**:
Complete example of a Many-to-Many relationship with customized join table and columns:
```java
@Entity
public class Employee {
    @ManyToMany
    @JoinTable(
        name = "EMAIL_GROUP_SUBSCRIPTIONS",
        joinColumns = @JoinColumn(name = "EMPLOYEE_ID"),
        inverseJoinColumns = @JoinColumn(name = "GROUP_ID")
    )
    private List<EmailGroup> emailGroups;
}

@Entity
public class EmailGroup {
    @ManyToMany(mappedBy = "emailGroups")
    private List<Employee> employees;
}
```
### **Updating Many-to-Many Relationships in JPA**

When updating a **Many-to-Many relationship** in JPA, the process involves modifying both sides of the relationship to ensure consistency and persisting the changes in a transaction.

---

### **Code Explanation**

```java
public static void main(String[] args) {

    EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
    EntityManager entityManager = entityManagerFactory.createEntityManager();

    // Fetch existing Employee and EmailGroup from the database
    Employee employee = entityManager.find(Employee.class, 1);
    EmailGroup emailGroup = entityManager.find(EmailGroup.class, 3);

    // Update the relationship on both sides
    employee.addEmailGroup(emailGroup);
    emailGroup.addEmployeeToEmailGroup(employee);

    // Begin the transaction
    EntityTransaction transaction = entityManager.getTransaction();
    transaction.begin();

    // Persist changes (optional, for entities already managed)
    entityManager.persist(employee);
    entityManager.persist(emailGroup);

    // Commit the transaction
    transaction.commit();
}
```

---

### **Key Points**

#### 1. **Fetching Entities**
- **`entityManager.find`**: Retrieves the `Employee` and `EmailGroup` objects from the database.
  - If either entity does not exist, `find` returns `null`.

#### 2. **Updating the Relationship**
- **Updating the owning side**:
  - Use a method like `addEmailGroup` in the `Employee` class to add the `EmailGroup` to the `emailGroups` collection.
- **Updating the inverse side**:
  - Similarly, use a method like `addEmployeeToEmailGroup` in the `EmailGroup` class to add the `Employee` to the `employeeList` collection.

#### 3. **Bidirectional Synchronization**
- Both sides of the relationship must be updated for consistency. 
- Helper methods ensure both `List<Employee>` and `List<EmailGroup>` reflect the same relationship.

#### 4. **Transaction Management**
- **Transaction Start**:
  - Use `transaction.begin()` to start a transaction.
- **Persisting Changes**:
  - For entities already in the persistence context (`managed` state), calling `persist` is optional.
  - Simply updating the object within the transaction will reflect changes in the database.
- **Transaction Commit**:
  - Use `transaction.commit()` to save all changes to the database.

---

### **Database Impact**
After committing the transaction:
- The join table (`EMAIL_GROUP_SUBSCRIPTIONS`) will be updated with a new row linking the `Employee` and `EmailGroup`.

| **EMPLOYEE_ID** | **GROUP_ID** |
|------------------|--------------|
| 1                | 3            |

---

### **Summary**
- Use bidirectional helper methods to update both sides of the relationship.
- Use transactions to persist changes atomically.
- Persisting already managed entities is optional; updating them within a transaction is sufficient.
- Always commit the transaction to save the updates.

### **Deleting Relationships in JPA**

When deleting an entity in JPA, the behavior depends on the type of relationship and any cascading or orphan removal annotations. Here’s a structured guide to understanding this:

---

### **Default Behavior Without Annotations**

1. **`@ManyToMany` Relationships**:
   - If an entity (e.g., `Employee`) is deleted:
     - The associated rows in the join table (e.g., `EMAIL_GROUP_SUBSCRIPTIONS`) are deleted automatically.
     - **No constraint violations occur** because the join table doesn't hold foreign key constraints to child tables.

2. **`@OneToMany` or `@ManyToOne` Relationships**:
   - If an entity (e.g., `Employee`) is deleted:
     - **Constraint violations** occur because child rows (e.g., `Payslip`) have foreign key constraints pointing to the parent (`Employee`).
     - By default, JPA does **not** cascade deletions to child entities.

3. **`@OneToOne` Relationships**:
   - Deleting one side of the relationship behaves as follows:
     - If the owning side is deleted, the related row (on the inverse side) remains, and its foreign key is set to `NULL`.
     - If the non-owning side is deleted, a **constraint violation** may occur if the database schema doesn't allow the foreign key to be `NULL`.

---

### **Customizing Deletion Behavior**

#### 1. **Cascade Deletion**
- Use **`cascade = CascadeType.REMOVE`** to ensure related entities are deleted when the parent is deleted.
- Example:
    ```java
    @Entity
    public class Payslip {
        @ManyToOne(cascade = CascadeType.REMOVE) // Cascade removal of Payslip when Employee is deleted
        @JoinColumn(name = "payslip_for_emp")
        private Employee employee;
    }
    ```

    **Effect**:
    - When an `Employee` is deleted, all related `Payslip` entries are also deleted.

---

#### 2. **Orphan Removal**
- Use **`orphanRemoval = true`** to delete child entities that are no longer associated with the parent.
- Example:
    ```java
    @Entity
    public class Employee {
        @OneToMany(mappedBy = "employee", orphanRemoval = true)
        private List<Payslip> payslips;
    }
    ```
    **Effect**:
    - If a `Payslip` is removed from the `Employee.payslips` list, it will be automatically deleted from the database.

---

#### 3. **No Cascade or Orphan Removal (Tracking Case)**
- For entities you want to retain (e.g., `Payslip`, `AccessCard`), simply do **not** configure cascade or orphan removal:
    ```java
    @Entity
    public class Payslip {
        @ManyToOne
        @JoinColumn(name = "payslip_for_emp")
        private Employee employee;
    }
    ```

    **Effect**:
    - Deleting an `Employee` will throw a constraint violation because `Payslip` still references it. 
    - This is useful for historical data (e.g., keeping payroll records after an employee leaves).

---

#### Deleting an Employee:
```java
EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();

Employee employee = entityManager.find(Employee.class, 1);

EntityTransaction transaction = entityManager.getTransaction();
transaction.begin();
entityManager.remove(employee); // Automatically deletes Payslips and updates Join Table
transaction.commit();
```

---

### **Behavior Summary Table**

| **Relationship**            | **Default Behavior**                                | **With `CascadeType.REMOVE`**                  | **With `orphanRemoval = true`**                     |
|-----------------------------|----------------------------------------------------|-----------------------------------------------|----------------------------------------------------|
| **`@ManyToMany`**            | Deletes rows in join table automatically.         | No effect (join table rows are auto-managed). | Not applicable.                                   |
| **`@OneToMany`**             | Throws constraint violation if child exists.      | Deletes all child entities.                   | Deletes child entities if removed from collection. |
| **`@ManyToOne`**             | Throws constraint violation if referenced parent is deleted. | Deletes parent and sets child references to `NULL`. | Not applicable.                                   |
| **`@OneToOne`**              | Parent deletion sets FK to `NULL` by default.     | Deletes related entity.                       | Deletes related entity if association is removed. |

---

### **Summary**
- Use **`CascadeType.REMOVE`** when child entities should be deleted with the parent.
- Use **`orphanRemoval = true`** when child entities should be deleted when no longer associated with the parent.
- For entities that should persist after parent deletion (e.g., `Payslip` for record-keeping), do **not** configure cascade or orphan removal.

### **Cascade Types in JPA**

Cascade types in JPA define how operations performed on a parent entity are propagated to its associated child entities. Below is a detailed explanation and a table summarizing each cascade type.

---

### **Cascade Types Overview**

| **Cascade Type**      | **Description**                                                                 | **Use Case**                                                                                      |
|-----------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| **`PERSIST`**          | Propagates the `persist` operation from the parent to the child.                | Use when creating new entities along with their children, ensuring all entities are persisted.   |
| **`MERGE`**            | Propagates the `merge` operation from the parent to the child.                  | Use when updating detached parent and child entities.                                            |
| **`REMOVE`**           | Propagates the `remove` operation from the parent to the child.                 | Use when child entities should be deleted automatically when the parent is deleted.             |
| **`REFRESH`**          | Propagates the `refresh` operation to synchronize the child entities with the database. | Use when you want to reload parent and child entities from the database, discarding changes.     |
| **`DETACH`**           | Propagates the `detach` operation to detach child entities from the persistence context. | Use to prevent cascading updates by detaching the parent and its children from the context.     |
| **`ALL`**              | Applies all cascade operations: `PERSIST`, `MERGE`, `REMOVE`, `REFRESH`, `DETACH`. | Use when all operations should propagate to the child entities.                                 |

---

### **Cascade Types with Examples**

1. **`CascadeType.PERSIST`**  
   - Ensures that child entities are persisted when the parent is persisted.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.PERSIST)
   private List<Payslip> payslips;
   
   // Code
   Payslip payslip = new Payslip();
   employee.getPayslips().add(payslip);
   entityManager.persist(employee); // Persists both `employee` and `payslip`
   ```

2. **`CascadeType.MERGE`**  
   - Updates both parent and child entities when the parent is merged.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.MERGE)
   private List<Payslip> payslips;

   // Code
   employee.setName("Updated Name");
   employee.getPayslips().get(0).setMonth("December");
   entityManager.merge(employee); // Merges both `employee` and its payslips
   ```

3. **`CascadeType.REMOVE`**  
   - Deletes child entities when the parent is deleted.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.REMOVE)
   private List<Payslip> payslips;

   // Code
   Employee employee = entityManager.find(Employee.class, 1);
   entityManager.remove(employee); // Removes both `employee` and its associated payslips
   ```

4. **`CascadeType.REFRESH`**  
   - Updates child entities to reflect the current database state.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.REFRESH)
   private List<Payslip> payslips;

   // Code
   Employee employee = entityManager.find(Employee.class, 1);
   entityManager.refresh(employee); // Refreshes `employee` and its payslips from the database
   ```

5. **`CascadeType.DETACH`**  
   - Detaches child entities when the parent is detached, preventing further changes from being tracked.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.DETACH)
   private List<Payslip> payslips;

   // Code
   Employee employee = entityManager.find(Employee.class, 1);
   entityManager.detach(employee); // Detaches `employee` and its payslips from persistence context
   ```

6. **`CascadeType.ALL`**  
   - Applies all cascade operations.

   **Example**:
   ```java
   @OneToMany(cascade = CascadeType.ALL)
   private List<Payslip> payslips;

   // Code
   Payslip payslip = new Payslip();
   employee.getPayslips().add(payslip);
   entityManager.persist(employee); // Persists both `employee` and `payslip`

   employee.setName("Updated Name");
   entityManager.merge(employee); // Merges `employee` and its payslips

   entityManager.remove(employee); // Removes both `employee` and its payslips
   ```

---

### **Best Practices**
1. **Use `CascadeType.REMOVE`**:
   - When child entities should not exist independently of the parent.
   - Example: Deleting an `Order` should delete its `OrderItems`.

2. **Avoid `CascadeType.ALL` Without Necessity**:
   - Overusing `ALL` can lead to unintended deletions or updates, especially in production-critical data.

3. **Use `CascadeType.MERGE`**:
   - For scenarios where updates on detached entities need to propagate to children.

4. **Avoid Cascades on `@ManyToOne`**:
   - This can cause performance issues or logical conflicts, as many parents may reference a single child.

---

### **Quick Comparison Table**

| **Cascade Type**      | **Propagation Operations**                                                                                     | **Common Use Cases**                                      |
|-----------------------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| **PERSIST**            | Parent persisting saves all child entities.                                                                   | Creating new entities along with their children.         |
| **MERGE**              | Parent merging updates all child entities.                                                                    | Updating detached parent and children entities.          |
| **REMOVE**             | Parent removal deletes all child entities.                                                                    | Deleting an entity and its dependent child entities.      |
| **REFRESH**            | Parent refresh reloads child entities from the database.                                                      | Sync parent and child with the database state.           |
| **DETACH**             | Parent detach detaches child entities from the persistence context.                                            | Prevent unintended persistence updates for child entities.|
| **ALL**                | Applies all of the above operations.                                                                          | When full propagation is required (use cautiously).      |



1. Parent Entity

    The parent entity is the entity that "owns" the relationship in the logical object model.
    This entity usually holds the collection or references the other entity. In a one-to-many relationship, the "one" side is often considered the parent.

2. Owning Side of the Relationship

    The owning side of a relationship in JPA refers to the entity that maintains the foreign key.
    The owning side is responsible for the mapping of the relationship in the database (i.e., the side that has the foreign key column).


### **1️⃣ One-to-One Relationship** (`@OneToOne`)

**Example:** `Person` and `Passport`.

- **Owning Side:** The side that **holds the foreign key**.
  - In this case, **Person** has the foreign key (`passport_id`), so **Person** is the owning side.
- **Parent Side:** The side that **manages the relationship** (typically where the reference is stored).
  - Since **Person** has a reference to **Passport**, **Person** is also the parent.

**Conclusion:**  
- **Owning side** **is also the parent** in a `@OneToOne` relationship because it manages the foreign key and the relationship.

---

### **2️⃣ One-to-Many Relationship** (`@OneToMany`)

**Example:** `Department` and `Employee`.

- **Owning Side:** The side that **has the foreign key**.
  - Here, **Employee** has the foreign key (`department_id`), so **Employee** is the owning side.
- **Parent Side:** The side that **holds the collection** (in this case, the `List<Employee>`).
  - **Department** is the **parent** because it manages the collection of `Employee`s.

**Conclusion:**  
- In `@OneToMany`, **owning side is the "many" side (Employee)**, but the **parent side is the "one" side (Department)** because it holds the collection.

---

### **3️⃣ Many-to-One Relationship** (`@ManyToOne`)

**Example:** `Employee` and `Department`.

- **Owning Side:** The side that **has the foreign key**.
  - In this case, **Employee** holds the foreign key (`department_id`), so **Employee** is the owning side.
- **Parent Side:** The **one side** in the relationship, which is **Department**.
  - The **Department** is considered the **parent** because it's the "one" side.

**Conclusion:**  
- In `@ManyToOne`, **owning side is the "many" side (Employee)**, but the **parent side is the "one" side (Department)**.

---

### **4️⃣ Many-to-Many Relationship** (`@ManyToMany`)

**Example:** `Student` and `Course`.

- **Owning Side:** The side that **holds the join table** (foreign keys on both sides, or a separate join table).
  - In a typical `@ManyToMany` relationship, neither side directly holds the foreign key. Instead, a **join table** manages the relationship between the two entities.
  - If you define a **mappedBy** in one of the entities, that side is **not the owning side**.
  - Otherwise, **both sides can be considered owning sides**.
- **Parent Side:** The side that **manages the relationship** and **holds the collection**.
  - This could be either side depending on the design of the relationship (but generally, both sides have equal control).

**Conclusion:**  
- In `@ManyToMany`, **owning side** depends on the mapping and whether you're defining `mappedBy`. 
- **Parent side** could be either side, but both sides are closely tied in `@ManyToMany` relationships.

---

### **Summary Table**

| Relationship | Owning Side | Parent Side | Notes |
|--------------|-------------|-------------|-------|
| `@OneToOne`  | Owning side is also the parent (since it has the foreign key). | Parent and owning side are the same (both "Person" in our example). | Both manage the relationship. |
| `@OneToMany` | "Many" side is the owning side (foreign key is on the "many" side). | "One" side is the parent (holds the collection). | Parent is typically the "one" side. |
| `@ManyToOne` | "Many" side is the owning side (foreign key is on the "many" side). | "One" side is the parent. | Parent is typically the "one" side. |
| `@ManyToMany` | Owning side is determined by the join table or the side with the `mappedBy` attribute. | Parent can be either side, as both sides hold collections. | Owning side controls the join. |

---

### **Final Clarification:**

- **In a `@OneToOne`, the owning side is also the parent.**
- **In `@OneToMany` and `@ManyToOne`, the owning side is the "many" side, but the parent is the "one" side.**
- **In `@ManyToMany`, both sides can be considered owning sides, and both sides can be seen as parent sides.**

---

I hope this clears up the distinction between **owning side** and **parent side** in different relationships! Feel free to ask if you need more clarification! 😊

# Persistence Context in JPA

### What is a Persistence Context?

A **Persistence Context** is a set of managed entity instances in JPA. These entities are associated with the EntityManager, which is used to perform database operations like `persist`, `merge`, `find`, etc.

The **Persistence Context** is created when an `EntityManager` is instantiated, and it holds the state of the entities. This context is automatically synchronized with the underlying database when changes are committed through the transaction.

### Example: Persisting an Entity

Let's go through an example of persisting an `Employee` entity and understanding the concept of **Persistence Context** in JPA.

#### Code Example

```java
Employee employee1 = new Employee();
employee1.setName("Bob Marley");
employee1.setDob(new Date());
employee1.setEmployeeType(EmployeeType.FULLTIME);

System.out.println("******* Created a new Employee Instance");

EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myApp");
EntityManager entityManager = entityManagerFactory.createEntityManager();
EntityTransaction transaction = entityManager.getTransaction();

transaction.begin();
System.out.println("******* Staring the transaction");
entityManager.persist(employee1);
System.out.println("******* After persist method call");
transaction.commit();
System.out.println("******* Commiting the transaction");
```

#### Output:

```
******* Created a new Employee Instance
******* Staring the transaction
Hibernate: 
    call next value for hibernate_sequence
******* After persist method call
Hibernate: 
    insert 
    into
        EMPLOYEE_DATA
        (accessCard_id, dob, employeeType, name, id) 
    values
        (?, ?, ?, ?, ?)
******* Commiting the transaction
```

### Explanation

- **Step 1:** A new `Employee` instance is created.
- **Step 2:** The `EntityManager` is created using `EntityManagerFactory`.
- **Step 3:** A transaction is started.
- **Step 4:** The `employee1` is persisted using `entityManager.persist()`. However, no insert is executed yet. The `persist` method just adds the entity to the **Persistence Context** (which is an in-memory cache).
- **Step 5:** The `insert` statement is only executed when the transaction is committed (`transaction.commit()`).

This delay in the actual insert statement happens because JPA waits for the transaction to be committed. The persistence context holds the entity and knows when to optimize the database operations. Thus, the actual SQL insert query is executed at the time of commit.

### Finding Entities Before Commit

What happens if you try to fetch the same `employee` before committing the transaction? Let’s try it:

```java
transaction.begin();
System.out.println("******* Staring the transaction");
entityManager.persist(employee1);

// Let's try to find the employee before the commit
Employee employee = entityManager.find(Employee.class, 1);
System.out.println(employee);

System.out.println("******* After persist method call");
transaction.commit();
System.out.println("******* Commiting the transaction");
```

#### Output:

```
******* Staring the transaction
Hibernate: 
    call next value for hibernate_sequence
Employee{id=1, name='Bob Marley', dob=Mon Dec 09 12:02:04 IST 2024, employeeType=FULLTIME, accessCard=null}
******* After persist method call
Hibernate: 
    insert 
    into
        EMPLOYEE_DATA
        (accessCard_id, dob, employeeType, name, id) 
    values
        (?, ?, ?, ?, ?)
******* Commiting the transaction
```

### Explanation

- Even though the `insert` query has not been executed yet, the `find` method doesn't query the database for the entity.
- **Persistence Context**: The entity manager holds the entity instance in the persistence context, and when you try to access the `employee` using `entityManager.find()`, it provides the entity from the cache instead of querying the database.
- This is because JPA manages an in-memory cache of all managed entities within the **Persistence Context**.

### Verifying the Same Entity Instance

You can verify that the same instance is being returned from the persistence context by comparing the references:

```java
entityManager.persist(employee1);

Employee employee = entityManager.find(Employee.class, 1);
System.out.println(employee == employee1); // Prints true
```

#### Explanation:

- The above line prints `true` because the `employee1` that was persisted is the same instance that is returned when you call `entityManager.find()` before the transaction is committed.
- This shows that JPA does not need to fetch the entity from the database since it's already in the persistence context.

### Conclusion

- **Persistence Context**: It is the in-memory cache that JPA uses to track the entities and their state. When you call methods like `persist`, JPA does not immediately write to the database but instead holds the entity in the persistence context until the transaction is committed.
- **Optimized Database Operations**: By managing the entities in memory and delaying database operations until the transaction commit, JPA optimizes the use of database resources.
- **Entity Identity**: The entity manager ensures that there is only one instance of each entity per persistence context, providing efficient access and preventing multiple database queries.

---

# Persistence Context in JPA

### What is a Persistence Context?

A **Persistence Context** is like a cache that stores your entity instances managed by JPA. The JPA provider (e.g., Hibernate) uses this context to interact with the database efficiently.

![image](https://github.com/user-attachments/assets/0a4cc130-5fbe-4e7d-a2e6-b891248969dc)

The **Persistence Context** works with the database to store and fetch data, and the JPA provider determines the most optimal way to handle this interaction.

![image](https://github.com/user-attachments/assets/d67eb81a-d7bd-4e64-8481-0c7154c647e4)

---

### How Does It Work?

1. **Persisting an Entity:**

   When you call `entityManager.persist(employee)`, the entity is added to the persistence context. However, **an insert statement is not executed immediately**.

   ![image](https://github.com/user-attachments/assets/03756107-90e1-4085-b5fd-d52a0a0e2a57)

2. **Finding an Entity:**

   If you use `entityManager.find(Employee.class, id)` for the same entity, the persistence context provides the reference to the entity already stored in it. No database query is executed.

   ![image](https://github.com/user-attachments/assets/5c01d5aa-8755-41a9-a75e-bd29b92fbb49)

---

# Entity States in JPA

Entities in JPA go through multiple states during their lifecycle. Here's a breakdown of these states:

---

## 1. **Transient State**

An entity typically starts in a **transient state**. This means the entity has been created, but no JPA-related operations have been performed on it.

Example:

```java
Employee employee1 = new Employee();
employee1.setName("Bob Marley 2");
employee1.setDob(new Date());
employee1.setEmployeeType(EmployeeType.FULLTIME);
```

- The `employee1` object here is in the **transient state**.
- It is not associated with any persistence context, and no database record exists for it yet.

---

## 2. **Managed State**

When you **persist** an entity, it transitions to the **managed state**. This means:

- JPA starts managing the entity.
- The entity is added to the **persistence context**.
- Changes to the entity are tracked and synchronized with the database when the transaction is committed.

### Example Flow:

1. Persisting an Entity:

```java
entityManager.persist(employee1);
```

At this point, the entity moves to the managed state.

![image](https://github.com/user-attachments/assets/5d88dbf8-9b12-406e-9991-b76b2b149bcf)

2. The entity is now in the persistence context but might not yet be inserted into the database until the transaction is committed:


---

### Managed State via Fetching:

If an entity is fetched from the database using methods like `entityManager.find()` or `entityManager.createQuery()`, it also enters the **managed state**. 

Example:

```java
Employee employee = entityManager.find(Employee.class, 1);
```

![image](https://github.com/user-attachments/assets/7a29902b-1653-42e5-a0a1-1f7a17847f22)

- The fetched `employee` entity is in the managed state and is part of the persistence context.
- JPA will synchronize changes to this entity back to the database at the end of the transaction.
---

# Remove, Flush, and Detached States

---

## 1. **Removed State**

An entity transitions to the **removed state** when the `remove()` method is called on a managed entity. This marks the entity for deletion in the database.

### Example:
```java
Employee employee = entityManager.find(Employee.class, 1); // Managed state
EntityTransaction transaction = entityManager.getTransaction();
transaction.begin();
entityManager.remove(employee); // Transition to removed state
transaction.commit();
```

Key Points:
- The entity remains in the persistence context but is no longer managed.
- Changes to this entity won't be synchronized with the database.
- If `find()` is called before the commit, a new SQL query is executed since the entity is not fetched from the persistence context.

![Removed State Transition](https://github.com/user-attachments/assets/abe45fe0-82a1-42b9-a255-6c4b722620c3)

### Reverting the Removal:
If removal was accidental, you can bring the entity back to the managed state by calling `persist()` again.

![Reverting Remove](https://github.com/user-attachments/assets/f1c7a2f2-4414-4b9d-9e6e-f39175d45ee0)

---

## 2. **Flushing the Persistence Context**

Flushing ensures that all changes in the persistence context (both managed and removed entities) are synchronized with the database.

### Example:
```java
entityManager.flush();
```

Key Points:
- Managed entities are updated in the database.
- Removed entities are deleted from the database.
- Flushing does not end the transaction; it only synchronizes the persistence context with the database.

![Flush Operation](https://github.com/user-attachments/assets/a5d63a00-9781-4b94-978d-1b795f5ae355)

---

## 3. **Detached State**

An entity transitions to the **detached state** when it is no longer associated with the persistence context. This is not the same as deletion; the database record still exists.

### Example:
```java
entityManager.detach(employee);
```

Key Points:
- The entity is removed from the persistence context.
- The entity won't be synchronized with the database.
- Any modifications made to the detached entity won't be tracked by JPA.

![Detached State Transition](https://github.com/user-attachments/assets/5a7edad8-a108-4391-9ea3-c4b3f2360ac2)

---

## 4. **Reattaching Detached Entities**

You can bring a detached entity back to the managed state using `merge()`. 

### Example:
```java
entityManager.merge(employee); // employee is detached
```

### Why `merge()` and not `persist()`?
- `persist()` creates a new entry in the persistence context, but `merge()` is used when an entity might already exist in the database.
- If another instance of the same entity is already in the persistence context, `merge()` will combine the data from the detached entity into the managed instance.

![Merging Detached Entity](https://github.com/user-attachments/assets/850e90c6-2483-4e55-ac37-0d2ecb7f2157)

---
### `clear()` vs `detach()`:
- **`clear()`**: It detaches **all** entities in the persistence context (whether they are managed, removed, or new). This means that after calling `clear()`, the `EntityManager` will no longer track any entity. It is a global operation on the entire persistence context.

  ```java
  entityManager.clear();
  ```

- **`detach()`**: It detaches a specific entity from the persistence context. This means the entity is no longer managed, and any changes made to it will not be tracked by JPA.

  ```java
  entityManager.detach(employee);
  ```

So, while both methods transition entities from the **managed** state to the **detached** state, `clear()` is a broad operation that affects all entities, whereas `detach()` allows you to specify which entity you want to detach.

---

### `refresh()`:
The `refresh()` method is useful when you want to **resynchronize** an entity with the data from the database. If an entity has been modified in the persistence context and you want to discard those changes (i.e., revert to the version of the entity as it exists in the database), you can use `refresh()`.

#### Example of using `refresh()`:
```java
Employee employee = entityManager.find(Employee.class, 1); // Managed state
// Assume some changes were made to 'employee' entity

// If you want to discard the changes and reload the entity from the database:
entityManager.refresh(employee);
```

### Key Points:
- **`refresh()`**:
  - It discards any pending changes (dirty state) and reloads the entity from the database.
  - It is useful when you want to make sure the entity reflects the most recent state in the database, particularly after other operations might have modified the entity in parallel.
- **`clear()`** and **`detach()`**:
  - **`clear()`** detaches all entities in the persistence context.
  - **`detach()`** detaches a specific entity from the persistence context.

These operations are important tools for managing the lifecycle and synchronization of entities in JPA.


### 1. **Basic JPQL Query**: Fetching All Entities

In JPA, the `find()` method is great when you know the primary key of the entity, but what if you want to fetch multiple entities based on some conditions or to retrieve all records? That's where JPQL comes in.

#### Example to fetch all employees:

```java
Query query = entityManager.createQuery("select e from Employee e");
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- `select e from Employee e` is the JPQL query. The `Employee` is the entity name, not the table name. JPQL operates on entities (Java classes), not directly on the database tables.
- `e` is an alias for the `Employee` entity in the query.

You can use `createQuery()` for dynamic queries, which returns a `Query` object. To make the query type-safe, you can use `TypedQuery`.

### 2. **Using TypedQuery** (Type-Safe)

If you know the type of the result, you can use `TypedQuery` to avoid type-casting errors at runtime.

```java
TypedQuery<Employee> query = entityManager.createQuery("select e from Employee e", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- `Employee.class` ensures that the query results are mapped to `Employee` entities.
- `getResultList()` will return a list of `Employee` entities.

### 3. **Using WHERE Clause** to Add Conditions

You can add conditions to the query using the `WHERE` clause. Keep in mind that JPQL uses entity properties (not table columns) in the `WHERE` clause.

#### Example to fetch employees who are older than 20:

```java
TypedQuery<Employee> query = entityManager.createQuery("select e from Employee e where e.age > 20", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- `e.age` refers to the `age` attribute of the `Employee` entity, not the database column.

### 4. **Using ORDER BY Clause** to Sort Results

You can also sort the results using the `ORDER BY` clause in JPQL.

#### Example to fetch employees ordered by age in descending order:

```java
TypedQuery<Employee> query = entityManager.createQuery("select e from Employee e order by e.age desc", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- `e.age` is the property of the `Employee` entity.
- `desc` sorts the results in descending order. You can use `asc` for ascending order (it’s the default if you don’t specify).

---

### Key Points:

- **JPQL (Java Persistence Query Language)** works with **entities** (Java objects) and **not** directly with tables. So, the queries are written using the entity’s properties (fields) instead of the database columns.
- **`createQuery()`** returns a `Query` object for dynamic queries, and **`TypedQuery`** ensures type safety by specifying the result type.
- **WHERE clause** in JPQL allows filtering based on the entity’s attributes, and **ORDER BY** sorts the results based on entity attributes.

JPQL allows you to write queries in a way that is more object-oriented, making it easier to work with JPA entities.



### 1. **LIKE Operator** in JPQL

The `LIKE` operator is used for pattern matching in JPQL, similar to SQL. It allows you to match strings based on a pattern.

#### Example: Fetch employees whose names start with "B"

```java
TypedQuery<Employee> query = entityManager.createQuery(
    "select e from Employee e where e.name like 'B%'", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- **Pattern**: `'B%'` is the pattern we’re matching against. The `%` symbol is a wildcard, meaning that any string starting with "B" will be matched. For example, "Bob", "Billy", "Bane", etc.
- **`LIKE`**: This is case-sensitive by default, but it can vary depending on the database (e.g., some databases are case-insensitive).

If you want to match a substring or use other wildcard characters like `_` (to match a single character), you can modify the pattern accordingly:
- `'B%'` — Starts with "B".
- `'%B'` — Ends with "B".
- `'%Bob%'` — Contains "Bob" anywhere in the name.
- `'B__'` — Starts with "B" and followed by exactly two characters.

---

### 2. **BETWEEN Operator** in JPQL

The `BETWEEN` operator is used to check if a value falls within a specified range, including both endpoints.

#### Example: Fetch employees whose IDs are between 1 and 10

```java
TypedQuery<Employee> query = entityManager.createQuery(
    "select e from Employee e where e.id between 1 and 10", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

- **`BETWEEN 1 AND 10`**: This will select employees whose `id` falls between 1 and 10, inclusive. It’s like saying "ID is greater than or equal to 1 and less than or equal to 10."
- **Range**: The `BETWEEN` operator works for numeric values, date ranges, and even string ranges in JPQL.

### Notes:
- The **`LIKE`** operator in JPQL works with **string properties** in entities.
- The **`BETWEEN`** operator is used for **numeric and date** ranges and can be applied to any comparable property.

These operators are useful when querying for records with specific patterns or within specific ranges, making your queries more flexible.
In JPQL, you can easily perform joins using the relationships defined between entities without needing to explicitly define the SQL join syntax. If the relationship between entities is mapped correctly (e.g., using `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`), JPQL will automatically handle the joins for you.

### Example: Fetching Employees whose Access Card is Active

Given that there’s a relationship between `Employee` and `AccessCard`, and assuming the `Employee` entity has a field called `card` that represents the relationship to `AccessCard`, you can query employees whose access card is active using JPQL:

```java
TypedQuery<Employee> query = entityManager.createQuery(
    "select e from Employee e where e.card.isActive = true", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

In this case:
- **`e.card`** refers to the `AccessCard` entity associated with the `Employee` (thanks to the relationship mapping in the `Employee` entity).
- **`e.card.isActive`** is accessing the `isActive` property of the `AccessCard` entity, which is assumed to be a boolean field indicating if the card is active.

---

### Equivalent SQL Query:

If you were to write this query in SQL, it would look something like this:

```sql
SELECT e.*
FROM Employee e
JOIN AccessCard ac ON e.accessCard_id = ac.id
WHERE ac.is_active = true;
```

Here:
- **`Employee e`**: Represents the `Employee` table.
- **`AccessCard ac`**: Represents the `AccessCard` table.
- **`JOIN`**: Explicitly joins the two tables based on the relationship between the `Employee` and `AccessCard` tables.
- **`WHERE ac.is_active = true`**: Filters employees whose associated access card is active.


However if you want to use join syntax, you can do that as well.

![image](https://github.com/user-attachments/assets/62461a53-9f84-4bc6-80d7-c80ba1bc1756)

In cases where the result of a query is not necessarily an entity but rather a subset of data or even a combination of different data types, JPQL allows you to fetch only the specific data you need. This can help optimize performance by reducing the amount of unnecessary data retrieval.

### Example 1: Fetching Specific Columns (Only Employee Names)

If you only need a subset of the entity data, such as just the names of employees, you can specify the exact field you want to retrieve. This avoids fetching all the data related to the employee entity.

#### Example Code:
```java
TypedQuery<String> query = entityManager.createQuery(
    "select e.name from Employee e", String.class);
List<String> resultList = query.getResultList();

resultList.forEach(System.out::println);
```

In this query:
- We're selecting only the `name` field from the `Employee` entity.
- The return type is `String.class` since we're fetching only the names.
- This is more efficient than retrieving the entire `Employee` entity if you're only interested in the `name` field.

### Example 2: Fetching Multiple Fields (Name and Date of Birth)

If you need more than one field from the entity, you can select multiple fields, and JPQL will return the results as an `Object[]`, where each element corresponds to a selected field.

#### Example Code:
```java
TypedQuery<Object[]> query = entityManager.createQuery(
    "select e.name, e.dob from Employee e", Object[].class);
List<Object[]> resultList = query.getResultList();

resultList.forEach(x -> {
    System.out.println(x[0]); // Employee name
    System.out.println(x[1]); // Employee date of birth
});
```

Here:
- We are selecting `name` and `dob` fields from the `Employee` entity.
- The result is returned as an array of objects (`Object[]`), where `x[0]` is the `name` and `x[1]` is the `dob`.

### Example 3: Using Joins with Specific Fields (Employee Name, DOB, and Access Card Issued Date)

When working with relationships, such as fetching an employee's information along with details from a related entity (like `AccessCard`), you can use JPQL joins. You specify the fields from both the `Employee` and `AccessCard` entities in the query.

#### Example Code:
```java
TypedQuery<Object[]> query = entityManager.createQuery(
    "select e.name, e.dob, e.card.issuedDate from Employee e", 
    Object[].class);
List<Object[]> resultList = query.getResultList();

resultList.forEach(x -> {
    System.out.println(x[0]); // Employee name
    System.out.println(x[1]); // Employee date of birth
    System.out.println(x[2]); // Access card issued date
});
```

In this case:
- The `Employee` entity is joined with the `AccessCard` entity using the `card` relationship.
- The query fetches the `name`, `dob`, and `issuedDate` fields, where `e.card.issuedDate` refers to the `issuedDate` field of the related `AccessCard` entity.

### Summary:
1. **Fetching Specific Fields**: You can select only the necessary fields from your entities, reducing the data fetched from the database.
2. **Using Object Arrays**: When fetching multiple fields, JPQL can return the results as an array of objects (`Object[]`), and you can access each field by its index.
3. **Working with Joins**: JPQL allows you to join related entities and fetch specific fields from both entities, simplifying the query process and improving readability.

By optimizing your queries in this way, you can avoid fetching unnecessary data and improve performance when working with JPA.
# Using Parameters in JPQL Queries

When working with JPA, it's crucial to avoid string concatenation to insert dynamic values into queries. String concatenation can lead to potential security risks, such as SQL injection, where malicious input could manipulate your query and harm your database.

## Example: Fetch Employees Older Than 20

### **Incorrect Approach (String Concatenation)**
A common but insecure approach might look like this:

```java
int age = 20;
TypedQuery<Employee> query = entityManager.createQuery(
        "select e from Employee e where e.age >" + age, Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

**Problem:** This approach exposes the query to SQL injection vulnerabilities. An attacker could manipulate the `age` value to run malicious SQL queries.

Say if we were using `String age = "25"` an attacker can manipulate the value of this string and pass something like : `String age="25;DELETE FROM EMPLOYEE_DATA"`

### **Secure Approach (Using Parameters)**
To prevent SQL injection, use named parameters in JPQL. Here's how you can safely insert dynamic values into your queries:

```java
int age = 25;
TypedQuery<Employee> query = entityManager.createQuery(
        "select e from Employee e where e.age > :minAge", Employee.class);

query.setParameter("minAge", age);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

### **Explanation:**

- **Named Parameters**: The query uses `:minAge` as a placeholder for the parameter. 
- **Setting Parameters**: The `setParameter` method is used to safely bind the `age` variable to the `minAge` parameter in the query.
- **Security**: This approach avoids SQL injection by ensuring the dynamic value is properly escaped and handled by JPA.
# Using Named Queries in JPA

Named Queries are a powerful feature in JPA that allow you to define frequently used queries directly within your entity class. They help organize your queries and make your code cleaner and more reusable.

We can have multiple annotations of @NamedQuery on top of a single entity.

## Steps to Define and Use Named Queries

### 1. Define the Named Query in the Entity Class
To define a named query, you use the `@NamedQuery` annotation inside your entity class. This query can be reused throughout your application.

#### Example: Named Query for Sorting Employees by Name

```java
@Entity
@Table(name = "EMPLOYEE_DATA")
@NamedQuery(query = "SELECT e FROM Employee e ORDER BY e.name", name = "emp_name_asc")
public class Employee {
    // Entity fields and methods
}
```

- `query`: The JPQL query that will be executed.
- `name`: A unique name for the query that can be used to refer to the query later.

### 2. Using Named Query in Code

Once the named query is defined, you can use it anywhere in your code to execute the query.

#### Example: Using the Named Query to Get Employees Sorted by Name

```java
TypedQuery<Employee> query = entityManager.createNamedQuery("emp_name_asc", Employee.class);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

### 3. Using Parameters in Named Queries

You can also define parameters in your named queries and set them when executing the query.

#### Example: Named Query with Parameters

```java
@Entity
@Table(name = "EMPLOYEE_DATA")
@NamedQuery(query = "SELECT e FROM Employee e WHERE e.age > :minAge ORDER BY e.name", name = "emp_name_by_age")
public class Employee {
    // Entity fields and methods
}
```

- `:minAge` is a placeholder for the parameter to be passed into the query.

#### Example: Setting Parameters for the Named Query

```java
int age = 20;
TypedQuery<Employee> query = entityManager.createNamedQuery("emp_name_by_age", Employee.class);
query.setParameter("minAge", age);
List<Employee> resultList = query.getResultList();
resultList.forEach(System.out::println);
```

### Benefits of Named Queries

- **Reusability**: Named queries are defined once and can be used across the application.
- **Separation of Concerns**: Queries are kept separate from business logic, making the code cleaner.
- **Performance**: Named queries are pre-compiled by the JPA provider, which can improve performance in some cases.
- **Maintainability**: Changes to a query only need to be made in one place, making the code easier to maintain.
### **Persisting Entities in a Spring Boot Project Using JPA**

---

#### **1. Create a Spring Boot Project**
- Go to [Spring Initializr](https://start.spring.io/).
- Add the following dependencies:
  - **Spring Data JPA**: Provides integration with JPA.
  - **H2 Database**: In-memory database for quick testing.

---

#### **2. Configure Database Properties**
Add the following configuration in the `application.properties` file to define the database connection and just like we added the properties in the persistance.xml, we give properties of the xml here:

```properties
spring.application.name=demo

spring.datasource.url=jdbc:h2:tcp://localhost/~/test
spring.datasource.username=sa
spring.datasource.password=

spring.datasource.driver-class-name=org.h2.Driver
spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.H2Dialect
```

- `spring.datasource.url`: URL for the H2 database.
- `spring.jpa.hibernate.ddl-auto=update`: Allows automatic table creation or updates based on entity definitions.
- `spring.jpa.show-sql=true`: Displays generated SQL in the logs.
- `spring.jpa.properties.hibernate.dialect`: Specifies the database dialect.

---

#### **3. Use the entities from the previous example, like `Employee`**

---

#### **4. Persisting an Entity**

In JPA, we typically use the `Persistence` class to create an `EntityManagerFactory` and then obtain an `EntityManager`. In Spring Boot, dependency injection simplifies this process.

##### **Injecting `EntityManagerFactory`**
Use the `@PersistenceUnit` annotation to inject the `EntityManagerFactory`:

```java
import jakarta.persistence.EntityManager;
import jakarta.persistence.EntityManagerFactory;
import jakarta.persistence.EntityTransaction;
import jakarta.persistence.PersistenceUnit;
import org.springframework.stereotype.Component;

@Component
public class EmployeeService {

    @PersistenceUnit
    private EntityManagerFactory emf;

    public void saveEmployee() {
        Employee e = new Employee();
        e.setName("Bob");
        e.setEmployeeType(EmployeeType.FULLTIME);
        e.setAge(25);

        EntityManager entityManager = emf.createEntityManager();
        EntityTransaction transaction = entityManager.getTransaction();
        try {
            transaction.begin();
            entityManager.persist(e);
            transaction.commit();
        } catch (Exception ex) {
            transaction.rollback();
            throw ex;
        } finally {
            entityManager.close();
        }
    }
}
```

##### **Explanation:**
1. **`@PersistenceUnit`**:
   - Injects the `EntityManagerFactory`.
   - Configures the persistence unit using properties from `application.properties`.

2. **EntityManager**:
   - Obtained from `EntityManagerFactory` to manage entity lifecycle.
   - Used to persist (`persist()`) the `Employee` entity.

3. **Transaction Management**:
   - Begin a transaction (`transaction.begin()`).
   - Persist data and commit the transaction (`transaction.commit()`).
   - Rollback if an exception occurs.

---
### **Directly Using `EntityManager` in Spring Boot**

---

#### **1. Using `@PersistenceContext` to Inject `EntityManager`**

Instead of obtaining an `EntityManager` from the `EntityManagerFactory`, Spring provides a way to directly inject it using the `@PersistenceContext` annotation:

```java
import jakarta.persistence.EntityManager;
import jakarta.persistence.PersistenceContext;
import org.springframework.stereotype.Service;

@Service
public class EmployeeService {

    @PersistenceContext
    private EntityManager entityManager;

    public void start() {
        Employee employee1 = entityManager.find(Employee.class, 1);
        System.out.println(employee1);
    }
}
```

---

#### **2. Shared Nature of `EntityManager`**

When using `@PersistenceContext`, the injected `EntityManager` is:
1. **A Shared Proxy**: It is a single shared instance that proxies the real `EntityManager`.
2. **Thread-Safe**: Spring ensures that each transaction gets its own actual `EntityManager` instance behind the scenes, while the proxy provides thread safety and transactional management.

---

#### **3. Limitations of Shared `EntityManager`**
- **Read-Only Operations**: The shared `EntityManager` works well for read operations.
- **No Manual Transaction Management**:
  - You cannot call `entityManager.getTransaction()` to start or manage transactions manually.
  - Transactions are managed by Spring through annotations like `@Transactional`.

---

#### **4. Handling Transactions Safely**

For write operations, ensure that your methods are marked as transactional. Spring will handle the creation of a dedicated `EntityManager` for the transaction:

```java
import jakarta.persistence.EntityManager;
import jakarta.persistence.PersistenceContext;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class EmployeeService {

    @PersistenceContext
    private EntityManager entityManager;

    @Transactional
    public void saveEmployee() {
        Employee employee = new Employee();
        employee.setName("Alice");
        employee.setAge(30);
        employee.setEmployeeType(EmployeeType.FULLTIME);

        entityManager.persist(employee);
    }
}
```

---

#### **5. Key Notes**
1. **Transactional Scope**: The `@Transactional` annotation ensures that a dedicated `EntityManager` is created for the transaction.
2. **Error on Manual Transaction**:
   - Trying to use `entityManager.getTransaction()` on the shared `EntityManager` will result in an exception, as Spring-managed transactions do not allow manual control.

---

### **Summary**
- **For Reads**: Use the shared `EntityManager` directly injected via `@PersistenceContext`.
- **For Writes**: Always use methods annotated with `@Transactional` to ensure proper transaction management and avoid thread-safety issues.
### **Spring Data JPA with `CrudRepository`**
Spring Data JPA simplifies database operations by providing predefined interfaces like `CrudRepository` and `JpaRepository`. These interfaces abstract away the repetitive code for common CRUD operations.

---

### **Step-by-Step Guide**

1. **Define a Repository**:
   - Instead of writing a DAO layer manually, create a repository interface extending `CrudRepository`.
   - Specify the **entity class** and its **primary key type** as generic parameters.

   Example:
   ```java
   @Repository
   public interface EmployeeRepository extends CrudRepository<Employee, Integer> {
   }
   ```

2. **Inject the Repository**:
   - Use Spring's `@Autowired` annotation to inject the repository into your service or controller.

   Example:
   ```java
   @Autowired
   private EmployeeRepository employeeRepository;
   ```

3. **Perform CRUD Operations**:
   - The `CrudRepository` interface provides built-in methods for basic operations:
     - `save(S entity)` - Saves or updates an entity.
     - `findById(ID id)` - Fetches an entity by its ID.
     - `findAll()` - Retrieves all entities.
     - `deleteById(ID id)` - Deletes an entity by its ID.
     - `delete(S entity)` - Deletes a specific entity.
     - `count()` - Returns the total number of entities.

   Example: **Find by ID**
   ```java
   Optional<Employee> employee = employeeRepository.findById(1);
   employee.ifPresent(System.out::println);
   ```

---

### **Benefits of Using Spring Data JPA**
1. **Less Boilerplate Code**:
   - No need to write repetitive DAO methods for basic CRUD operations.

2. **Custom Query Support**:
   - You can define custom methods for specific queries using Spring Data JPA's query derivation.

   Example:
   ```java
   List<Employee> findByName(String name);
   ```

3. **Integration with Spring Ecosystem**:
   - Works seamlessly with Spring Boot and Spring Data layers, enabling rapid application development.

4. **Optional Use of JPQL**:
   - When required, you can define JPQL queries using `@Query`.

   Example:
   ```java
   @Query("SELECT e FROM Employee e WHERE e.age > :age")
   List<Employee> findEmployeesOlderThan(@Param("age") int age);
   ```

### **Update Operation Using `CrudRepository` in Spring Boot**

In Spring Data JPA, the `save()` method is used for both **insert** and **update** operations. If the entity already exists (identified by its ID), the method performs an **update**. Otherwise, it performs an **insert**.

---

### **How Transactions Work in Spring Boot**

- **Declarative Transaction Management**: Spring Boot provides the `@Transactional` annotation to manage transactions declaratively. 
- When a method annotated with `@Transactional` is called:
  1. A new transaction is started.
  2. If the method completes successfully, the transaction is **committed**.
  3. If any exception occurs, the transaction is **rolled back** automatically.

---

### **Example: Updating an Entity**

Here's how you can update an employee using the `CrudRepository` and `@Transactional` annotation:

#### **Step 1: Define the Update Method**

```java
import org.springframework.transaction.annotation.Transactional;

@Service
public class EmployeeService {

    @Autowired
    private EmployeeRepository employeeRepository;

    @Transactional
    public void updateEmployee(Employee employee) {
        // Update the employee details
        employee.setName("Bob Lazar");
        employeeRepository.save(employee);
    }
}
```

- **`@Transactional`**:
  - Ensures that the update operation happens within a transaction.
  - Handles commit and rollback automatically.

#### **Step 2: Call the Update Method**

```java
@Autowired
private EmployeeService employeeService;

public void updateEmployeeExample() {
    Optional<Employee> optionalEmployee = employeeRepository.findById(1);
    if (optionalEmployee.isPresent()) {
        Employee employee = optionalEmployee.get();
        employeeService.updateEmployee(employee);
    }
}
```

---

### **How `save()` Determines Insert vs. Update**

1. **Insert**:
   - If the primary key (ID) of the entity is `null`, the `save()` method performs an **insert** operation.

2. **Update**:
   - If the primary key (ID) exists and matches an entity in the database, the `save()` method performs an **update** operation.

---

### **Rollback on Error**

If an exception is thrown during the execution of the `updateEmployee()` method:
- Spring automatically rolls back the transaction, ensuring no partial changes are saved to the database.

Example:
```java
@Transactional
public void updateEmployeeWithError(Employee employee) {
    employee.setName("John Doe");
    employeeRepository.save(employee);
    
    // Simulate an error
    if (true) {
        throw new RuntimeException("Simulated error");
    }
}
```
- In this case, the update operation is rolled back, and no changes are saved.


We can also specify if we want to rollback only at specific Exception.

```java
@Transactional(rollbackOn= SQLException.class)
public void updateEmployeeWithError(Employee employee) {
    employee.setName("John Doe");
    employeeRepository.save(employee);
}
```


We can also specify if we don't want to rollback only at specific Exception.

```java
@Transactional(dontrollbackOn= MyApplicationException.class)
public void updateEmployeeWithError(Employee employee) {
    employee.setName("John Doe");
    employeeRepository.save(employee);
}
```
### **Managing Transactions Across Multiple Repositories in Spring Boot**

---

### **Scenario**
You need to update two entities (e.g., `Employee` and `AccessCard`) using two different repositories. You want to ensure that:
1. Both updates are treated as **one transaction**: If one fails, the entire operation rolls back.
2. You can control how transactions are propagated when methods are called within the same or across different classes.

---

### **Single Transaction**

By default, Spring Boot provides **transaction propagation** behavior to manage this.

#### Example: Combining Two Repository Calls into a Single Transaction
```java
@Service
public class EmployeeService {

    @Autowired
    private EmployeeRepository employeeRepository;

    @Autowired
    private AccessCardRepository accessCardRepository;

    @Transactional
    public void updateEmployeeAndAccessCard(Employee employee, AccessCard accessCard) {
        // Save employee
        employeeRepository.save(employee);

        // Save access card
        accessCardRepository.save(accessCard);
    }
}
```

- **Result**: If either `save()` call fails, the entire transaction is rolled back.

---

### **Handling Nested Transactions**

#### Default Behavior
When you call a method with `@Transactional` from another `@Transactional` method:
- Spring uses the **same transaction** (default `Propagation.REQUIRED` behavior).
- Example:
  ```java
  @Transactional
  public void updateEmployeeAndAccessCard(Employee employee, AccessCard accessCard) {
      updateEmployee(employee);
      accessCardRepository.save(accessCard);
  }

  @Transactional
  public void updateEmployee(Employee employee) {
      employee.setName("Updated Name");
      employeeRepository.save(employee);
  }
  ```

  **What Happens**:
  - `updateEmployeeAndAccessCard()` starts a transaction.
  - `updateEmployee()` runs within the **same transaction**.
  - Both operations succeed or fail together.

#### Forcing a New Transaction
If you want `updateEmployee()` to always run in a **new transaction**, use `Propagation.REQUIRES_NEW`:
```java
@Transactional
public void updateEmployeeAndAccessCard(Employee employee, AccessCard accessCard) {
    updateEmployee(employee); // Starts a new transaction
    accessCardRepository.save(accessCard);
}

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void updateEmployee(Employee employee) {
    employee.setName("Updated Name");
    employeeRepository.save(employee);
}
```

**Effect**:
- `updateEmployee()` starts a new transaction **independent** of `updateEmployeeAndAccessCard()`.
- If `updateEmployeeAndAccessCard()` fails after calling `updateEmployee()`, changes made by `updateEmployee()` **are not rolled back** because it has its own transaction.

---

### **Other Transaction Propagation Modes**

1. **`Propagation.NOT_SUPPORTED`**:
   - The method does **not participate** in any transaction.
   - If called within an existing transaction, the transaction is **suspended**.
   - Example:
     ```java
     @Transactional(propagation = Propagation.NOT_SUPPORTED)
     public void someNonTransactionalMethod() {
         // No transaction here
     }
     ```

2. **`Propagation.MANDATORY`**:
   - Requires an **existing transaction**.
   - Throws an exception if no transaction is active.
   - Example:
     ```java
     @Transactional(propagation = Propagation.MANDATORY)
     public void mustRunWithinTransaction() {
         // Will throw an exception if no transaction exists
     }
     ```

3. **`Propagation.SUPPORTS`**:
   - Runs within a transaction **if one exists**, otherwise runs without one.
   - Example:
     ```java
     @Transactional(propagation = Propagation.SUPPORTS)
     public void runIfTransactionExists() {
         // Will use transaction if available
     }
     ```

---

### **Choosing the Right Propagation Mode**
- Use **default behavior (`Propagation.REQUIRED`)** for most scenarios.
- Use **`Propagation.REQUIRES_NEW`** when specific operations must run independently.
- Use **`Propagation.NOT_SUPPORTED`** for read-only or logging operations that don't need a transaction.
- Use **`Propagation.MANDATORY`** to enforce that certain methods are always called within a transaction.

---

### **Common Pitfalls**
1. **Calling `@Transactional` Methods Within the Same Class**:
   - Spring's transaction management works via proxies. Calling a `@Transactional` method directly within the same class bypasses the proxy and won't respect transaction boundaries.
   - **Solution**: Use a different service or call the method via the bean.

2. **Unchecked Exceptions for Rollback**:
   - By default, Spring rolls back transactions only for **unchecked exceptions** (`RuntimeException`).
   - Use `@Transactional(rollbackFor = Exception.class)` if you want to include checked exceptions.

---

### **Using Transactions for Read-Only Operations in Spring**

---

### **Scenario: Avoiding Race Conditions in Read Operations**

When reading multiple entities in sequence (e.g., retrieving data for multiple tables), there can be a potential **race condition**:
- The state of the database might change between successive reads.
- This could result in inconsistent data being fetched.

#### **Solution: Use a Transaction for Read-Only Operations**
To ensure consistency during read operations, you can use Spring's `@Transactional` annotation with `readOnly = true`. This ensures that all read operations are part of a single transaction.

---

### **Example: Read-Only Transaction**

```java
@Service
public class ReportService {

    @Autowired
    private EmployeeRepository employeeRepository;

    @Autowired
    private AccessCardRepository accessCardRepository;

    @Transactional(readOnly = true)
    public Report generateEmployeeReport(int employeeId) {
        // Fetch Employee
        Employee employee = employeeRepository.findById(employeeId)
                .orElseThrow(() -> new RuntimeException("Employee not found"));

        // Fetch Access Card
        AccessCard accessCard = accessCardRepository.findById(employee.getCardId())
                .orElseThrow(() -> new RuntimeException("Access Card not found"));

        // Combine data into a Report object
        Report report = new Report();
        report.setEmployeeName(employee.getName());
        report.setAccessCardNumber(accessCard.getCardNumber());

        return report;
    }
}
```

---

### **Key Benefits of `@Transactional(readOnly = true)`**

1. **Consistency**:
   - Ensures all reads occur within the same transaction context.
   - Prevents changes to the database state during the transaction.

2. **Performance Optimization**:
   - The underlying transaction mechanism recognizes it as a **read-only transaction**.
   - Some optimizations can occur:
     - Disabling dirty checks (since no updates are happening).
     - Reducing the overhead of locking mechanisms in the database.

3. **Non-Blocking Nature**:
   - `readOnly = true` transactions are **not blocking** and allow other operations (including writes) to proceed concurrently.

---

### **When to Use Read-Only Transactions**

- **Complex Reads**:
  - When fetching multiple entities across repositories and consistency is critical.

- **Reports**:
  - Generating reports or dashboards where the data must remain consistent during generation.

- **Batch Read Operations**:
  - Large-scale data retrieval tasks where database state consistency matters.

---

### **Things to Keep in Mind**

1. **Not a Locking Mechanism**:
   - `@Transactional(readOnly = true)` does **not lock** data.
   - If the database is updated by another process during the transaction, the changes will be visible within the same transaction unless the database itself handles isolation.

2. **Database Behavior Depends on Isolation Level**:
   - The consistency of read data still depends on the **isolation level** of the transaction.
   - For stricter consistency, use higher isolation levels like **REPEATABLE READ** or **SERIALIZABLE**, but this may come with performance trade-offs.

3. **Must Be Used with Transactions**:
   - The `readOnly = true` flag is effective only when the method is part of a transactional context.
