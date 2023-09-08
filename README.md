# NOTES

- varchar(15) means 15 character limit for string type
- DATABASE -> TABLE -> COLUMNS
- Best practice to use single quote ('') for 'strings' 
  - Escape is \ like python - so 'Ben\\'s Icecream'
- source <filepath> works to run sql scripts


## Comments 

- Mainly useful in a workbench or editor
- Two dashes, "--", comments a line
- CTRL+ "/" comments blocks in workbench

# REFERENCE

## Database

To show what database you are working in:

```sql
SELECT DATABASE();
```

To change to a particular database:

```sql
USE DATABASE <A_database>;
```

To show all databases:

```sql
SHOW DATABASES;
```

To drop a database:

```sql
DROP DATABASE <A_database>;
```

## Tables

Show tables in a database:

```sql
SHOW TABLES;
```

To drop a table:

```sql
DROP TABLE <example_table>; 
```

Add entry to table:

```sql
INSERT INTO example_table (<column1>, <column2>)

	VALUES(<column1_VALUE>, <column2_VALUE>);			
```

You can also submit multiple INSERTs at once:

```sql
INSERT INTO people(first_name, last_name, age)
VALUES    
('Linda', 'Belcher', 45),    
('Phillip', 'Frond', 38),    
('Calvin', 'Fischoeder', 70);
```

## Columns

To view columns from database:

```sql
SHOW COLUMNS FROM <A_database>;  
```

OR

```sql
desc <example_table>
```

## SELECT Statements 

Select everything from a table:

```sql
SELECT * FROM <A_table>;
```

### WHERE (when using SELECT)

Narrow down rows, sort of a filter function:

```sql
SELECT * FROM men WHERE age = 4;
```

```sql
SELECT age FROM cats WHERE name ='Egg';
```

## NULL

A NULL value indicates an empty value

```sql
CREATE TABLE persons (    
	name VARCHAR(100) NOT NULL,    
	age INT NOT NULL
	);
```

## DEFAULT 

If you have a default value without a NOT NULL statement, you could update a value with NULL later. 

If both NOT NULL and DEFAULT, DEFAULT cannot be equal to NULL.

```sql
CREATE TABLE doggies (        
	name VARCHAR(20) NOT NULL DEFAULT 'unnamed',        
	age INT NOT NULL DEFAULT 99 );
```

## Primary Key

Each row has unique identifier like a serial number. Primary keys are unique. 

Primary key can never be NULL, redundant to specify as NOT NULL

Assign a column as the primary key:

```sql
CREATE TABLE unique_animal (	
	animal_id INT PRIMARY KEY,    
	name VARCHAR(100) NOT NULL,    
	age INT NOT NULL);
```

Using AUTO_INCREMENT will adjust each row by 1 without specification:

```sql
CREATE TABLE <A_table> (    
	table_id INT AUTO_INCREMENT PRIMARY KEY,    
	name VARCHAR(100) NOT NULL,    
	age INT NOT NULL);
```

## CRUD (Create, Read, Update, Delete)

### Alias 

Temporary name for a column:

```sql
SELECT data_id AS id,name FROM store;
```

### UPDATE, SET

UPDATE and SET commands go together

The following command would update every row VALUE in 'column_name' to 'Example String'. This may not be useful in most cases, and thus a WHERE statement is required:

```sql
UPDATE <A_table> SET column_name='Example String';
```

Updating multiple columns at once is possible. As above, this will affect all rows in 'column_name':

```sql
UPDATE <A_table> SET column_name='Example String',column_name2 ='Example String2';
```

A WHERE clause will allow us to filter row values:

```sql
UPDATE <A_table> SET age=14 WHERE name='Bennie';
```

**Best practice is to SELECT query what needs to be updated prior to making update:**

### DELETE

**Again, best practice to run SELECT clause to verify before deleting elements of tables**

Delete every row of the table without dropping the table itself:

```sql
DELETE FROM <A_table>;
```

## String Functions 

### CONCAT(x,y,z)

Combines text from arguments 

```sql
SELECT CONCAT(name, '-san') FROM japan;
```

Would append the name, 'Meri' becomes 'Meri-san'

Same could be achieved with CONCAT_WS( ), concatenate with separator:

```sql
SELECT CONCAT_WS('-', name, 'san') AS formalName FROM japan;
```

When using CONCAT_WS, the first argument, or "separator", will be added between each subsequent argument. 
