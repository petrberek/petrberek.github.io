# Two views how to use Code First with Entity Framework

Many developers use code first techniques to develop application which works with database through Entity Framework. Code first means that developer creates entity in non SQL language, i.e. C#. Entity framework can produce database schema based on these entities.  

It allows to have focus on code instead of have focus on database. Entity framework can apply all changes on entities to database. It leads to database is deployed with application and deployment is more easy. You can read that Code First is useful for Domain Driven Design.[[1]]  I think Domain Driven Design is more complex and it helps you how to recognize domains and establish collaboration between them. So I think Code First could be useful in domain model and model driven design generally.  

Code first is very useful feature. Based on architecture style we can have two options how to code first use.  

Most tradition architectures have three layers:
- Presentation layer is for interaction with user or another systems. Some data transformation logic of presentation logic should by here.
- Business layer is layer where business logic is placed.
- Data (or database) layer is layer where some database queries are placed and data manipulation is here. 

Entity framework works with database so it is layed in data layer. It means implementation of DbContext is here. DbContext contains DbSets through that we can access to database. Each entity created by Code First should has own DbSet.  

## Database Code First
In traditional development first focus is on database. At first we need to create database, tables, views and another database objects. Tables has relations and constraints. Then we write some non-SQL code to data manipulation (CRUD) in application. With code first we are happy we cannot create tables and data manipulation code because it is provided by Entity Framework. What we need to do is create entities.  
When we have tradition architecture where higher layer has reference to lower layer, we need to create entities in most lower layer to use them in higher layer. It means our entities will be in data layer. It leads to entities will be more like as we would like to begin with database schema. We will have focus to all relations and constraints between entities. This is reason I call this view __Database Code First__.  
This approach can be used for small project without or with small amount of business logic. When amount of entities grows then grows complexity of relations between them. DbSet provides IQueryable interface which is used to create queries to entities and thus create SQL queries. When IQueryable interface is exposed to business layer data manipulation responsibility is shifted from data layer to business layer because LINQ Query is more something like SQL query which should by encapsulated in data layer. So in large project we lose track of data manipulation tasks. 

## Business Code First
In this approach we need to change our view to architecture. Higher layer is not presentation but business layer. It means business layer has not any reference to any layer. 


[1]: <https://www.entityframeworktutorial.net/code-first/what-is-code-first.aspx>