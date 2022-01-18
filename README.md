# DBMS-Information
DBMS Interview Questions
# PRIMARY KEY Constraint
The PRIMARY KEY constraint uniquely identifies each record in a table. Primary keys must contain UNIQUE values, and cannot contain NULL values. A table can have only ONE primary key; and in the table, this primary key can consist of single or multiple columns.
# UNIQUE Constraint
Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns.A PRIMARY KEY constraint automatically has a UNIQUE constraint.
However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table. Primary key cannot have NULL value, the unique constraints can have only one NULL value. The primary key creates the cluster index automatically but the Unique key does not.
# FOREIGN KEY Constraint
The FOREIGN KEY constraint prevents invalid data from being inserted into the foreign key column, because it has to be one of the values contained in the parent table.
A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.

That is, this field points to primary key of another table. This usually creates a kind of link between the two tables.
# Candidate Key
Candidate keys are those attributes that uniquely identify rows of a table. The Primary Key of a table is selected from one of the candidate keys. So, candidate keys have the same properties as the primary keys explained above. There can be more than one candidate keys in a table.

# Alternate Key
As stated above, a table can have multiple choices for a primary key; however, it can choose only one. So, all the keys which did not become the primary Key are called alternate keys.

# Composite Key
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

# ACID Properties
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
  
     Isolation ensures that concurrent execution of transactions leaves the database in the same state that would have been obtained if the transactions were executed   sequentially.Every transaction is individual, and One transaction can’t access the result of other transactions until the transaction completed.  It's example discussed above in consistency.
