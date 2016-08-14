#### psjavaee7fundanote
######4 Thanks
basic:
```
@Entity
public class Book{
  @Id
  private Long id;
  private String title;
}
```
service, manipulating
```
public class BookService{
  @Inject
  private EntityManager em;
  public void persistBook(Book book){
    em.persist(book);  
  }
  public Book findBook(Long id){
    return em.find(Book.class,id);
  }
}
```
######8 What is
persistence.xml
```
<persistence xmlns:
<persistence-unit name="ke" transaction
<description>
<properties>
  <property name="javax.persistence.schema-generation..
</properties>
</description>
</persistence>
```

use mvn to create package
```
mvn clean package
```
use wildfly to deploy.
######13 Injection
CDI->Context Dependency injection
######14  CDI lifecycle
new annotation
```
@PostConstruct
```
deployment descriptor
```
beans xmlns=""
alternatives
  class
interceptors
  class
```
some cdi api
```
javax.inject
javax.enterprise.inject
javax.enterprise.context
javax.enterprise.event
javax.interceptor
javax.decorator
javax.enterprise.util
```

######17
```
@ApplicationScoped
@SessionScoped
@RequestScoped
@ConversationScoped
```

Conversation Scope
```
@ConversationScoped
public class CustomerWIzard implements Serializable{
  @Inject
  private Conversation conversation;
  ...
  public void init(){
    conversation.begin();
  }
  public void end(){
    conversation.end();
  }
  
}
```

######20 Intercepting calls
```
@Loggable
@Interceptor
public class LoggingInterceptor{
@Inject
private Logger logger;

@AroundInvoke
private Object intercept(InvocationContext ic)throws Exception{
  logger.info(,ic.getMethod()
}
```
######22 Understanding bean validation
```
public class Customer{
  @NotNull
  @Size(min=4,max=10)
  private String firstName;
  
  @Past
  private Date dataOfBirth
}
```
validator
````
public class PurchaseService{
  @Inject
  private Validator validator
  
  private Set<ConstraintViolation<Customer>> violation;
  
  public void createCustoer(Customer customer)
  {
    violations = validator.validate(customer);
    if (violations.size()>0) throw new ContranitViolationException(violations);
  }
}
```
######23 Build in contraints
```
@Size
@Digits
@Max Min
@DecimalMax DecimalMin
```
```
@Future
@Past
```
object
```
@Null
@NotNull
```
regex:
```
public class Book{
  @Pattern(regexp = "^(07(8|9))?\\d{9}(\\d|X)$")
  private String isbn;
}
```

######24 Own constraint
```
@Target(TYPE)
@Retention(RUNTIME)
@Documented
@Constraint(validatedBy = ChronologicalDatasValidator.class)
public @interface ChronologicalDates{
}
```
######28 JPA
jpa packages
```
javax.persistence
javax.persistence.criteria
javax.persistence.metamodel
javax.persistence.spi
```
