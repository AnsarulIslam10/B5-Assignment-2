# Bonus Section (Answer Any 5 Questions on readme.md in Bangla) → 10 Marks

## 1. What is PostgreSQL?
PostgreSQL also known as postgres is a powerfull open source object relational database system with over 35 years of active development. It was originally developed at the University of California, Berkeley in the 1980s, PostgreSQL has evolved into one of the most sophisticated database systems available today.
PostgreSQL supports both SQL and JSON querying. 
PostgreSQL is used as a primary database for many web applications as well as mobile analysis applications.
PostgreSQL is simple and easy to learn. and it's completely free unlike some other databases that cost thousands of dollars, postgreSQL is 100% free. Anyone can download and use it for their projects.

## 2. What is the purpose of a database schema in PostgreSQL?
In PostgreSQL, a schema is a way to organize objects like tables, views, functions, constraints, indexes, data types into groups. It helps with better management and organization of the database. </br>
A single database can have more then one schema. but a schema only belongs to one database. </br>
Here are some purposes of schemas:
- **Organization and structure**: Helps logically group related objects.
- **Security and Access Control**: Permissions can be managed at the schema level.
- **Avoiding Name Conflicts**: Different schemas can have tables or functions with the same name without conflict.
- **Easier Maintenance**: Makes it simpler to manage and maintain large databases.

## 3. Explain the Primary Key and Foreign Key concepts in PostgreSQL.
**Primary Key**: A Primary Key is a unique identifier for each record in a table. It's like an ID card for each row in a table.
- it's unuquely identifies every record
- it must be unique.
- it can't be empty.
    ```
    CREATE TABLE users (
        user_id SERIAL PRIMARY KEY,
        name VARCHAR(100)
    );
    ```
Here, `user_id` is the primary key. </br></br>
**Foreign Key**: A Foreign Key is the primary key of another table. for example:
```
CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  user_id INT REFERENCES users(user_id),
  order_date DATE
);
```
In this example:
- `order_id` is the Primary Key of `orders` table. 
- `user_id` is the Foreign Key of `orders` table. 
- `user_id` refers to the Primary Key of `users` table.

So when we use the `user_id` from the `users` table in the `orders` table, it becomes a foreign key because it creates relationship between the two tables.

## 4. What is the difference between the VARCHAR and CHAR data types?
The main difference between the `VARCHAR` and `CHAR` is that `CHAR` has fixed size but `VARCHAR` has variable size.</br>
`CHAR`:
- Fixed lenght string.
- No size indicator.
- Static memory.
- Programmer can use `CHAR` when the sizes of the column data entries are consistent. </br>

`VARCHAR`:
- Variable length charecter.
- Variable memory.
- Dynamic memory.
- Programmer can use `VARCHAR` when the sizes of the column data entries change considerably.

## 5. Explain the purpose of the WHERE clause in a SELECT statement.
The purpose of `WHERE` clause in a `SELECT` statement is to filter rows from a table based on a specific condition. it ensures that only the rows that matches the condition are returned in the query result.
for example:-
```
<!-- students -->
+----+--------+-----+
| id | name   | age |
+----+--------+-----+
| 1  | Naruto | 16  |
| 2  | Ichigo | 19  |
| 3  | Luffy  | 14  |
| 4  | Goku   | 28  |
| 5  | Eren   | 18  |
+----+--------+-----+
```
Now if we want to see the data of students who are older then `18` then we can do it by using the `WHERE` clause in the `SELECT` statement. like this:-
```
SELECT * FROM students WHERE age >= 18;
```
**Output:**
```
+----+--------+-----+
| id | name   | age |
+----+--------+-----+
| 2  | Ichigo | 19  |
| 4  | Goku   | 28  |
| 5  | Eren   | 18  |
+----+--------+-----+
```
The `WHERE age >= 18` part filters out Naruto and Luffy because they are under 18.