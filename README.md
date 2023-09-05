# NOTES

- varchar(15) means 15 character limit for string type
- DATABASE -> TABLE -> COLUMNS
- Best practice to use single quote ('') for 'strings' 
  - Escape is \ like python - so 'Ben\\'s Icecream'


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
USE DATABASE <database>;
```

To show all databases:

```sql
SHOW DATABASES;
```

To drop a database:

```sql
DROP DATABASE <database>;
```

## Tables

Show tables in a database:

```sql
SHOW TABLES;
```

To drop a table:

```sql
DROP TABLE <table>; 
```

Add entry to table:

```sql
INSERT INTO <table> (<column1>, <column2>)

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
SHOW COLUMNS FROM <database>;  
```

OR

```sql
desc <table>
```

## SELECT Statements 

Select everything from a table:

```sql
SELECT * FROM <table>;
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
CREATE TABLE <table> (    
	table_id INT AUTO_INCREMENT PRIMARY KEY,    
	name VARCHAR(100) NOT NULL,    
	age INT NOT NULL);
```

## CRUD (Create, Read, Update, Delete)
