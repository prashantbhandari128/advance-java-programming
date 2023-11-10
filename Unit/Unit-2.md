<div align="center">

[**_``Go Back``_**](../README.md)

# Database Programming

</div>

## JDBC
-------
JDBC stands for ``Java Database Connectivity`` , which is a standard Java API for database-independent connectivity between the Java programming language and a wide range of databases.

The ``JDBC`` library includes APIs for each of the tasks mentioned below that are commonly associated with database usage.

- **Making a connection to a database.**
- **Creating SQL statements.**
- **Executing SQL queries in the database.**
- **Viewing & Modifying the resulting records.**

Fundamentally, ``JDBC`` is a specification that provides a complete set of interfaces that allows for portable access to an underlying database. Java can be used to write different types of executables, such as:

- **Java Applications**
- **Java Applets**
- **Java Servlets**
- **Java ServerPages (JSPs)**
- **Enterprise JavaBeans (EJBs)**

All of these different executables are able to use a ``JDBC`` driver to access a database, and take advantage of the stored data.

``JDBC`` provides the same capabilities as ``ODBC``, allowing Java programs to contain database-independent code.

## Design of JDBC
------------------
``Java Database Connectivity (JDBC)`` is an ``Application Programming Interface (API)``, from Sun microsystem that is used by the Java application to communicate with the relational databases from different vendors. Design of JDBC defines the components of JDBC, which is used for connecting to the database.

### **JDBC Architecture**

``JDBC (Java Database Connectivity)`` follows a well-defined architecture that allows Java applications to interact with relational databases. This architecture consists of several key components and layers, which work together to facilitate database access and operations. 

<div align="center">

![JDBC Architecture](img/Architecture-of-JDBC.webp)

</div>

- **``Application``**: It is a java applet or a servlet that communicates with a data source.

- **``The JDBC API``**: The JDBC API allows Java programs to execute SQL statements and retrieve results. Some of the important classes and interfaces defined in JDBC API are as follows:
    - ``Drivers``
    - ``DriverManager``
    - ``Statement``
    - ``Connection``
    - ``CallableStatement``
    - ``PreparedStatement``
    - ``ResultSet``
    - ``SQL data``

- **``DriverManager``**: It plays an important role in the JDBC architecture. It uses some database-specific drivers to effectively connect enterprise applications to databases

- **``JDBC drivers``**: To communicate with a data source through JDBC, you need a JDBC driver that intelligently communicates with the respective data source.

## JDBC Driver Types & Typical Uses of JDBC

### **JDBC Drivers**

- **Type 1 Driver (``JDBC-ODBC Bridge``)**: This driver uses ``ODBC (Open Database Connectivity)`` to connect to databases. It is not recommended for production use, as it depends on platform-specific ODBC drivers.

- **Type 2 Driver (``Native-API Driver``)**: This driver communicates directly with the database using a database-specific native API. It is platform-dependent.

- **Type 3 Driver (``Network Protocol Driver``)**: Also known as the ``Network Protocol Driver``, this driver translates JDBC calls into a database-independent network protocol, which then communicates with a server that understands the database-specific protocol.

- **Type 4 Driver (``Thin Driver``)**: The Type 4 driver, often referred to as the ``Thin Driver``, communicates directly with the database server through sockets. It is a pure Java driver and doesn't depend on any native libraries. Type 4 drivers are the most commonly used for JDBC connections.

### **Typical Uses of JDBC**
``JDBC (Java Database Connectivity)`` is a fundamental technology for connecting Java applications to relational databases. Here are some typical uses of JDBC in software development:

- **``Database Connectivity``**: ``JDBC`` is primarily used to establish connections to relational databases. Applications use JDBC drivers to connect to databases such as ``MySQL``, ``PostgreSQL``, ``Oracle``, ``SQL Server``, and more.

- **``Data Retrieval``**: You can use ``JDBC`` to execute SQL queries and retrieve data from the database. This includes retrieving specific records, aggregating data, and joining data from multiple tables.

- **``Data Manipulation``**: ``JDBC`` allows you to perform data manipulation operations on the database, such as inserting, updating, and deleting records. This is crucial for maintaining and updating the database.

