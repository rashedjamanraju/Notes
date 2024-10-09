# 🚀 PostgreSQL on Windows

## 1. **Run PostgreSQL** 🖥️
To start using PostgreSQL, open your terminal and enter the following command:
```shell
psql -U username
```
The default username is **postgres**. 
![alt text](image-8.png)
After entering your password, press enter.

---

## 2. **Clear the Terminal** 🧹
To clear the terminal screen, use:
```shell
\! cls;
```
![alt text](image-11.png)

---

## 3. **Check Existing Databases** 📊
You can check existing databases using the terminal with the following commands:
- **Way 1**:
    ```shell
    \l; 
    ```
    ![alt text](image-15.png)
- **Way 2**:
    ```shell
    \list; 
    ```
- **Way 3**:
    ```shell
    SELECT datname FROM pg_database; 
    ```



### Using pgAdmin 4:
1. Select **postgres**.
   ![alt text](image.png)
2. Click on **query tools**.
   ![alt text](image-2.png)
3. Execute:
   ```sql
   SELECT datname FROM pg_database;
   ```
   ![alt text](image-16.png)

---

## 4. **Create a New Database** ➕
To create a new database, use:
```sql
CREATE DATABASE name;
```
**Example:**
```sql
CREATE DATABASE persondb;
```
![alt text](image-17.png)

---

## 5. **Switch to Another Database** 🔄
To switch to a different database, use:
```sql
\c name;
```
**Example:**
```sql
\c persondb;
```
- Before switching, the selected database is postgres:
  ![alt text](image-4.png)
- After executing `\c persondb;`, you are now on another database:
  ![alt text](image-19.png)

---

## 6. **Delete an Existing Database** ❌
To delete a database, use:
```sql
DROP DATABASE name;
```
**Example:**
```sql
DROP DATABASE ustc;
```
If you encounter an error:
![alt text](image-22.png)

- Go to pgAdmin 4 and disconnect the 'ustc' database:
  ![alt text](image-23.png)
- Then execute the command again in the terminal:
![alt text](image-24.png)

---

## 🗃️ Working with Tables

### 7. **Create a Table** 🛠️
First we need to switch to our desire database then we will create table
![alt text](image-25.png)
To create a table, use:
```sql
CREATE TABLE person(
    id INT, 
    name VARCHAR(100), 
    city VARCHAR(100)
);
```
here, **VARCHAR(100)** means, name and city field can contain maximum 100 characters.
![alt text](image-26.png)

---

### 8. **Verify Table Creation** ✅
In the terminal (Only):
```sql
\d person;
```
![alt text](image-27.png)

In **pgAdmin 4**:
```sql
SELECT * FROM information_schema.columns WHERE table_name = 'person';
```
![alt text](image-28.png)

---

### 9. **Insert Single Person's Data** 👤
- **Way 1**:
    ```sql
    INSERT INTO person(id, name, city)
    VALUES (101, 'Raju', 'CTG');
    ```
- **Way 2**:
    ```sql
    INSERT INTO person 
    VALUES (101, 'raju', 'CTG');
    ```

---

### 10. **Insert Multiple Persons' Data** 👥
- **Way 1**:
    ```sql
    INSERT INTO person(id, name, city)
    VALUES 
        (102, 'Jaman', 'CTG'), 
        (103, 'Rashed', 'CTG');
    ```
- **Way 2**:
    ```sql
    INSERT INTO person 
    VALUES 
        (102, 'Jaman', 'CTG'), 
        (103, 'Rashed', 'CTG');
    ```

---

### 11. **Read Data from the Person Table** 📖
- To read all columns:
    ```sql
    SELECT * FROM person;
    ```
- To read specific columns:
    ```sql
    SELECT name FROM person;
    ```
- For multiple specific columns:
    ```sql
    SELECT name, city FROM person;
    ```
- For specific id containing row:
    ```sql
    SELECT * FROM person WHERE id=102;
    ```
    ```sql
    SELECT name,city FROM person WHERE id=102;
    ```

---

### 12. **Update Data of a Specific Person** ✏️
To update a person's city:
```sql
UPDATE person
SET city = 'KHULNA'
WHERE id = 101;
```

---

### 13. **Delete a Person's Row** 🗑️
To delete a row:
```sql
DELETE FROM person
WHERE id = 102;
```

---

### 14. **Data Types in PostgreSQL** 📊
**Numeric Types:**
- `INT`
- `DOUBLE PRECISION`
- `FLOAT`
- `DECIMAL`
- `SERIAL`

**String Type:**
- `VARCHAR(limit)`

**Date Type:**
- `DATE`

**Boolean Type:**
- `BOOLEAN`

---

### 15. **Constraints** ⚖️
Common constraints include:
1. **PRIMARY KEY**
2. **NOT NULL**
3. **UNIQUE**
4. **DEFAULT VALUE**
5. **CURRENT_DATE**

---

### **Use of Constraints**
Creating a table with various constraints:
```sql
CREATE TABLE employees(
    emp_id SERIAL PRIMARY KEY,
    fname VARCHAR(10) NOT NULL,
    lname VARCHAR(10) NOT NULL,
    email VARCHAR(25) NOT NULL UNIQUE,
    dept VARCHAR(9),
    salary DECIMAL(10,2) DEFAULT 30000.00,
    hire_date DATE DEFAULT CURRENT_DATE
);
```

---

