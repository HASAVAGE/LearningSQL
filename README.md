# NOTES

- varchar(15) means 15 character limit for string type
- DATABASE -> TABLE -> COLUMNS

## Comments 

- Mainly useful in a workbench or editor
- Two dashes, "--", comments a line
- CTRL+ "/" comments blocks in workbench

# REFERENCE

## Database

To show what database you are working in:

```
SELECT DATABASE();
```

To change to a particular database:

```
USE DATABASE <database>;
```

To show all databases:

```
SHOW DATABASES;
```

To drop a database:

```
DROP DATABASE <database>;
```

## Tables

Show tables in a database:

```
SHOW TABLES;
```

To drop a table:

```
DROP TABLE <table>; 
```

Add entry to table:

```
INSERT INTO <table> (<column1>, <column2>)

	VALUES(<column1_VALUE>, <column2_VALUE>);			
```

You can also submit multiple INSERTs at once:

```
INSERT INTO people(first_name, last_name, age)
VALUES    
('Linda', 'Belcher', 45),    
('Phillip', 'Frond', 38),    
('Calvin', 'Fischoeder', 70);
```

## Columns

To view columns from database:

```
SHOW COLUMNS FROM <database>;  
```

OR

```
desc <table>
```

## Select Statements 

Select everything from a table:

```
SELECT * FROM <table>;
```

## NULL

- A NULL value indicates an empty value
- 
