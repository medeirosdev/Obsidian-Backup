ActiveRecord is a Ruby on Rails’ ORM layer, roughly comparable to Hibernate in Java. ActiveRecord is based on conventions rather than configuration, so it is easier to work with than Hibernate. It really shines when it comes to simplifying the basic operations for creating, reading, updating, and deleting data.

With ActiveRecord, your model class doubles as a Data Access Object (DAO) to perform the CRUD operations. After my early investigations I was so impressed with ActiveRecord that I started looking for solutions that simplify usage of ORMs based on the Java Persistence API (JPA).

Most JPA applications have some kind of Data Access Layer (DAL) to interact with the database. Usually a DAL consists of Data Access Objects (DAO) or classes of the [Repository design pattern](http://martinfowler.com/eaaCatalog/repository.html).

**Code, deploy, and scale Java your way.**  
Microsoft Azure supports your workload with abundant choices, whether you're working on a Java app, app server, or framework. **[Learn more](https://www.infoq.com/url/f/242996dc-82ab-4dd7-aa32-a24fc5f7a25a/).**

While a DAO is usually implemented in a one-to-one relationship with an entity object, repositories are implemented per [aggregate root](http://martinfowler.com/bliki/DDD_Aggregate.html). In either case these applications end up creating multiple classes to interact with the database. While the right kind of abstraction can limit the number of classes created, it still introduces an additional layer that you have to maintain and test in your application.

[ActiveJPA](https://github.com/activejpa/activejpa) is a Java implementation of [Martin Fowler’s Active Record pattern](http://www.martinfowler.com/eaaCatalog/activeRecord.html) over JPA. It wraps around JPA and provides useful abstractions to simplify data access. With ActiveJPA, models themselves act as a DAO and interact with the database without you having to write any additional code for the DAL.

Since ActiveJPA uses the JPA spec, all ORM implementations (Hibernate, EclipseLink, OpenJPA, etc.) that implement JPA can be used with ActiveJPA.