- **``Batch Processing``**: ``JDBC`` supports batch processing, where you can execute multiple SQL statements as a single batch. This is useful for performing bulk insertions, updates, or deletes efficiently.

- **``Stored Procedures and Functions``**: ``JDBC`` can be used to execute stored procedures and functions that are stored in the database. This is common in enterprise applications that rely on database-side logic.

- **``Transaction Management``**: ``JDBC`` enables the management of database transactions. You can use it to group multiple SQL statements into a single transaction, ensuring data consistency and integrity.

- **``Parameterized Queries``**: ``JDBC`` supports parameterized queries using ``PreparedStatement``. This helps prevent ``SQL injection`` attacks and allows you to pass parameters securely into SQL statements.

## SQL
--------
``SQL (Structured Query Language)`` is a standardized programming language used for managing and manipulating relational databases. It provides a set of commands and syntax for interacting with databases to perform various operations such as querying data, inserting, updating, and deleting records, creating and modifying database schemas, and more. SQL is widely used in database management systems (DBMS) like MySQL, PostgreSQL, Oracle, Microsoft SQL Server, and SQLite. 

Here are some common SQL commands and operations:

### ``SELECT`` Statement: 
Used to retrieve data from one or more tables in a database.

**Example:**

```SQL
SELECT column1, column2 FROM table_name WHERE condition;
```

### ``INSERT`` Statement:
Used to add new records (rows) to a table.

**Example:**

```SQL
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

### ``UPDATE`` Statement:
Used to modify existing records in a table.

**Example:**

```SQL
UPDATE table_name SET column1 = value1 WHERE condition;
```

### ``DELETE`` Statement:

Used to remove records from a table.

**Example:** 

```SQL
DELETE FROM table_name WHERE condition;
```

### ``CREATE TABLE`` Statement:
Used to create a new table in the database with specified columns and data types.

**Example:**

```SQL
CREATE TABLE table_name (column1 datatype, column2 datatype);
``` 

### ``ALTER TABLE`` Statement:
Used to modify an existing table, such as adding, modifying, or deleting columns.

**Example:**

```SQL
ALTER TABLE table_name ADD column_name datatype;
```

### ``DROP TABLE`` Statement:
Used to delete an existing table and all its data.

**Example:**

```SQL
DROP TABLE table_name;
```

### ``CREATE INDEX`` Statement:
Used to create an index on one or more columns of a table to improve query performance.

**Example:**

```SQL
CREATE INDEX index_name ON table_name (column1, column2);
```

### ``JOIN`` Clause:

Used to combine data from two or more tables based on a related column between them.

**Example:**

```SQL
SELECT orders.order_id, customers.customer_name FROM orders JOIN customers ON orders.customer_id = customers.customer_id;
```

### ``GROUP BY`` Clause:

Used to group rows from a table based on the values in one or more columns.

**Example:** 

```SQL
SELECT column1, COUNT(column2) FROM table_name GROUP BY column1;
```

### ``HAVING`` Clause:

Used in conjunction with ``GROUP BY`` to filter grouped rows based on a specified condition.

**Example:**

```SQL
SELECT column1, COUNT(column2) FROM table_name GROUP BY column1 HAVING COUNT(column2) > 10;
```

### ``ORDER BY`` Clause:

Used to sort the result set based on one or more columns, either in ``ascending (ASC)`` or ``descending (DESC)`` order.

**Example:**

```SQL
SELECT column1, column2 FROM table_name ORDER BY column1 ASC, column2 DESC;
```

### Subqueries:

Queries nested within other queries, often used in ``WHERE`` or ``FROM`` clauses to retrieve or filter data based on results from another query.

**Example:** 

```SQL
SELECT column1 FROM table_name WHERE column2 IN (SELECT column3 FROM another_table);
```

### Views:

Virtual tables created from the result of a ``SELECT`` query. Views can be used to simplify complex queries or restrict access to certain data.

**Example:**

```SQL
CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;
```

### Transactions:

A set of SQL statements that are executed as a single unit of work. Transactions ensure the consistency and integrity of the database.

**Example:**

```SQL
BEGIN TRANSACTION;
-- SQL statements
COMMIT; -- or ROLLBACK on error
```

## JDBC Configration:
----------------------
### **Loading the JDBC Driver**
In your Java code, load the ``JDBC`` driver using the ``Class.forName()`` method. This step is required to register the driver with the ``DriverManager``.

```Java
Class.forName("com.mysql.cj.jdbc.Driver");
```

### **Create Connection Object**

You can establish a connection using the ``DriverManager.getConnection()`` method. For easy reference, let me list the three overloaded ``DriverManager.getConnection()`` methods :

* ``getConnection(String url)``

* ``getConnection(String url, Properties prop)``

* ``getConnection(String url, String user, String password)``

Here each form requires a database URL. A database URL is an address that points to your database.

Formulating a database URL is where most of the problems associated with establishing a connection occurs.

Following table lists down the popular ``JDBC`` driver names and database URL.

| RDBMS |         JDBC driver name           |                      URL format                        |
|-------|------------------------------------|--------------------------------------------------------|
|MySQL  |``com.mysql.jdbc.Driver``           |``jdbc:mysql://hostname/ databaseName``                 |
|ORACLE |``oracle.jdbc.driver.OracleDriver`` |``jdbc:oracle:thin:@hostname:port Number:databaseName`` |
|DB2    |``com.ibm.db2.jdbc.net.DB2Driver``  |``jdbc:db2:hostname:port Number/databaseName``          |
|Sybase |``com.sybase.jdbc.SybDriver``       |``jdbc:sybase:Tds:hostname: port Number/databaseName``  |

We have listed down three forms of ``DriverManager.getConnection()`` method to create a connection object. The most commonly used form of ``getConnection()`` requires you to pass a database URL, a username, and a password. 

```Java
String url ="jdbc:mysql://localhost/school";
String user="root";
String password="";
Connection con = DriverManager.getConnection(url, user, password);
```

### **Closing JDBC Connections**

At the end of your JDBC program, it is required explicitly to close all the connections to the database to end each database session. However, if you forget, Java's garbage collector will close the connection when it cleans up stale objects.

Relying on the garbage collection, especially in database programming, is a very poor programming practice. You should make a habit of always closing the connection with the ``close()`` method associated with connection object.

To ensure that a connection is closed, you could provide a 'finally' block in your code. A finally block always executes, regardless of an exception occurs or not.

To close the above opened connection, you should call ``close()`` method as follows −

```Java
con.close();
```

**Example Program:**
```Java
import java.sql.*;
import java.sql.SQLException;

