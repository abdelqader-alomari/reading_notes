# Read: 18 - Web App Security

## Many to many relationships

### Example

![Many to Many](https://www.baeldung.com/wp-content/uploads/2017/09/New-768x152.png)

Here In this scenario, any given employee can be assigned to multiple projects and a project may have multiple employees working for it, leading to a many-to-many association between the two.
A join table employee_project is required here to connect both sides.

### Model Class

#### Employee Class

```
@Entity
@Table(name = "Employee")
public class Employee {
// ...

    @ManyToMany(cascade = { CascadeType.ALL })
    @JoinTable(
        name = "Employee_Project",
        joinColumns = { @JoinColumn(name = "employee_id") },
        inverseJoinColumns = { @JoinColumn(name = "project_id") }
    )
    Set<Project> projects = new HashSet<>();

    // standard constructor/getters/setters

}
```

#### Project Class

```
@Entity
@Table(name = "Project")
public class Project {
// ...

    @ManyToMany(mappedBy = "projects")
    private Set<Employee> employees = new HashSet<>();

    // standard constructors/getters/setters

}
```

In order to map a many-to-many association, we use the @ManyToMany, @JoinTable and @JoinColumn annotations

The @ManyToMany annotation is used in both classes to create the many-to-many relationship between the entities.

This association has two sides i.e. the owning side and the inverse side.

### Testing

```
@Test
public void givenData_whenInsert_thenCreatesMtoMrelationship() {
String[] employeeData = { "Peter Oven", "Allan Norman" };
String[] projectData = { "IT Project", "Networking Project" };
Set`<Project>` projects = new HashSet<>();

        for (String proj : projectData) {
            projects.add(new Project(proj));
        }

        for (String emp : employeeData) {
            Employee employee = new Employee(emp.split(" ")[0],
              emp.split(" ")[1]);

            assertEquals(0, employee.getProjects().size());
            employee.setProjects(projects);
            session.persist(employee);

            assertNotNull(employee);
        }
    }
```

## Security a humorous overview

![web security](https://lvivity.com/wp-content/uploads/2019/11/wa_secure.jpg)

It's almost as though security researchers have issues with public relations since they make it impossible to do everything you want on a website. Security experts are always working to address security vulnerabilities and improve people's ability to establish more secure passwords. Any password may be hacked. Using the same password for everything isn't a smart idea. Security researchers utilize the threat model to prevent security breaches by instructing individuals on how to create passwords and where security risks originate, although security breaches don't always come from apparent sources. There is no such thing as a flawless security system, and any security system, no matter how robust, will be breached at some point. To make things more safe, information flow control and security labels are employed. The majority of individuals do not want to pay a lot of money merely to make their system safer. As a result, security researchers should focus on what will happen when I properly construct my software, rather than what may happen.

- Seems you have to find a balance when it comes to passwords and security.
- There will always be those that are trying to hack.
- Make sure to have strong passwords!
- Should we care more about how to put our data on websites like email account should be with strong password
- And should be aware of Organized criminals who breaking into email account and sending spam using identity ...

---

## Resources

1. <https://www.baeldung.com/hibernate-many-to-many>
2. <https://scholar.harvard.edu/files/mickens/files/thisworldofours.pdf>
3. Google.com

---

```

```
