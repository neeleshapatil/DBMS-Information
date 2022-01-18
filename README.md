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