class Main {
    public static void main(String [] args) {
        // Database connection parameters
        String url ="jdbc:mysql://localhost/school";
        String user="root";
        String password="";
        
        try {
            // Load the JDBC driver (required for older JDBC versions)
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
            return;
        }
        
        try(Connection con = DriverManager.getConnection(url, user, password)){
            System.out.println("Connection Sucessful");
            // Code
            con.close();
        } catch (SQLException e) {
            System.out.println(e);
        }
    }
}
```

## Working with JDBC Statements
----------------------------------
The ``Statement interface`` provides methods to execute queries with the database. The statement interface is a factory of ResultSet i.e. it provides factory method to get the object of ResultSet.

Before you can use a Statement object to execute a SQL statement, you need to create one using the Connection object's ``createStatement()`` method, as in the following example 

### Create Statemet:

From the connection interface, you can create the object for this interface. It is generally used for general–purpose access to databases and is useful while using static SQL statements at runtime.

Syntax:

```Java
Statement statement = connection.createStatement();
```

Example:

```Java
Statement s = con.createStatement();
```

**Commonly used methods of Statement interface:**

* ``public ResultSet executeQuery(String sql)``: is used to execute SELECT query. It returns the object of ResultSet.
* ``public int executeUpdate(String sql)``: is used to execute specified query, it may be create, drop, insert, update, delete etc.
* ``public boolean execute(String sql)``: is used to execute queries that may return multiple results.
* ``public int[] executeBatch()``: is used to execute batch of commands.

```Java
Statement statement = connection.createStatement();
ResultSet result = statement.executeQuery("SELECT * FROM people");
```

### Prepared Statement:

Prepared Statement represents a recompiled SQL statement, that can be executed many times. This accepts parameterized SQL queries. In this, ``?`` is used instead of the parameter, one can pass the parameter dynamically by using the methods of PREPARED STATEMENT at run time.

**Illustration:** 

Considering in the people database if there is a need to INSERT some values, SQL statements such as these are used: 

```Java
INSERT INTO people VALUES ("Ayan",25);
```
To do the same in Java, one may use Prepared Statements and set the values in the ``?`` holders, **``setXXX()``** of a prepared statement is used as shown: 

```Java
String query = "INSERT INTO people(name, age)VALUES(?, ?)";
Statement s = con.prepareStatement(query);
s.setString(1,"Ayan");
s.setInt(2,25);
s.executeUpdate();
```

**Implementation:** Once the PreparedStatement object is created, there are three ways to execute it: 

* ``execute()``: This returns a boolean value and executes a static SQL statement that is present in the prepared statement object.

* ``executeQuery()``: Returns a ResultSet from the current prepared statement.

* ``executeUpdate()``: Returns the number of rows affected by the DML statements such as ``INSERT``, ``DELETE``, and more that is present in the current Prepared Statement.

### Callable Statement:

Callable Statement are stored procedures which are a group of statements that we compile in the database for some task, they are beneficial when we are dealing with multiple tables with complex scenario & rather than sending multiple queries to the database, we can send the required data to the stored procedure & lower the logic executed in the database server itself. The Callable Statement interface provided by JDBC API helps in executing stored procedures.

Syntax: To prepare a CallableStatement

```Java
CallableStatement cstmt = con.prepareCall("{call Procedure_name(?, ?}");
```
**Implementation:** Once the callable statement object is created

* ``execute()`` is used to perform the execution of the statement.

Example Programs:

```Java
import java.sql.*;
import java.sql.SQLException;

