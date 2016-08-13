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
