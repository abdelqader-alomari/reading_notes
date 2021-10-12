# Read: 13 - Related Resources and Integration Testing

## Related data in Spring - relationship annotations

### One-to-One Relationship

Defines a single-valued association to another entity that has one-to-one multiplicity. It is not normally necessary to specify the associated target entity explicitly since it can usually be inferred from the type of the object being referenced. If the relationship is bidirectional, the non-owning side must use the mappedBy element of the OneToOne annotation to specify the relationship field or property of the owning side.

```
@OneToOne
    @JoinColumn(name = "address_id")
    @RestResource(path = "libraryAddress", rel="address")
    private Address address;
```

### Creating the Associations

This is done using the HTTP method PUT, which supports a media type of text/uri-list, and a body containing the URI of the resource to bind to the association.
Example :

```
curl -i -X PUT -d "http://localhost:8080/addresses/1"
 -H "Content-Type:text/uri-list" http://localhost:8080/libraries/1/libraryAddress
One-to-Many Relationship
Example :
public class Library {

    @OneToMany(mappedBy = "library")
    private List<Book> books;

}
```

### One-toMany Relationship

A @OneToMany relationship refers to the relationship between two entities/tables A and B in which one element/row of A may only be linked to many elements/rows of B, but a member of B is linked to only one element/row of A.
Usually, the child entity is one that owns the relationship and the parent entity contains the @OneToMany annotation.

### Many-to-Many Relationship

A many-to-many relationship is defined using @ManyToMany annotation, to which we can add @RestResource.
The @ManyToOne annotation is used to define a many-to-one relationship between two entities in Spring Data JPA. The child entity, that has the join column, is called the owner of the relationship defined using the @ManyToOne annotation.

example: 1 restaurant can have many reviews.

```
public class Book {
    @ManyToMany(mappedBy = "books")
    private List<Author> authors;

}
```

### Many-to-One Relationship

@ManyToOne Annotation The @ManyToOne annotation is used to define a many-to-one relationship between two entities in Spring Data JPA. The child entity, that has the join column, is called the owner of the relationship defined using the @ManyToOne annotation.

## Integration Testing in Spring

The integration testing role in the application development cycle is verifying the end-to-end behavior of a system.
Spring MVC Test Configuration.

### Enable Spring in Tests with JUnit 5

```
@ExtendWith(SpringExtension.class)
@ContextConfiguration(classes = { ApplicationConfig.class })
@WebAppConfiguration
public class GreetControllerIntegrationTest {
    ....
}
```

### Verify Test Configuration

```
@Test
public void givenWac_whenServletContext_thenItProvidesGreetController() {
    ServletContext servletContext = webApplicationContext.getServletContext();

    Assert.assertNotNull(servletContext);
    Assert.assertTrue(servletContext instanceof MockServletContext);
    Assert.assertNotNull(webApplicationContext.getBean("greetController"));
}
```

### Writing Integration Tests

```
@Test
public void givenHomePageURI_whenMockMVC_thenReturnsIndexJSPViewName() {
    this.mockMvc.perform(get("/homePage")).andDo(print())
      .andExpect(view().name("index"));
}
```

### MockMvc Limitations

it does use a subclass of the DispatcherServlet to handle test requests.

The MockMvc class wraps this TestDispatcherServlet internally. So, every time we send a request using the perform() method, MockMvc will use the underlying TestDispatcherServlet directly.

because Spring prepares a fake web application context to mock the HTTP requests and responses, it may not support all features of a full-blown Spring application.

---

Resources:
Mainly:
https://www.baeldung.com/spring-data-rest-relationships
https://www.baeldung.com/integration-testing-in-spring

From google search:
https://springframework.guru/spring-framework-annotations/
https://attacomsian.com/blog/spring-data-jpa-one-to-many-mapping
https://docs.oracle.com/javaee/6/api/javax/persistence/