public class CreateTable {
    public static void main(String[] args) {
        String url ="jdbc:mysql://localhost/school";
        String user="root";
        String password="";
        String query= "CREATE TABLE student (StudentID int,FirstName varchar(255),LastName varchar(255),RollNo int,City varchar(255));";
        try {
            Connection con = DriverManager.getConnection(url, user, password);
            Statement s = con.createStatement();
            s.executeUpdate(query);
            System.out.println("Table Created");
            con.close();
        } catch (SQLException e) {
            System.out.println(e);
        }
    }
}
```

```Java
import java.sql.*;
import java.sql.SQLException;

public class Insert {
    public static void main(String[] args) {
        String url ="jdbc:mysql://localhost/school";
        String user="root";
        String password="";
        try {
            Connection con = DriverManager.getConnection(url, user, password);
            Statement s = con.createStatement();
            String query= "INSERT INTO student VALUES (1, 'Prashant', 'Bhandari', 39, 'Birtamode');";
            s.executeUpdate(query);
            System.out.println("Data Inserted");
            con.close();
        } catch (SQLException e) {
            System.out.println(e);
        }
    }
}
```

## Scrollable and Upgradeable ResultSet
----------------------------------------
The SQL statements that read data from a database query, return the data in a result set. The SELECT statement is the standard way to select rows from a database and view them in a result set. The java.sql.ResultSet interface represents the result set of a database query.

A ``ResultSet`` in ``JDBC (Java Database Connectivity)`` is an interface provided by the Java standard library that represents the result of a database query. It allows you to retrieve and manipulate the data returned by a database query. A ``ResultSet`` typically represents a tabular data structure with rows and columns, similar to the result set produced by an SQL SELECT query.

A ``ResultSet`` object maintains a cursor that points to the current row in the result set. The term "result set" refers to the row and column data contained in a ``ResultSet`` object.

**Commonly used methods of ResultSet interfaces:**

* ``public boolean next()``:is used to move the cursor to the one row next from the current position.
* ``public boolean previous()``:is used to move the cursor to the one row previous from the current position.
* ``public boolean first()``:is used to move the cursor to the first row in result set object.
* ``public boolean last()``:is used to move the cursor to the last row in result set object.
* ``public boolean absolute(int row)``: is used to move the cursor to the specified row number in the ``ResultSet`` object.
* ``public boolean relative(int row)``: is used to move the cursor to the relative row number in the ``ResultSet`` object, it may be positive or negative.
* ``public int getInt(int columnIndex)``: is used to return the data of specified column index of the current row as int.
* ``public int getInt(String columnName)``:is used to return the data of specified column name of the current row as int.
* ``public String getString(int columnIndex)``:is used to return the data of specified column index of the current row as String.
* ``public String getString(String columnName)``:is used to return the data of specified column name of the current row as String.


**Creating a ResultSet**

You create a ResultSet by executing a Statement or PreparedStatement, like this:

```Java
Statement statement = connection.createStatement();
ResultSet result = statement.executeQuery("SELECT * FROM people");
```

Or like this:

```Java
String sql = "SELECT * FROM people";
PreparedStatement statement = connection.prepareStatement(sql);
ResultSet result = statement.executeQuery();
```

Example Program:

```Java
import java.sql.*;
import java.sql.SQLException;

