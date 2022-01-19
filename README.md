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
  
     Isolation ensures that concurrent execution of multiple transactions leaves the database in the same state that would have been obtained if the transactions were executed   sequentially.Every transaction is individual, and One transaction can’t access the result of other transactions until the transaction completed.  It's example discussed above in consistency.
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

# 10) First Normal Form

For a table to be in the Second Normal form

 - It is in first normal form
 - All non-key attributes are fully functional dependent on the primary key
    
    Partial Dependency exists, when for a composite primary key, any non- key attribute in the table depends only on a part of the primary key and not on the complete primary key. To remove Partial dependency, we can divide the table, remove the attribute which is causing partial dependency, and move it to some other table.
