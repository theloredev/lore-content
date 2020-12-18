---
id: database
title: Database
sidebar_label: Database
---

> "Once the business data have been centralized and integrated, the value of the database is greater than the sum of the preexisting parts." - Larry Ellison, Oracle founder

The use of databases are important to most systems because they provide the ability to store and retrieve data. Data is some of the most valuable assets that a company can have. 
There are two main types of databases, relational and non-relational; which then further subdivide into quite a few specialized types (particularly on the non-relational database side of things).

## Value of Database Naming Conventions

Imagine a database with a few hundred tables, and the names of each table are a mix of camelCase, PascalCase, ALLCAPS, ALL_CAPS_WITH_UNDERSCORES, etc. Column names might be a similar mix, and it is nearly impossible to track down which column might represent the Primary Key based on name alone. To make matters even worse, there may be some seemingly duplicate tables, such as user_accounts, userAccounts, and USER_ACCOUNTS.

This database would be a nightmare to support and maintain, but it doesn’t have to be this way. By defining clear Naming Conventions while designing the data model, you can save yourself, and other developers, a lot of headaches down the road.

Naming conventions need to encompass all aspects of a database. Don’t just apply them to the obvious and frequently used portions, such as tables, schemas, views, columns, and keys; but ensure they are applied to everything, including things like constraints, indexes, [stored procedures & functions](#naming-conventions-for-stored-procedures-and-functions), triggers, schedule database jobs, etc.

The conventions you apply should be logical in their naming. For example, using “PK” as a prefix on a Primary Key makes logical sense. It is also easy to interpret and implement, both major pluses when coming up with your database’s naming conventions.

Also, take into consideration who will be working with your database. For example, if you are creating a database that is primarily going to be accessed by Java developers, consider using camelCase as your naming standard since conventional naming of methods in Java also uses camelCase. On the other hand, if you are implementing a database that is going to be accessed by some legacy system, be sure the naming conventions used are compatible with that system before you begin.

You should attempt to avoid using any reserved words found in SQL or in the DBMS you are implementing your database on. 

## Relational Databases

The Relational Database theory was invented by E.F. Codd at IBM in 1970 but it took until 1979 when Oracle released the first Relational Database Management System (RDMS). We use the term “relational” because the main point of this database architecture is the ability to create relationships between different pieces of data.

Relational Databases use a structured schema to construct tables, with each table being constructed of columns and rows.
 
Each table can have a column designated as the primary key and multiple columns designated as foreign keys. Each of the foreign keys link to a unique primary key. This is how all of the relationships in this form of database are constructed.

Data is Created, Read, Updated, and Deleted (CRUD) from a relational database via Structured Query Language (SQL). Queries can be written to access data, join tables together by the primary and foreign keys, determine specific data constraints, access specific portions of tables, and order and sort the results, among a host of other actions that SQL can perform. 

### Stored Procedures and Stored Functions

When used properly, stored procedures and stored functions offer a number of advantages, including protection against security risks such as SQL injection, access to advanced and rapid numerical data analysis functionality, and the ability to isolate code functionality (see [Separation of Concerns](/development/writing-code.md#separation-of-concerns)).

In many cases, stored procedures and stored functions can improve speed and performance because the procedure or function is *"cached in the server memory and its execution is much faster than dynamic SQL"*, [{codng}Sight](https://codingsight.com/dynamic-sql-vs-stored-procedure/#:~:text=Stored%20procedures%20beat%20dynamic%20SQL,stored%20procedure%20outperforms%20dynamic%20SQL.). This is particularly true for complex, resource-intensive SQL queries and operations.

According to database expert Don Burleson, stored procedures and functions *"load once into the shared pool and remain there unless they become paged out."* As a result, repeated execution of the same procedure or function is *"far faster than executions of external code"*. Burleson Consulting

#### Securing your stored procedures with bind variables

To prevent the likelihood of a SQL injection attack, the use of Bind Variables in stored procedures is highly recommended.  Bind variables help enforce data type constraints and escape characters.

By enforcing data type constraints and escape characters, bind variables help prevent situations where unchecked, malicious strings are sent to your procedure which allow for remote code execution, unauthorized modification of databases, and remote application execution. 

Let's take a quick look at an example using a Bind Variable *'myname'* in Oracle PL/SQL. Similar concepts can be applied when using other database platforms:

```sql
CREATE OR REPLACE PROCEDURE myTestFunction(myname IN VARCHAR2) AS 
BEGIN
	EXECUTE IMMEDIATE 'UPDATE weightList set weight = 150 
     where name = :1' USING myname; 
     -- :1 was substituted with the 'myname' bind variable
COMMIT; 
END;
```

The use of the bind variable above automatically handles data type constraints and escape characters, making it more difficult for potential hackers to compromise your database by sending malicious commands that could result in dangerous database modifications or unauthorized code or program execution. 

Bind variables also help improve overall database performance. Bind "are «substitution» variables that are used in place of literals."  This enables your database to re-use the same execution plan each time the procedure is run. 

<https://www.akadia.com/services/ora_bind_variables.html>

#### Proper error handling

There are 2 rules to follow when building stored procedures:

- Always use error handling. Experts recommend that you always *"include an exception handler for every logical grouping of...statements (BEGIN/END block)."*
<https://www.budaconsulting.com/2016/06/29/best-practices-for-error-handling-in-database-stored-procedures/>
- Always handle and log exceptions. It is recommended that you develop a separate Log function or stored procedure to log errors in detail.
    - *"By creating a separate logging procedure that you call at the beginning, at various points within the code, and in exception blocks, you can always know exactly which processes completed before a failure."* 
    <https://www.budaconsulting.com/2016/06/29/best-practices-for-error-handling-in-database-stored-procedures/>

Here is an example of the correct way to use error handling to properly handle and log exceptions.  While this example may be specific to Oracle, similar concepts can be applied when using other database platforms.

```sql
CREATE OR REPLACE procedure update_case_file(case_number IN varchar2)
AS

BEGIN
update vouchers set status = 'IV' where voucher_no in (select    voucher_no from vouchers v where v.case_no = case_number)
	and status ='NIB';

COMMIT;
	-- log a message to the terminal if everything went well
dbms_output.put_line('update_case_file was Successful');

EXCEPTION	-- ERROR HANDLING
WHEN OTHERS THEN   -- what we do when an error happens

-- print a message to the terminal
 dbms_output.put_line('Errors'||SQLCODE ||'Message'||SQLERRM);

	-- Use a centralized procedure or function to log the 
-- error and its origin. This procedure could send the 
-- error to a file, database table, or terminal screen

	UPDATE_ERR_LOG(SQLCODE, SQLERRM, 'update_case_file');   
	-- We have captured the SQL error code, SQL error message, 
-- and the source of the error

END update_case_file;
```

#### Naming conventions for stored procedures and functions

There is no universally accepted naming convention for stored procedures and functions. You should choose a [naming convention](/development/writing-code.md#define-and-keep-a-consistent-style-guide) that fits your team, system, and organization. The 3 most important details to remember are the following:

- A naming convention must be chosen.
- The naming convention must be enforced.
- The naming convention must be consistent.

Dr. Timothy Hall and Don Burleson suggest naming conventions for stored procedures and stored functions that have been widely accepted by many teams and organizations.

    "Naming conventions for stored procedures and functions are relatively simple. They begin with the 3-digit application abbreviation, have a functional name, and end with one of these options:

    - PL/SQL Packages:	NAME_PKG
    - PL/SQL Procedures:  NAME_PRC
    - PL/SQL Functions:   NAME_FUN

    For example, we might have these names:

    - GEN_ADD_CUSTOMER_FUN
    - HSD_PROCESS_ORDER_PRC"

    PL/SQL naming conventions, Don Burleson, Burleson Consulting

When writing your stored procedures and functions, Dr. Timothy Hall suggests:

    "variables are prefixed with a single letter, if possible, to indicate their type or usage.

    Package Global Variables	: g_variable_name
    Local Variables         	: l_variable_name
    Types                   	: t_type_name
    Cursors                 	: c_cursor_name
    Exceptions              	: e_exception_name
    Input Parameters        	: i_parameter_name
    Output Parameters        	: o_parameter_name
    In/Out Parameters       	: io_parameter_name"

    Oracle-Base: Naming Conventions, Dr. Timothy Hall, Rampant Books & Burleson Consulting

#### Using packages and schemas to organize stored procedures and functions

Whenever you have multiple stored procedures or stored functions that handle the same business logic or form the foundation for similar blocks of software programming code, you should consider organizing your procedures and functions using packages.  It is also a great idea to include any related user-defined types in those packages, if possible.

Here is an example of a database package used to group procedures and functions related to customer data for an application:

| ![](assets/development/database/procedure.png) |
|:--:|
| *Credit: [Navigating Your PL/SQL Packages in Oracle SQL Developer](https://www.thatjeffsmith.com/archive/2012/11/quick-outline-navigating-your-plsql-packages-in-oracle-sql-developer/)* |

Bundling your stored procedures, functions, and user-defined types into packages will make your application easier to maintain and easier to understand for new developers joining your teams.  Using packages will also make your application more portable if you ever need to migrate your application to a new database server.  Creating packages within the database can also make it easier to create regular backups of the database code that drives your application. 

Packages for stored procedures and stored functions *"allow you to encapsulate, or group, related stored procedures, variables, datatypes, etc. in a single named, stored unit in the database. This provides for better organization during the development process."*  <https://docs.oracle.com/cd/A57673_01/DOC/server/doc/SCN73/ch14.htm#:~:text=Stored%20packages%20allow%20you%20to,also%20makes%20privilege%20management%20easier.>

Not all database platforms offer a packages feature.  For example, packages are available in Oracle but are not available in Microsoft SQL Server and several other database platforms.  However, your database platform might offer a similar concept. 

For example, in Microsoft SQL Server, schemas are available that enable you to cleanly organize your stored procedures and functions. You can create multiple schemas to group stored procedures and stored functions by system functionality.  Here's an example:

    Customer.add_customer
    Customer.update_customer
    Customer.return_item
    Manager.add_manager
    Manager.interview_candidates
    Manager.hire_store_clerk
    StoreClerk.add_store_clerk
    StoreClerk.receive_promotion

In the example above, we have created 3 schemas: Customer, Manager, and StoreClerk. WIth these new schemas, we can associate certain stored procedures and stored functions with the appropriate people or "actors" within our system.

#### When to use a Stored Procedure versus a Stored Function

Simply put, a Stored Function should be used to return a value or multiple values, while a Stored Procedure should be used to perform operations or work where no return values are required. 

A Stored Function *"takes a set of inputs, and *derives* something based on those inputs. So typically it would not *alter* the state of anything, it merely comes up with a new value."*
<https://asktom.oracle.com/pls/apex/f?p=100:11::::RP:P11_QUESTION_ID:9538125800346011641>

A Stored Procedure *"takes a set of inputs and *performs* something based on those inputs. So those inputs are used to *do* something, rather than *derive* something."* If you are using any type of "output" parameter for a Stored Procedure, you probably should consider using a Stored Function Instead.
<https://asktom.oracle.com/pls/apex/f?p=100:11::::RP:P11_QUESTION_ID:9538125800346011641>

Here is an example of a **Stored Function** which returns a numeric value. Although this example is Oracle-specific, similar concepts can be applied when using other database platforms. 

```sql
CREATE OR REPLACE FUNCTION Get_Status(p_voucherNo IN VARCHAR2 )
  RETURN PLS_INTEGER    
-- A 'return' TYPE is specified because Stored Functions
-- should return a value. We are returning an Integer.
IS
v_status_id NUMBER;
BEGIN

SELECT c.status_id
INTO v_status_id
FROM vch_status c
WHERE c.status_code =
    (SELECT v.status
    FROM vouchers v
    WHERE v.voucher_no=p_voucherNo
    ) ;

-- If our query was successful, we will return 
-- 'v_status_id' as our Integer return value.
RETURN v_status_id;

EXCEPTION	-- error handling

WHEN OTHERS THEN	
-- Since this is a Function, we always return a value: 
-- A default value is returned if an exception occurred. 
RETURN 0;  

END Get_Status;
```

Here is an example of a **Stored Procedure** which performs a task but returns no value. Although this example is Oracle-specific, similar concepts can be applied when using other database platforms. 

```sql
-- Notice that no return TYPE is specified in the procedure 
-- declaration because we will not return any value

CREATE OR REPLACE PROCEDURE FC_MOVE_EXPIRED_VCHRS
AS     
BEGIN
-- A simple procedure to update the 'status' column for 
-- a group of records based on some business rules in 
-- 'isPastThe16th'
update fc_vouchers set status='NS' where 
WVS_FC_VOUCHERLIST_V3.isPastThe16th(voucher_no)=1  
and status = 'CUR'; 

COMMIT; 

EXCEPTION   -- error handling

WHEN OTHERS THEN  
-- For our scenario, we are ignoring the error to 
-- keep this example simple

	RETURN;   
-- Notice that the procedure ends by returning NO value

END FC_MOVE_EXPIRED_VCHRS;
```

### ACID Properties

A database is only as good as the consistency of the data stored within it. In order to maintain the consistency of data in a database, there are a series of properties that should be followed on all transactions. These properties are known as the ACID properties, which is an acronym for Atomicity, Consistency, Isolation, and Durability.

A transaction against the contents of a database is any single logical unit of work that performs any single or series of CRUD (create, read, update, delete) interactions with the data.

#### Atomicity

This property could be called "all or nothing," meaning that all pieces of a transaction will succeed, or none of it does. There is no midway point, transactions do not partially complete. Each transaction either runs to completion, or it doesn't run at all.

#### Consistency

This property relies on all of the rules that have been defined within the database, including constraints, cascades, and triggers, to guarantee that all data will be consistent. Data that is saved cannot violate the integrity rules defined within the database. Additionally, any transactions that fail result in rollbacks of the transaction’s prior changes, ensuring that the data remains consistent, and looks like it did prior to the transaction starting.

#### Isolation

Each transaction must execute independently of any other concurrent transactions taking place on the database. Any changes made in a transaction will only become visible once the transaction completes successfully. Another way to say this is that a transaction won't be able to read data from any other transaction that has yet to complete.

#### Durability

Once a transaction completes successfully, the data is persisted so that, even if a system failure occurs, the data from the transaction is guaranteed to be in the stored data. This also means that if the system informed the user the transaction was successful, then the transaction is guaranteed to have been successful (so essentially the database won't lie to the user).

A great example of ACID Properties at work would be bank transactions.  Transferring money from one account to another must either be completely successful, or fail. Money can’t leave the first account, and never make it to the second (Atomicity). The data for the transaction, such as the amount of the transfer, cannot violate a constraint in the database, such as not permitting NULL as the transfer amount (Consistency). The transaction where the money is transferred must take place independently from any other transactions on the two accounts (Isolation). Finally, once the transaction is successfully complete, even if the database goes offline, the changes made by the transaction have been saved (Durability).

All of the major Relational Databases support the ACID Principles. Non-Relational Databases are a bit different, and as such, they don't necessarily adhere to all of the ACID Principles. Some do ahear to some degree of Atomicity, and there are some that will function with the concept of "Consistency eventually," where data will eventually be synced across database clusters.

### Normalization Recommendations

> "Database normalization is the process of structuring a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity." - https://en.wikipedia.org/wiki/Database_normalization

#### Reducing Redundancy

Relational Databases are built for relationships, and these relationships can be leveraged in order to reduce the redundancy of stored data. When properly structured, the same single piece of data can be referenced in multiple places throughout the database.

For example, a user’s address is best stored in a single location, rather than replicated across multiple tables. The address can have relationships created between numerous tables, but that data is stored in a single table on a single row. When the user updates their address, that update is reflected across the entire database that has a relationship with that table.

Advantages of normalization are:
- As data redundancy decreases, the integrity and consistency of the data within the database increases.
- CRUD actions only need to be executed once, rather than against numerous tables.
- Changes are immediately reflected across the whole application.
- Queries against the data are simpler to compose.

#### Normal Forms

There is a standard collection of normalization rules that can be applied to relational databases known as Normal Forms. 

Below are the various Normal Forms, and a brief explanation of the rules that apply to each. Each Normal Form must comply with all of the rules above it. Highly detailed explanations of each Normal Form is beyond the scope of this document, but there are numerous books and external websites dedicated exploring Normalization and each of the Normal Forms.

- 1st Normal Form (1NF)
    - Each record must be unique
    - Columns can only contain a single value (atomic values)
- 2nd Normal Form (2NF)
    - All the columns depend on the table’s Primary Key (tables serve a single purpose)
- 3rd Normal Form (3NF)
    - All the columns are not transitively dependent on the Primary Key (a table’s data must depend only on the table’s Primary Key, and not on any other field in the table)
- Boyce-Codd Normal Form (BCNF)
    - An extension of 3NF, and most tables in 3NF comply with BCNF. Only becomes an issue when there are multiple overlapping candidate keys for a table (composite Primary Keys constructed out of more than one column)
    - There can be no non-trivial functional dependencies of attributes on anything other than a superset of a candidate key.
- 4th Normal Form (4NF)
    - A table cannot have any multivalued dependencies other than a candidate key.
- 5th Normal Form (5NF)
    - A table cannot be decomposed any further with different candidate keys.
- 6th Normal Form (6NF)
    - When a row in a table contains at most, the Primary Key and one additional column.

#### How Normalized?

Obviously, it depends on the needs of the business, and the format of the source data. Traditionally, data is normalized to the 3rd or 4th Normal Form. Extending past that point, to the 5th or 6th Normal Forms results in an unnecessarily complex database with no real gains. For the most part, the 5th and 6th Normal Forms are considered primarily to be of academic interest, and nothing more.

### Data Modeling

Data Modeling is the process of creating a model or blueprint for the data that will be stored in the database; including the structure of the data objects, associations, and business rules. We use this process to ensure that the database will:

- Reflect real life as much as possible 
- Construct and define relationships between data
- Ensure all the business rules concerning data are implemented within the database before application implementation
- Resolve problems before implementation

This phase is broken into several steps, which end up constructing a complete design for the database’s structure.

#### Conceptual Model

The Conceptual Model’s primary goal is to identify the different entities, their attributes, and any possible relationships between the entities. Focusing exclusively on these areas means we don’t need to concern ourselves on ID’s or Primary & Foreign Keys, but just on the bigger picture and relating the model to the business requirements and the scenario that is looking to be solved.

#### Logical Model

The Logical Model aims to build the relationships between the entities that we created in the Conceptual Model phase, which creates the base for the Physical Model. Once again, this phase has us building a high-level model and not implementing anything yet.

#### Physical Model

The final phase is to create the actual Physical Model, which involves constructing the real tables that contain fields that will store our data in our database. This is where you should apply the [naming conventions](#value-of-database-naming-conventions) across the entirety of your database, standardizing the naming of tables and fields. 

#### Data Modeling Tools

Below are some great tools to create data models: 

- Oracle Data Modeler*
- IBM - InfoSphere Data Architect
- Erwin Data Modeler
- Navicat Data Modeler
- PowerDesigner
- RISE*
- ModelSphere*
- Archi*
- Oracle SQL Developer

**Offers free edition or is free to use*

### Popular Relational Databases

There are quite a few different RDBMSes out there. In fact, there are a lot! Some of the largest players in the market currently are:

- Oracle
- MySQL
- Microsoft SQL Server
- PostgreSQL
- IBM DB2
- IBM Informix
- Sybase

Check the [current database rankings](https://db-engines.com/en/ranking) to see a complete list of database engines and their popularity.

### Advantages

- Well structured when data is properly normalized.
- Normalized data is predictable thanks to that structure
- Relationships and structure allow for clearly defined data constraints
- Handles complex queries that span multiple tables via joins quite well

### Disadvantages

- Data migrations between systems are a major hassle due to the rigid schema.
- Due to their structure, they scale vertically (CPU, RAM, Disk space) which works well for midrange applications, but resources will eventually run out for larger applications.

## Non-Relational Databases

There are quite a few different types of Non-Relational Databases, but they all share a key common feature. Their structure lacks the rigid schema of their relational counterparts, and replaces it with a more free-form structure which allows more flexibility in the way data is structured and stored. They are built to handle unstructured data.

### Choosing the Right Type

#### Types

- Document Store: Data is stored as semi-structured JSON documents, and while they resemble key-value stores, they process data differently. Most of the popular Non-Relational/NoSQL databases fall into this category.
- Key-Value Store: Designed to store key-value pairs. Also described as storing associative arrays, maps, or dictionaries, which are all synonyms. Stores data using a variety of optimal options to classify the data types of the values.
- Wide Column: Also known as a multidimensional key-value store, this is ideal for managing massive amounts of data (think petabytes), as the value can have billions of possible columns to store data in.
- Graph: Basically, it is a collection of relationships and is useful for analyzing different types of data and the relationships between that data.
- Search Engine: Really more of a specialized sub-type of Document Stores, which optimize data to make it more available for text-based searches.

### Popular Non-Relational Databases

- MongoDB
- Elasticsearch
- Redis
- Cassandra
- Splunk
- Amazon DynamoDB
- Solr

Check the [current database rankings](https://db-engines.com/en/ranking) to see a complete list of database engines and their popularity.

### Advantages
- Does not require a predefined schema.
- Perfect for handling unstructured or multi-structured data.
- Also handles abstract data quite well.
- Designed to easily manage huge amounts of data.
- This data scales horizontally very well, and can be distributed across multiple nodes for better access speeds.
- Requires fewer computing resources.

### Disadvantages

- Data contained in fields may not be reliable, as there is no specific structure or schema of the stored data.
- The lack of relationships between data makes updating a single detail potentially time consuming, as the data that needs to be updated may be duplicated across the database. 

## Relational Databases vs Non-Relational Databases

So how do you go about choosing which type of database you should use to meet the requirements of a new system you need to develop? There are numerous blog posts describing the merits of both, and how to go about choosing between the different types. In this, we will list some commonly brought up things to consider.

- How well structured is the data that you anticipate storing and similarly, how critical is the data’s integrity and validity? 
    - If you find yourself needing to follow the ACID Principles, then a relational database may be your best option. 
    - If your data is less structured, and more fluid, then a non-relational database may meet your needs.
- How much data are you anticipating, and what about scalability?
    - If you need to store incredibly huge amounts of data, like multiple petabytes of data, then non-relational is definitely the way to go.
    - Additionally, if you need to replicate some portions of data across multiple database systems in an effort to increase performance, then non-relational is also your best choice.
    - For smaller, less data hungry systems, and systems that can work well with vertical scalability, then a relational database may work best.
- Consider support costs - how much will this cost to host?
    - Every web hosting company supports MySQL, an incredibly popular relational database.
    - Take into account the associated costs with regards to a powerful system up front to scale vertically vs the need for multiple systems to scale horizontally.
- What kind of detailed queries are you looking to run on this system?
    - As stated above, complex queries work best on relational databases. They are possible on non-relational systems, but don’t anticipate the performance to be as good.

## References

- <https://www.astera.com/type/blog/a-quick-overview-of-different-types-of-databases/>
- <https://www.geeksforgeeks.org/difference-between-sql-and-nosql/>
- <https://www.dataversity.net/a-brief-history-of-non-relational-databases/>
- <https://en.wikipedia.org/wiki/Database_normalization>
- <https://www.informit.com/articles/article.aspx?p=30646>
- <https://www.budaconsulting.com/2016/06/29/best-practices-for-error-handling-in-database-stored-procedures/>
- <https://www.akadia.com/services/ora_bind_variables.html>
- <https://asktom.oracle.com/pls/apex/f?p=100:11::::RP:P11_QUESTION_ID:9538125800346011641>
- <https://www.thatjeffsmith.com/archive/2012/11/quick-outline-navigating-your-plsql-packages-in-oracle-sql-developer/>
- <https://oracle-base.com/articles/misc/naming-conventions>
- <http://www.dba-oracle.com/t_plsql_naming_standards.htm>
- <https://codingsight.com/dynamic-sql-vs-stored-procedure/#:~:text=Stored%20procedures%20beat%20dynamic%20SQL,stored%20procedure%20outperforms%20dynamic%20SQL.>