public class Select {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost/school";
        String user = "root";
        String password = "";
        try
        {
            Connection conn = DriverManager.getConnection(url,user,password);
            Statement s = conn.createStatement();
            String query = "SELECT * FROM student";
            ResultSet r = s.executeQuery(query);
            while(r.next()){
                //Display values
                System.out.print(" ID : " + r.getInt("StudentID"));
                System.out.print(" First Name: " + r.getString("FirstName"));
                System.out.print(" Last Name: " + r.getString("LastName"));
                System.out.print(" Roll Number: " + r.getInt("RollNo"));
                System.out.println(" City : " + r.getString("City"));
            }
        } catch (SQLException e) {
            System.out.println(e);
        }
    }
}
```

Output:

```
ID : 1 First Name: Prashant Last Name: Bhandari Roll Number: 39 City : Birtamode
```

### **Scrollable ResultSet**

In ``JDBC (Java Database Connectivity)``, a scrollable ``ResultSet`` allows you to navigate through the result set in both forward and backward directions. This is particularly useful when you need to move back and forth within the result set to retrieve or update data. To create a scrollable ``ResultSet``, you typically set the appropriate parameters when creating a Statement or PreparedStatement object.

Here's how you can create and use a scrollable ResultSet in JDBC:

#### Create a Scrollable ``Statement``:
To create a scrollable ``ResultSet``, you need to specify the ``ResultSet.TYPE_SCROLL_INSENSITIVE`` or ``ResultSet.TYPE_SCROLL_SENSITIVE`` type when creating your ``Statement`` or ``PreparedStatement``.

- ``ResultSet.TYPE_SCROLL_INSENSITIVE``: allows you to scroll through the result set, and changes in the database are not reflected in the ``ResultSet``.
- ``ResultSet.TYPE_SCROLL_SENSITIVE``: creates a scrollable ``ResultSet`` that reflects changes made in the database while the ResultSet is still open.

Example for creating a scrollable ``Statement``:

```Java
Statement statement = connection.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_READ_ONLY);
```
Example for creating a scrollable ``PreparedStatement``:

```Java
String sql = "SELECT * FROM mytable";
PreparedStatement preparedStatement = connection.prepareStatement(sql, ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_READ_ONLY);
```

#### Execute the Query:
After creating a scrollable ``Statement`` or ``PreparedStatement``, execute your SQL query as usual.

```Java
ResultSet resultSet = statement.executeQuery("SELECT * FROM mytable");
```
#### Navigate the Scrollable ResultSet:
Once you have a scrollable ``ResultSet``, you can use various methods to navigate it.

```Java
resultSet.beforeFirst(); // Move the cursor before the first row
while (resultSet.next()) {
    // Process each row of data
}
```
#### Retrieve Data:
Use the appropriate methods to retrieve data from the ``ResultSet`` based on your query.

```Java
int id = resultSet.getInt("id");
String name = resultSet.getString("name");
```

### **Upgradeable ResultSet**
An updatable or upgradeable ``ResultSet`` in ``JDBC`` allows you to not only retrieve data from a database but also update, insert, or delete data directly through the ``ResultSet`` and have those changes reflected in the underlying database. In other words, you can use an updatable ``ResultSet`` to perform data modification operations on the database while iterating through the result set. However, not all databases or result sets support updatable ``ResultSet`` functionality.

#### Create a Scrollable and Updatable ``Statement``:

To create an updatable ``ResultSet``, you need to specify both ``ResultSet.TYPE_SCROLL_INSENSITIVE`` or ``ResultSet.TYPE_SCROLL_SENSITIVE`` and ``ResultSet.CONCUR_UPDATABLE`` when creating your ``Statement`` or ``PreparedStatement``.

- ``ResultSet.TYPE_SCROLL_INSENSITIVE`` or ``ResultSet.TYPE_SCROLL_SENSITIVE`` allows for scrolling through the result set.
- ``ResultSet.CONCUR_UPDATABLE`` enables the ResultSet to be updatable.

Example for creating an updatable ``Statement``:

```Java
Statement statement = connection.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_UPDATABLE);
```

Example for creating an updatable ``PreparedStatement``:

```Java
String sql = "SELECT * FROM mytable";
PreparedStatement preparedStatement = connection.prepareStatement(sql, ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_UPDATABLE);
```

#### Execute the Query:
After creating an updatable ``Statement`` or ``PreparedStatement``, execute your SQL query as usual.

```Java
ResultSet resultSet = statement.executeQuery("SELECT * FROM mytable");
```

#### Perform Updates:
Once you have an updatable ``ResultSet``, you can use its methods to modify data in the result set.

```Java
resultSet.absolute(2); // Move to the second row
resultSet.updateString("name", "Prashant"); // Update the "name" column
resultSet.updateRow(); // Commit the update to the database
```

#### Commit Changes:
To make changes permanent in the database, you need to explicitly call the **``updateRow()``** method or ``insertRow()`` method or ``deleteRow()`` . Afterward, commit the transaction using the database connection's **``commit()``** method.

```Java
resultSet.updateRow(); // Commit an update
connection.commit(); // Commit the transaction
```

## RowSet
----------
A ``RowSet`` in Java is a ``JavaBeans`` component that encapsulates a ``ResultSet`` and provides an easier and more flexible way to work with tabular data from a database. ``RowSet`` implementations, such as ``CachedRowSet``, ``JdbcRowSet``, and ``WebRowSet``, are part of the Java Standard Edition (Java SE) platform and provide a higher-level abstraction compared to a raw ``ResultSet``. ``RowSet`` objects are serializable, disconnected from the database, and can be used to perform tasks like browsing, updating, and persisting data.

``RowSet``s are classified into five categories based on how they are implemented which are listed namely as below:

- ``JdbcRowSet``
- ``CachedRowSet``
- ``WebRowSet``
- ``FilteredRowSet``
- ``JoinRowSet``

#### ``JdbcRowSet``
``JdbcRowSet`` is a connected RowSet that maintains an active connection to the database.

**Key methods:**

- **``setUsername()``** and **``setPassword()``**: Sets the username and password for the database connection.
- **``execute()``**: Executes a query and populates the ``JdbcRowSet``.

```Java
// Java Program to Illustrate RowSet in JDBC
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;
import javax.sql.RowSetEvent;
import javax.sql.RowSetListener;
import javax.sql.rowset.JdbcRowSet;
import javax.sql.rowset.RowSetProvider;

class Program {
    public static void main(String args[]){
        try {
            Class.forName("oracle.jdbc.driver.OracleDriver");
            JdbcRowSetrowSet = RowSetProvider.newFactory().createJdbcRowSet();
            rowSet.setUrl("jdbc:mysql://localhost/mydb");
            rowSet.setUsername("root");
            rowSet.setPassword("");
            rowSet.setCommand("select * from Student");
            rowSet.execute();
            while (rowSet.next()) {
                System.out.println("RollNo: " + rowSet.getInt(1));
                System.out.println("Name: " + rowSet.getString(2));
                System.out.println("Marks: " + rowSet.getString(3));
            }
        }
        catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```