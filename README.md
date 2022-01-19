# DBMS-Information
DBMS Interview Questions
# 1) PRIMARY KEY Constraint
The PRIMARY KEY constraint uniquely identifies each record in a table. Primary keys must contain UNIQUE values, and cannot contain NULL values. A table can have only ONE primary key; and in the table, this primary key can consist of single or multiple columns.
# 2) UNIQUE Constraint
Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns.A PRIMARY KEY constraint automatically has a UNIQUE constraint.
However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table. Primary key cannot have NULL value, the unique constraints can have only one NULL value. The primary key creates the cluster index automatically but the Unique key does not.
# 3) FOREIGN KEY Constraint
The FOREIGN KEY constraint prevents invalid data from being inserted into the foreign key column, because it has to be one of the values contained in the parent table.
A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.

That is, this field points to primary key of another table. This usually creates a kind of link between the two tables.
# 4) Candidate Key
Candidate keys are those attributes that uniquely identify rows of a table. The Primary Key of a table is selected from one of the candidate keys. So, candidate keys have the same properties as the primary keys explained above. There can be more than one candidate keys in a table.

# 5) Alternate Key
As stated above, a table can have multiple choices for a primary key; however, it can choose only one. So, all the keys which did not become the primary Key are called alternate keys.

# 6) Composite Key
A key that has more than one attributes is known as composite key. The attributes in the set may not be unique when considered separately. However, when taken all together, they will ensure uniqueness.

#
|Emp_Id |	Emp_Number |	Emp_Name
|------ |----------  |    --------
| E01    | 2264          |Steve
|E22	|2278	        |Ajeet
|E23	|2288	        |Chaitanya
|E45	|2290	        |Robert

How many super keys the above table can have?
1. {Emp_Id}
2. {Emp_Number}
3. {Emp_Id, Emp_Number}
4. {Emp_Id, Emp_Name}
5. {Emp_Id, Emp_Number, Emp_Name}
6. {Emp_Number, Emp_Name}

Lets select the candidate keys from the above set of super keys.

1. {Emp_Id} – No redundant attributes
2. {Emp_Number} – No redundant attributes
3. {Emp_Id, Emp_Number} – Redundant attribute. Either of those attributes can be a minimal super key as both of these columns have unique values.
4. {Emp_Id, Emp_Name} – Redundant attribute Emp_Name.
5. {Emp_Id, Emp_Number, Emp_Name} – Redundant attributes. Emp_Id or Emp_Number alone are sufficient enough to uniquely identify a row of Employee table.
6. {Emp_Number, Emp_Name} – Redundant attribute Emp_Name.

The candidate keys we have selected are:
{Emp_Id}
{Emp_Number}

Note: A primary key is selected from the set of candidate keys. That means we can either have Emp_Id or Emp_Number as primary key. The decision is made by DBA (Database administrator)
# Record or Tuple
Each row of a table is known as record. It is also known as tuple. 

# 7) ACID Properties
To ensure the integrity of data during a transaction, the database system maintains the following properties
  - ## Atomicity
     if any operation is performed on the data, either it should be executed completely or should not be executed at all. It further means that the operation should not break in between or execute partially.
     
     Suppose Account A has a balance of 400$ & B has 700$. Account A is transferring 100$ to Account B. This is a transaction that has two operations a) Debiting 100$ from A’s balance b) Creating 100$ to B’s balance. Let’s say first operation passed successfully while second failed, in this case A’s balance would be 300$ while B would be having 700$ instead of 800$.Either the transaction should fail without executing any of the operation or it should process both the operations. The Atomicity property ensures that.
  - ## Consistency
    The database must be consistent before and after the transaction.
     - If the transaction completed successfully, then it will apply all the changes to the database.
     - If there is an error in a transaction, then all the changes that already made will be rolled back automatically. It means the database will restore to its state that it had before the transaction started.
    - If there is a system failure in the middle of the transaction, then also, all the changes made already will automatically rollback. 
    
    For example account A is having a balance of 400$ and it is transferring 100$ to account B & C both. So we have two transactions here. Let’s say these transactions run concurrently and both the transactions read 400$ balance, in that case the final balance of A would be 300$ instead of 200$. This is wrong. If the transaction were to run in isolation then the second transaction would have read the correct balance 300$ (before debiting 100$) once the first transaction went successful.
 - ## Isolation
   The term 'isolation' means separation. Multiple transactions occur independently without interference. 
  
     Isolation ensures that concurrent execution of multiple transactions leaves the database in the same state that would have been obtained if the transactions were executed   sequentially.
     
     Every transaction is individual, and One transaction can’t access the result of other transactions until the transaction completed.  It's example discussed above in consistency.
 - ## Durability
   Durability guarantees that once a transaction has been committed, it will remain committed even in the case of a system failure which actually means recording the completed   transactions (or their effects) in non-volatile memory.
