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

### SUBSTRING / SUBSTR()

Selects only a portion of an existing string. Examples below:

```sql
SELECT SUBSTRING('HELLO WORLD', 2, 7);
```

Returns "ELLO W"

Argument 2 is starts at 2nd character, and 3rd argument defines length of the string.

```sql
SELECT SUBSTRING('HELLO WORLD', 7);
```

Only passing one integer argument returns "WORLD", SUBSTRING takes seventh character to end of string. 

Passing a negative number in the above case will start at the end of string and go forward to the end. The following command could be useful to determine the last character in any string:

```SQL
SELECT SUBSTRING('STRING', -1);
```

Returns 'G'

```sql
SELECT CONCAT(SUBSTR(title,1,10), '...') AS short_title FROM movies;
```

Above code passes a 10 char abbreviation of movie title to CONCAT, which adds '...' to each abbreviation.  

### REPLACE

REPLACE(str, from_str, to_str), fairly simple arguments.

### REVERSE

As stated, simply reverses a string ... 'Guard dog' becomes 'god drauG'

### CHAR_LENGTH

Pretty much a len function

Returns length of string. Not to be confused with LENGTH(), which returns length in **bytes**

### UPPER / LOWER

Case changing functions

Can also call upper as UCASE, and lower as LCASE

### INSERT

INSERT(str,pos,len,newstr)

Returns the string str, with the substring beginning at position pos and len characters long replaced by the string newstr. pos and len are int. len is number of characters to replace and pos is where to add newstr. Returns NULL if any argument is NULL. 

```sql
SELECT INSERT('Hello Bobby', 6, 6, 'There');
> 'HelloThere'
```

Add string to another string 

### RIGHT / LEFT

```sql
SELECT LEFT('Kaley', 1);
> 'K'
```

### REPEAT

Duplicates a string by some int number of times

```sql
SELECT REPEAT('ha', 4);
> 'hahahaha'
```

### TRIM

```sql
SELECT TRIM('  pickle  ');
> 'pickle'
```

Cleans up first and last extra spaces, but not those in the middle. 

Good for cleaning data 

If a character other than ' ' needs to be trimmed, you can specify which with LEADING or TRAILING / FROM 

## REFINING QUERIES

### DISTINCT 

Basically a unique function. 

If you need a combination of columns to both be DISTINCT, add both to SELECT query after DISTINCT:

```sql
SELECT DISTINCT author_fname, author_lname FROM books;
```

### ORDER BY

Put this after the FROM statement in a query. 

ASC (default) or DESC set order direction. 

```sql
SELECT * FROM movies
ORDER BY released_year DESC;
```

