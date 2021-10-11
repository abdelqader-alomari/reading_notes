# Read: 12 - Spring RESTful Routing & Static Files

## Spring RequestMapping

@RequestMapping is used for mapping web requests onto handler methods in request-handling classes. The process of mapping web requests to handler methods is also called routing.

@RequestMapping has the following specializations:

- @GetMapping
- @PostMapping
- @PutMapping
- @DeleteMapping
- @PatchMapping
- The annotation can be used both at the class and at the method level. If used on both levels, the request paths are combined.

- @RequestMapping — by Path: use GET method

```
@RequestMapping(value = "/ex/foos", method = RequestMethod.GET)
@ResponseBody
public String getFoosBySimplePath() {
    return "Get some Foos";
}
```

To test it:

`curl -i http://localhost:8080/spring-rest/ex/foos`

- @RequestMapping — the HTTP Method: use POST method
  The HTTP method parameter has no default. So, if we don't specify a value, it's going to map to any HTTP request.

```
@RequestMapping(value = "/ex/foos", method = POST)
@ResponseBody
public String postFoos() {
    return "Post some Foos";
}
```

to test it:
`curl -i -X POST http://localhost:8080/spring-rest/ex/foos`

![](https://springframework.guru/wp-content/uploads/2017/09/mvc.png)

## Accessing Data with JPA

This guide walks you through the process of building an application that uses Spring Data JPA to store and retrieve data in a relational database.

### Define a Simple Entity

In this example, you store Customer objects, each annotated as a JPA entity. The following listing shows the Customer class (in src/main/java/com/example/accessingdatajpa/Customer.java):

```
package com.example.accessingdatajpa;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class Customer {

  @Id
  @GeneratedValue(strategy=GenerationType.AUTO)
  private Long id;
  private String firstName;
  private String lastName;

  protected Customer() {}

  public Customer(String firstName, String lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
```

### Create Simple Queries

Spring Data JPA focuses on using JPA to store data in a relational database. Its most compelling feature is the ability to create repository implementations automatically, at runtime, from a repository interface.

To see how this works, create a repository interface that works with Customer entities as the following listing (in src/main/java/com/example/accessingdatajpa/CustomerRepository.java) shows:

```
package com.example.accessingdatajpa;

import java.util.List;

import org.springframework.data.repository.CrudRepository;

public interface CustomerRepository extends CrudRepository<Customer, Long> {

  List<Customer> findByLastName(String lastName);

  Customer findById(long id);
}
```

### Create an Application Class

Spring Initializr creates a simple class for the application. The following listing shows the class that Initializr created for this example (in src/main/java/com/example/accessingdatajpa/AccessingDataJpaApplication.java):

```
package com.example.accessingdatajpa;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class AccessingDataJpaApplication {

  public static void main(String[] args) {
    SpringApplication.run(AccessingDataJpaApplication.class, args);
  }

}
```

### Build an executable JAR

```
You can run the application from the command line with Gradle or Maven. You can also build a single executable JAR file that contains all the necessary dependencies, classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, across different environments, and so forth.

If you use Gradle, you can run the application by using ./gradlew bootRun. Alternatively, you can build the JAR file by using ./gradlew build and then run the JAR file, as follows:

java -jar build/libs/gs-accessing-data-jpa-0.1.0.jar
If you use Maven, you can run the application by using ./mvnw spring-boot:run. Alternatively, you can build the JAR file with ./mvnw clean package and then run the JAR file, as follows:

java -jar target/gs-accessing-data-jpa-0.1.0.jar
```

@Override
public String toString() {
return String.format(
"Customer[id=%d, firstName='%s', lastName='%s']",
id, firstName, lastName);
}

public Long getId() {
return id;
}

public String getFirstName() {
return firstName;
}

public String getLastName() {
return lastName;
}

```

## Baeldung: Comparing repositories

###  CrudRepository interface:

```

public interface CrudRepository<T, ID extends Serializable>
extends Repository<T, ID> {

    <S extends T> S save(S entity);

    T findOne(ID primaryKey);

    Iterable<T> findAll();

    Long count();

    void delete(T entity);

    boolean exists(ID primaryKey);

}

```
Notice the typical CRUD functionality:

- save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
- findOne(…) – get a single entity based on passed primary key value
- findAll() – get an Iterable of all available entities in database
- count() – return the count of total entities in a table
- delete(…) – delete an entity based on the passed object
- exists(…) – verify if an entity exists based on the passed primary key value
- This interface looks quite generic and simple, but actually, it provides all basic query abstractions needed in an application.
```

### PagingAndSortingRepository

```
public interface PagingAndSortingRepository<T, ID extends Serializable>
  extends CrudRepository<T, ID> {

    Iterable<T> findAll(Sort sort);

    Page<T> findAll(Pageable pageable);
}
```

This interface provides a method findAll(Pageable pageable), which is the key to implementing Pagination.

When using Pageable, we create a Pageable object with certain properties and we've to specify at least:

- Page size
- Current page number
- Sorting
  So, let's assume that we want to show the first page of a result set sorted by lastName, ascending, having no more than five records each. This is how we can achieve this using a PageRequest and a Sort definition:

Sort sort = new Sort(new Sort.Order(Direction.ASC, "lastName"));
Pageable pageable = new PageRequest(0, 5, sort);
Passing the pageable object to the Spring data query will return the results in question (the first parameter of PageRequest is zero-based).

### JpaRepository

Finally, we'll have a look at the JpaRepository interface:

```
public interface JpaRepository<T, ID extends Serializable> extends
  PagingAndSortingRepository<T, ID> {

    List<T> findAll();

    List<T> findAll(Sort sort);

    List<T> save(Iterable<? extends T> entities);

    void flush();

    T saveAndFlush(T entity);

    void deleteInBatch(Iterable<T> entities);
}
```

the methods:

- findAll() – get a List of all available entities in database
- findAll(…) – get a List of all available entities and sort them using the provided condition
- save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
- flush() – flush all pending task to the database
- saveAndFlush(…) – save the entity and flush changes immediately
- deleteInBatch(…) – delete an Iterable of entities. Here, we can pass multiple objects to delete them in a batch
- Clearly, above interface extends PagingAndSortingRepository which means it has all methods present in the CrudRepository as well.

![](https://1.bp.blogspot.com/-Hp5KPW5F_zc/XvP_DDboR-I/AAAAAAAAOj8/j28IVURGB4wJ1-ymh1ThNvZOaLCjZRahwCK4BGAsYHg/w500-h406/CrudRepositoryVsJpaRepo.png)

---

Resources:

1. http://www.baeldung.com/spring-requestmapping
2. https://springframework.guru/spring-requestmapping-annotation/
3. https://spring.io/guides/gs/accessing-data-jpa/
4. https://www.baeldung.com/spring-data-repositories