# 8) Normalization of Database
Normalization is a systematic approach of decomposing tables to eliminate data redundancy(repetition) and undesirable characteristics like Insertion, Update and Deletion Anomalies. It reduce the amount of space a database consumes.
    Normalization is used for mainly two purposes,
     
     - Eliminating redundant(useless) data.
     - Ensuring data dependencies make sense i.e data is logically stored.
 # 9) 1st Normal form 
 
  |Emp_Id |	Emp Name |	Phone Number | Salary
  |------ |----------|   ------      | ----
  | E01    | Alex    | +1 20155,  +1 20144     | 60,000
  | E02   | Barry |  +1 20166     | 48000
  | E03   | Clair | +1 20177 |22,000
  
  Single cell can not hold multiple values - Atomocity
  
  Table in 1st Normal form
   |Emp_Id |	Emp Name |	Phone Number | Salary
  |------ |----------|   ------      | ----
  | E01    | Alex    | +1 20155    | 60000
  | E01    | Alex   |+1 20144|60000
  | E02   | Barry |  +1 20166     | 48000
  | E03   | Clair | +1 20177 |22,000

A database is in first normal form if it satisfies the following conditions:

   - Contains only atomic values -
       An atomic value is a value that cannot be divided. For example, in the table shown above, phone number column holds multiple values. It should only have single(atomic) valued attributes/columns
   - There are no repeating groups -
A repeating group means that a table contains two or more columns that are closely related. For example, a table that records data on a book and its author(s) with the following columns: [Book ID], [Author 1], [Author 2], [Author 3] is not in 1NF because [Author 1], [Author 2], and [Author 3] are all repeating the same attribute.

# 10) Second Normal Form

For a table to be in the Second Normal form

 - It is in first normal form
 - All non-key attributes are fully functional dependent on the primary key. Their is no Partial Dependency.
    
    Partial Dependency exists, when for a composite primary key, any non- key attribute in the table depends only on a part of the primary key and not on the complete primary key. To remove Partial dependency, we can divide the table, remove the attribute which is causing partial dependency, and move it to some other table.
    
# 11) Third Normal form

When a table is in the Second Normal Form and has no transitive dependency, then it is in the Third Normal Form.

By its nature, a transitive dependency requires three or more attributes that have a functional dependency between them, meaning that column A is functionally dependent on column B, and column B is functionally dependent on column C. In this case, C is transitively dependent on A via B.

| Author_ID	| Author	| Book	| Author_Nationality
 |------ |----------|   ------ | ----
|Auth_001	|Orson Scott | Card	Ender's Game	| United States
| Auth_001	| Orson Scott | Card	Children of the Mind	| United States
|Auth_002	|Margaret Atwood	|The Handmaid's Tale |	Canada


In the AUTHORS example above:

- Book → Author: Here, the Book attribute determines the Author attribute. If you know the book name, you can learn the author's name. However, Author doesn't determine Book, because an author can write multiple books. For example, just because we know the author's name is Orson Scott Card, we still don't know the book name.

- Author → Author_Nationality: Likewise, the Author attribute determines the Author_Nationality, but not the other way around—just because we know the author's nationality doesn't mean we can determine the author.

But this table introduces a transitive dependency:

- Book →Author_Nationality: If we know the book name, we can determine the author's nationality via the Author column.

The advantage of removing transitive dependency is,

   - Amount of data duplication is reduced.
   - Data integrity achieved

# 12) Why Transitive Dependencies Are Bad Database Design
What is the value of avoiding transitive dependencies to help ensure 3NF? Let's consider our first table again and see the issues it creates:

AUTHORS

|Author_ID	|Author	|Book	|Author_Nationality
|------ |----------|   ------ | ----
|Auth_001	|Orson Scott Card|	Ender's Game|	United States
|Auth_001	|Orson Scott Card	|Children of the Mind|	United States
|Auth_002|	Margaret Atwood|	The Handmaid's Tale|	Canada

This kind of design can contribute to data anomalies and inconsistencies, for example:

- If you deleted the two books Children of the Mind and Ender's Game, you would delete the author "Orson Scott Card" and his nationality completely from the database.
- You cannot add a new author to the database unless you also add a book. What if the author is yet unpublished or you don't know the name of a book they authored?
- If "Orson Scott Card" changed his citizenship, you would have to change his citizenship in all records in which he appears. Having multiple records with the same author can result in inaccurate data. What if the data entry person doesn't realize there are multiple records for someone, and changes the data in only one record?
- You can't delete a book such as The Handmaid's Tale without also completely deleting the author.

# 13) Boyce Codd normal form (BCNF) or 3.5NF
To understand more, few concepts need to be discussed, such as keys and attributes.

Attributes: Attributes that are a part of the candidate key are called prime attributes, and the rest of the attributes are known as Non-prime attributes.

Super Key: This is the combination of columns that will uniquely identify the rows in a table. A candidate key is selected from the given super keys based on the minimum number of attributes. And the primary key is one among the candidate keys.

It should satisfy the following two conditions:
 - It should be in the Third Normal Form.
 - And, for any dependency A → B (read as “A determines B”), A should be a super key.
The second point means, that for a dependency A → B, A cannot be a non-prime attribute, if B is a prime attribute.

Relation:
Person(SSN, Name, BirthMonth, ZodiacSign)

