> Data Mapper is the software layer that separates the in-memory objects from the database. Its responsibility is to transfer data between the objects and database and isolate them from each other. If we obtain a Data Mapper, it is not necessary for the in-memory object to know if the database exists or not. The user could directly manipulate the objects via Java command without having knowledge of SQL or database.

## [#](https://java-design-patterns.com/patterns/data-mapper/#explanation)Explanation

Real world example

> When a user accesses a specific web page through a browser, he only needs to do several operations to the browser. The browser and the server will take the responsibility of saving data separately. You don't need to know the existence of the server or how to operate the server.

In plain words

> A layer of mappers that moves data between objects and a database while keeping them independent of each other.