SSN->Name, BirthMonth

BirthMonth->ZodiacSign

 - A person has a social security number (SSN) which determines their name and birth month. A person’s birth month determines their zodiac sign.
- The original Person relation is not in BCNF because BirthMonth from the functional dependency BirthMonth->ZodiacSign is not a super key
- 
We need to decompose orginal relation

R1(BirthMonth, ZodiacSign) where BirthMonth->ZodiacSign
R2(SSN, Name, BirthMonth) where SSN->Name,BirthMonth

In this decomposition, BirthMonth is a super key in R1 and SSN is a super key in R2, so R1 and R2 are a BCNF decomposition of Person.

# 14) DDL – Data Definition Language

DDL is a set of SQL commands used to create, modify, and delete database structures but not data. CREATE, DROP, ALTER, RENAME, TRUNCATE

CREATE: This command is used to create the database or its objects (like table, index, function, views, store procedure, and triggers).
```
CREATE TABLE customers
( customer_id number(10) NOT NULL,
  customer_name varchar2(50) NOT NULL,
  city varchar2(50)
);
```
DROP: This command is used to delete objects from the database. Issue a PURGE so that the space associated with the customers table is released
```
DROP TABLE customers PURGE;
```
ALTER: This is used to alter the structure of the database.
```
ALTER TABLE Customers
ADD Email varchar(255);
```
```
ALTER TABLE Customers
DROP COLUMN Email
```
Modify existing column
```
ALTER TABLE customers
MODIFY customer_name varchar2(100) NOT NULL
```

RENAME: This is used to rename an object existing in the database. You can rename table name or column name etc.

```
ALTER TABLE customers
RENAME COLUMN customer_name TO cname
```
```
ALTER TABLE customers
RENAME TO contacts
```
TRUNCATE: It is used to delete all the rows of a relation (table) in one go. With the help of the “TRUNCATE” command, we can’t delete the single row as here WHERE clause is not used. By using this command the existence of all the rows of the table is lost. It is comparatively faster than the delete command as it deletes all the rows fastly. Here we can’t restore the tuples of the table by using the “ROLLBACK” command.

COMMENT: This is used to add comments to the data dictionary.
# 15) DML(Data Manipulation Language)

The SQL commands that deals with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. 

List of DML commands: INSERT, UPDATE  , DELETE , LOCK etc.

INSERT : It is used to insert data into a table.
```
INSERT INTO suppliers
(supplier_id, supplier_name)
VALUES
(5000, 'Apple');
```
Insert using select
```
INSERT INTO suppliers
(supplier_id, supplier_name)
SELECT account_no, name
FROM customers
WHERE customer_id > 5000
```
How do I make sure that I do not enter the same client information again while inserting new records to table Clients
```
INSERT INTO clients
(client_id, client_name, client_type)
SELECT supplier_id, supplier_name, 'advertising'
FROM suppliers
WHERE NOT EXISTS (SELECT *
                  FROM clients
                  WHERE clients.client_id = suppliers.supplier_id);
```
UPDATE: It is used to update existing data within a table.

This Oracle UPDATE statement example would update the state to 'California' and the customer_rep to 32 where the customer_id is greater than 100
```
UPDATE customers
SET state = 'California',
customer_rep = 32
WHERE customer_id > 100
```


Based on the suppliers and customers table , update the city in the suppliers table with the city in the customers table when the supplier_name in the suppliers table matches the customer_name in the customers table

```
UPDATE suppliers
SET city = (SELECT customers.city
            FROM customers
            WHERE customers.customer_name = suppliers.supplier_name)
WHERE EXISTS (SELECT customers.city
              FROM customers
              WHERE customers.customer_name = suppliers.supplier_name);
```
DELETE : It is used to delete records from a database table.
```
DELETE FROM customers
WHERE last_name = 'Smith';
```
LOCK: Table control concurrency.

# 15) DCL - Data Control Language. 
SQL queries like GRANT and REVOKE come under this.

# 16) TCL (Transaction Control Language) :
Transaction Control Language commands are used to manage transactions in the database.
```
COMMIT: Commit command is used to permanently save any transaction into the database.

ROLLBACK: This command restores the database to last committed state.
It is also used with savepoint command to jump to a savepoint in a transaction.

SAVEPOINT: Savepoint command is used to temporarily save a transaction so that 
you can rollback to that point whenever necessary.
```
# 17) DELETE VS TRUNCATE
| DELETE | TRUNCATE
| -----   |  -------
| DML(Data Manipulation Language) command |DDL(Data Definition Language) command
|DELETE command is used to delete specified rows(one or more) | It is used to delete all the rows from a table
|You can give WHERE clause in the DELETE command | There is no WHERE clause in the TRUNCATE command.
| Slower | Faster
| DELETE is a DML Command so it can be rolled back |TRUNCATE TABLE statement is a DDL command so it can not be rolled back.

# 18) What is the difference between DROP and TRUNCATE?

TRUNCATE removes all rows from the table which cannot be retrieved back, DROP removes the entire table from the database and it cannot be retrieved back. Both are DDL Commands
