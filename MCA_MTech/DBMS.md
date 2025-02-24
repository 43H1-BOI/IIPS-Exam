# **DBMS Questiion Paper Solution**

### **Q1: Differentiate Between Weak and Strong Entity Type**

| **Feature**        | **Weak Entity**                                                 | **Strong Entity**                                 |
| ------------------ | --------------------------------------------------------------- | ------------------------------------------------- |
| **Dependency**     | Depends on a strong entity for identification.                  | Exists independently and does not rely on others. |
| **Primary Key**    | Lacks a complete primary key; uses a foreign key + partial key. | Has a unique primary key.                         |
| **Representation** | Represented with a double rectangle in ER diagrams.             | Represented with a single rectangle.              |
| **Example**        | `Dependent` (relies on `Employee`)                              | `Employee` entity                                 |

---

### **Q2: What is a Multivalued Attribute? Give Example.**

- **Definition:** A multivalued attribute is one that can have multiple values for a single entity instance.
- **Example:**
  - Entity: `Student`
  - Multivalued Attribute: `Phone_Numbers` (A student can have multiple phone numbers like 1234567890 and 9876543210).

---

### **Q3: State Any 5 Properties of Relation**

1. **Rows Uniqueness (Tuples):**  
   No two rows in a relation can have identical values for all attributes.

2. **Atomicity of Attributes:**  
   Each attribute must hold atomic (indivisible) values; no composite or multivalued attributes allowed.

3. **Order Irrelevance:**  
   The order of rows and columns in a relation does not affect its data or meaning.

4. **Attribute Uniqueness:**  
   Each attribute must have a unique name within a relation.

5. **Domain Constraint:**  
   The values of each attribute must belong to a defined domain (e.g., integers, dates).

---

### **Q4: Explain Stored and Derived Attribute with Examples**

1. **Stored Attribute:**

   - **Definition:** An attribute physically stored in the database.
   - **Example:** `Date_Of_Birth` in a `Person` entity is a stored attribute.

2. **Derived Attribute:**
   - **Definition:** An attribute that can be derived from stored attributes but is not physically stored in the database.
   - **Example:** `Age` can be derived from `Date_Of_Birth` and the current date.

---

### **Q5: Explain Any 5 Aggregate Functions**

1. **SUM():**

   - Calculates the sum of a numeric column.
   - **Example:** `SELECT SUM(Salary) FROM Employees;`

2. **AVG():**

   - Computes the average of a numeric column.
   - **Example:** `SELECT AVG(Marks) FROM Students;`

3. **COUNT():**

   - Returns the number of rows that match a condition.
   - **Example:** `SELECT COUNT(*) FROM Orders;`

4. **MIN():**

   - Finds the smallest value in a column.
   - **Example:** `SELECT MIN(Salary) FROM Employees;`

5. **MAX():**
   - Finds the largest value in a column.
   - **Example:** `SELECT MAX(Salary) FROM Employees;`

---

### **Q6: Write Any 5 Disadvantages of DBMS**

1. **Cost:**

   - High initial and operational cost for hardware, software, and skilled personnel.

2. **Complexity:**

   - DBMS systems are complex to design, implement, and maintain.

3. **Performance Issues:**

   - For small datasets or simple tasks, DBMS may be slower than traditional file systems.

4. **Security Risks:**

   - Centralized storage increases vulnerability to data breaches and unauthorized access.

5. **Overhead:**
   - Requires additional resources (e.g., memory and processing power) to manage databases efficiently.

---

### **Q7: Write Any 5 DDL Commands**

1. **CREATE:**

   - Used to create database objects like tables, views, or schemas.
   - **Example:** `CREATE TABLE Students (ID INT, Name VARCHAR(50));`

2. **ALTER:**

   - Modifies the structure of existing database objects.
   - **Example:** `ALTER TABLE Students ADD Age INT;`

3. **DROP:**

   - Deletes a database object, such as a table or view.
   - **Example:** `DROP TABLE Students;`

4. **TRUNCATE:**

   - Removes all rows from a table without logging individual row deletions.
   - **Example:** `TRUNCATE TABLE Employees;`

5. **RENAME:**
   - Renames a database object like a table or column.
   - **Example:** `RENAME TABLE Old_Name TO New_Name;`

---

### **Q8: State Referential Integrity Constraint**

- **Definition:**  
  A referential integrity constraint ensures that a foreign key in one table corresponds to a valid primary key in another table.

- **Example:**
  - **Parent Table:** `Departments` with `Department_ID` as the primary key.
  - **Child Table:** `Employees` with `Department_ID` as a foreign key.
  - The constraint ensures that every `Department_ID` in `Employees` must exist in `Departments`.

---
### **1. Explanation of 2nd and 3rd Normal Forms**

#### **Second Normal Form (2NF)**  
- A table is in **2NF** if:
  1. It is already in **1NF** (no repeating groups, and each column contains atomic values).  
  2. Every non-key column depends on the **whole primary key**, not just part of it.  

**Example**:  

**Before 2NF (1NF table)**:  
| OrderID | ProductName | SupplierName | Quantity |  
|---------|-------------|--------------|----------|  
| 1       | Pen         | ABC Supplies | 50       |  
| 2       | Notebook    | XYZ Supplies | 20       |  

- Here, `OrderID` and `ProductName` together are the key, but `SupplierName` only depends on `ProductName`.  

**After 2NF**:  
**Orders Table**:  
| OrderID | ProductName | Quantity |  
|---------|-------------|----------|  
| 1       | Pen         | 50       |  
| 2       | Notebook    | 20       |  

**Products Table**:  
| ProductName | SupplierName |  
|-------------|--------------|  
| Pen         | ABC Supplies |  
| Notebook    | XYZ Supplies |  

---

#### **Third Normal Form (3NF)**  
- A table is in **3NF** if:
  1. It is already in **2NF**.  
  2. There are no **transitive dependencies** (non-key columns should not depend on other non-key columns).  

**Example**:  

**Before 3NF (2NF table)**:  
| EmployeeID | EmployeeName | DepartmentID | DepartmentName | Manager |  
|------------|--------------|--------------|----------------|---------|  
| 1          | Alice        | D001         | HR             | John    |  
| 2          | Bob          | D002         | IT             | Mark    |  

- Here, `DepartmentName` and `Manager` depend on `DepartmentID`, not on `EmployeeID`.  

**After 3NF**:  
**Employees Table**:  
| EmployeeID | EmployeeName | DepartmentID |  
|------------|--------------|--------------|  
| 1          | Alice        | D001         |  
| 2          | Bob          | D002         |  

**Departments Table**:  
| DepartmentID | DepartmentName | Manager |  
|--------------|----------------|---------|  
| D001         | HR             | John    |  
| D002         | IT             | Mark    |  

---

### **2. Differences**

#### **a) DELETE vs TRUNCATE**  

| Feature       | **DELETE**                                     | **TRUNCATE**                                |
|---------------|-----------------------------------------------|--------------------------------------------|
| **Purpose**    | Removes specific rows from the table.          | Removes all rows from the table.           |
| **Condition**  | You can use a `WHERE` clause to delete rows.   | No condition; deletes all rows.            |
| **Performance**| Slower because it logs each deleted row.       | Faster as it does not log individual rows. |
| **Rollback**   | Can be rolled back if inside a transaction.    | Cannot be rolled back.                     |
| **Triggers**   | Activates triggers on the table.               | Does not activate triggers.                |

---

#### **b) PRIMARY KEY vs UNIQUE KEY**  

| Feature       | **PRIMARY KEY**                             | **UNIQUE KEY**                            |
|---------------|--------------------------------------------|-------------------------------------------|
| **Uniqueness**| Ensures all rows are unique and no NULLs.   | Ensures uniqueness but allows NULLs.      |
| **Purpose**   | Used to identify each row in the table.      | Used to ensure no duplicate values in a column. |
| **Quantity**  | Only one primary key per table.             | Can have multiple unique keys in a table. |
| **Index**     | Creates a clustered index.                  | Creates a non-clustered index.            |
---

### **SQL Queries for the Given Schema**
### Created Tables with Data

#### **Table Schemas : **
##### **Salesman Table**
| Salesman_id | Name  | City       | Comission |
|-------------|-------|------------|-----------|

##### **Customer Table**
| Customer_id | Customer_name | City       | Grade | Salesman_id |
|-------------|---------------|------------|-------|-------------|

##### **Order Table**
| Order_no | Purchase_amt | Order_date | Customer_id | Salesman_id |
|----------|--------------|------------|-------------|-------------|

---

#### **Salesman Table**
| Salesman_id | Name  | City       | Comission |
|-------------|-------|------------|-----------|
| 1           | Raj   | Delhi      | 500.00    |
| 2           | Amit  | Pune       | 800.00    |
| 3           | Sara  | Bangalore  | 600.00    |
| 4           | John  | Mumbai     | 700.00    |

---

#### **Customer Table**
| Customer_id | Customer_name | City       | Grade | Salesman_id |
|-------------|---------------|------------|-------|-------------|
| 101         | Ravi          | Delhi      | 1     | 1           |
| 102         | Priya         | Pune       | 2     | 2           |
| 103         | Karan         | Bangalore  | 3     | 3           |
| 104         | Anjali        | Mumbai     | 1     | 4           |
| 105         | Neha          | Delhi      | 2     | 1           |

---

#### **Order Table**
| Order_no | Purchase_amt | Order_date | Customer_id | Salesman_id |
|----------|--------------|------------|-------------|-------------|
| 1001     | 5500.00      | 2024-11-01 | 101         | 1           |
| 1002     | 4500.00      | 2024-11-05 | 102         | 2           |
| 1003     | 6000.00      | 2024-11-10 | 103         | 3           |
| 1004     | 3000.00      | 2024-11-15 | 104         | 4           |
| 1005     | 7500.00      | 2024-11-18 | 105         | 1           |

---

### **Schema for `Salesman` Table**  
```sql
CREATE TABLE Salesman (
    Salesman_id INT PRIMARY KEY,   -- Unique identifier for salesman
    Name VARCHAR(50) NOT NULL,    -- Name of the salesman
    City VARCHAR(50),             -- City of the salesman
    Comission DECIMAL(10, 2)      -- Commission earned by the salesman
);
```

---

### **Schema for `Order` Table**  
```sql
CREATE TABLE Order (
    Order_no INT PRIMARY KEY,        -- Unique identifier for order
    Purchase_amt DECIMAL(10, 2),     -- Purchase amount of the order
    Order_date DATE,                 -- Date of the order
    Customer_id INT,                 -- Customer who placed the order
    Salesman_id INT,                 -- Salesman associated with the order
    FOREIGN KEY (Customer_id) REFERENCES Customer(Customer_id), -- Foreign key to Customer table
    FOREIGN KEY (Salesman_id) REFERENCES Salesman(Salesman_id)  -- Foreign key to Salesman table
);
```

---

### **Schema for `Customer` Table**  
```sql
CREATE TABLE Customer (
    Customer_id INT PRIMARY KEY,   -- Unique identifier for customer
    Customer_name VARCHAR(50) NOT NULL, -- Name of the customer
    City VARCHAR(50),              -- City of the customer
    Grade INT,                     -- Grade of the customer
    Salesman_id INT,               -- Associated salesman for the customer
    FOREIGN KEY (Salesman_id) REFERENCES Salesman(Salesman_id) -- Foreign key to Salesman table
);
```

---

### **Key Points of the Schema**
1. **Primary Keys**:
   - `Salesman_id` in `Salesman`.
   - `Order_no` in `Order`.
   - `Customer_id` in `Customer`.
   
2. **Foreign Keys**:
   - `Salesman_id` in `Order` and `Customer` references `Salesman(Salesman_id)`.
   - `Customer_id` in `Order` references `Customer(Customer_id)`.

3. **Data Types**:
   - `INT` for IDs and numeric values (e.g., grade).
   - `VARCHAR` for string values like names and cities.
   - `DECIMAL` for monetary values (e.g., `Purchase_amt`, `Comission`).
   - `DATE` for order dates.
---

#### **i) Remove all the orders whose purchase amount is less than 5000**  
```sql
DELETE FROM Order 
WHERE Purchase_amt < 5000;
```

---

#### **ii) Find the salesman and customer who live in the same city. Retrieve customer name, salesman name, and salesman city.**  
```sql
SELECT c.Customer_name, s.Name AS Salesman_name, s.City AS Salesman_city 
FROM Customer c 
JOIN Salesman s 
ON c.City = s.City;
```

---

#### **iii) Add information of a new salesman in the salesman table.**  
```sql
INSERT INTO Salesman (Salesman_id, Name, City, Comission) 
VALUES (101, 'Amit', 'Mumbai', 800);
```

---

#### **iv) Find the total orders placed by each customer. Retrieve customer id and total orders.**  
```sql
SELECT Customer_id, COUNT(Order_no) AS Total_Orders 
FROM Order 
GROUP BY Customer_id;
```

---

#### **v) Write the relational algebra query to show the details of all customers.**  
**Relational Algebra Query:**  
```
Π(Customer_id, Customer_name, City, Grade, Salesman_id)(Customer)
```

---

#### **vi) Find the orders made by customers. Retrieve order number and customer name.**  
```sql
SELECT o.Order_no, c.Customer_name 
FROM Order o 
JOIN Customer c 
ON o.Customer_id = c.Customer_id;
```

---

#### **vii) Find the salesman who earns a commission not equal to 500.**  
```sql
SELECT * 
FROM Salesman 
WHERE Comission <> 500;
```

---

#### **viii) Find the customers who live in cities Delhi, Pune, Bangalore, or Bhopal.**  
```sql
SELECT * 
FROM Customer 
WHERE City IN ('Delhi', 'Pune', 'Bangalore', 'Bhopal');
```

---

#### **ix) Change the salesman name from 'Raj' to 'Raju'.**  
```sql
UPDATE Salesman 
SET Name = 'Raju' 
WHERE Name = 'Raj';
```

---

#### **x) Retrieve all the details from the salesman table.**  
```sql
SELECT * 
FROM Salesman;
```

---
### **Q1a) Transformation of ER Diagram Components into Relations**

#### **i) Regular Entity Type**  
A regular (strong) entity type is directly transformed into a relation (table).  
- Each attribute of the entity becomes a column in the relation.  
- The primary key of the entity is used as the primary key of the relation.  

**Example:**  
Entity: `Employee(ID, Name, Age, Department)`  
Relation:  
```sql
CREATE TABLE Employee (
  ID INT PRIMARY KEY,
  Name VARCHAR(50),
  Age INT,
  Department VARCHAR(50)
);
```

---

#### **ii) Composite Attribute**  
Composite attributes are broken down into their constituent simple attributes. These simple attributes are included as columns in the relation.  

**Example:**  
Composite Attribute: `FullName (FirstName, LastName)`  
Relation:  
```sql
CREATE TABLE Person (
  ID INT PRIMARY KEY,
  FirstName VARCHAR(50),
  LastName VARCHAR(50)
);
```

---

### **Q1b) Characteristics of Data Models**

| **Feature**            | **Relational Model**                                      | **Hierarchical Model**                             | **Network Model**                                      |
|------------------------|----------------------------------------------------------|--------------------------------------------------|-------------------------------------------------------|
| **Structure**          | Tables (relations) with rows and columns.                | Tree-like structure with parent-child hierarchy. | Graph structure with records and sets.               |
| **Data Representation**| Data stored in tuples (rows) and attributes (columns).    | Data stored as records with parent-child links.  | Data stored as records with multiple parent-child links. |
| **Relationships**      | Established using primary and foreign keys.              | One-to-many relationships (parent to child).     | Many-to-many relationships via pointers.             |
| **Flexibility**        | Highly flexible and easy to modify.                      | Rigid; requires restructuring for changes.       | Less rigid than hierarchical but still complex.       |
| **Ease of Use**        | Easy for end users and applications.                     | Complex to query and update.                     | Moderate complexity in query and update.             |

---

### **Q2a) Logical and Physical Data Independence**

#### **Logical Data Independence**  
- Refers to the ability to change the conceptual schema (e.g., adding/removing tables) without affecting the external schema or application programs.  
- **Example**: Adding a new attribute to a table without modifying application queries.

#### **Physical Data Independence**  
- Refers to the ability to change the internal schema (e.g., changing storage mechanisms or file structures) without affecting the conceptual schema.  
- **Example**: Moving data from one disk to another without changing the database schema.

#### **Which is harder to achieve and why?**  
Logical data independence is harder to achieve because it requires applications to be isolated from schema changes at the logical level, which involves reworking data access layers and query adjustments. Physical independence primarily involves storage changes, which have less impact on application logic.

---

### **Q2b) Degree of Relationship**

The degree of a relationship in an ER diagram refers to the number of entities participating in the relationship.  

#### **Types of Relationship Degree**

1. **Unary Relationship (Degree 1)**  
   Involves a single entity type.  
   **Example**: An employee supervises another employee.  
   ``` 
   Employee (ID, Name, SupervisorID) 
   ```

2. **Binary Relationship (Degree 2)**  
   Involves two different entity types.  
   **Example**: A student enrolls in a course.  
   ``` 
   Student(ID, Name)  
   Course(ID, Title)  
   Enrollment(StudentID, CourseID)  
   ```

3. **Ternary Relationship (Degree 3)**  
   Involves three entity types.  
   **Example**: A supplier supplies a product to a project.  
   ``` 
   Supplier(ID, Name)  
   Product(ID, Name)  
   Project(ID, Title)  
   Supplies(SupplierID, ProductID, ProjectID)  
   ```
   
---


### Q3a) Four of Codd's Rules:

Codd's 12 rules are a set of guidelines proposed by Dr. Edgar F. Codd to define what constitutes a relational database management system (RDBMS). Below are four of them:

1. **Rule 1 - Information Rule:**
   All information in a relational database is represented explicitly as values in tables (also known as relations). This includes both data and metadata (e.g., column names, table names). Everything must be stored in a tabular format.

2. **Rule 2 - Guaranteed Access Rule:**
   Every piece of data in a relational database should be accessible by using a combination of table name, primary key, and attribute name. This ensures that the data is not hidden in any other way and can be retrieved with certainty.

3. **Rule 3 - Systematic Treatment of Null Values:**
   Null values (representing missing or unknown information) should be treated systematically in the database. Null should not be confused with zero or empty strings. All operations on the database should recognize and correctly handle null values.

4. **Rule 5 - Data Independence:**
   The data in a relational database should be logically independent from the application programs that use the data. Changes to the database's structure should not require changes to application programs, thus supporting data independence.

---

### Q3b) Types of Database Users and Role of Database Administrator (DBA):

**Types of Database Users:**

1. **End Users:**
   These are the people who directly interact with the database through applications. They can be classified into:
   - **Naive users**: These users interact with the database using pre-designed applications, often through user interfaces (e.g., query forms).
   - **Parametric users**: These users interact with the database through a set of queries and commands (e.g., SQL users).
   - **Sophisticated users**: These users have expertise in the database system and might develop complex queries, reports, or use programming interfaces.

2. **Application Programmers:**
   These users write application programs that interact with the database using languages like SQL, Java, or Python. They create software that manipulates the data stored in the database.

3. **Database Administrators (DBAs):**
   DBAs are responsible for the overall management and maintenance of the database system. Their tasks include:
   - Database design and implementation.
   - Ensuring data security, integrity, and availability.
   - Performing regular backups and recovery operations.
   - Managing database performance and optimization.
   - Creating user access controls and permissions.
   - Handling data migration, patching, and upgrades.

---

### Q4a) What is Normalization? Why Do We Normalize a Database? Explain the Second Normal Form (2NF) with an Example:

**Normalization:**
Normalization is the process of organizing the data in a database to reduce redundancy and improve data integrity. This process involves dividing large tables into smaller, related tables and ensuring that relationships among the data are well-structured.

**Why Normalize a Database:**
- **Reduce Data Redundancy:** It avoids the unnecessary duplication of data.
- **Improve Data Integrity:** Normalization ensures that the data is consistent and follows rules that help maintain its accuracy.
- **Simplify Data Structure:** It makes querying and updating the data easier and more efficient.
- **Improve Storage Efficiency:** By eliminating duplicate data, normalization can reduce the overall storage requirements.

**Second Normal Form (2NF):**
A table is in 2NF if it is in **First Normal Form (1NF)** and if all non-key attributes are fully functionally dependent on the primary key (no partial dependencies).

- **1NF**: The table must have a primary key and all attributes must contain atomic values (no repeating groups).
- **2NF**: The table must not have any partial dependency. This means that if a table has a composite primary key, all non-key attributes must depend on the entire primary key, not just part of it.

**Example of 2NF:**

Consider a table that stores information about students and their enrolled courses:

| StudentID | CourseID | StudentName | Instructor |
|-----------|----------|-------------|------------|
| 1         | CS101    | Alice       | Prof. A    |
| 2         | CS101    | Bob         | Prof. A    |
| 3         | MATH101  | Charlie     | Prof. B    |

This table is in **1NF** but violates **2NF** because `StudentName` is partially dependent on `StudentID` and `Instructor` is partially dependent on `CourseID`. To convert it into 2NF, we split the table into two:

- **Student Table**:
  | StudentID | StudentName |
  |-----------|-------------|
  | 1         | Alice       |
  | 2         | Bob         |
  | 3         | Charlie     |

- **Course Enrollment Table**:
  | StudentID | CourseID | Instructor |
  |-----------|----------|------------|
  | 1         | CS101    | Prof. A    |
  | 2         | CS101    | Prof. A    |
  | 3         | MATH101  | Prof. B    |

Now, both tables are in 2NF, as all non-key attributes are fully functionally dependent on the entire primary key.

---

### Q4a) What is Normalization? Why Do We Normalize a Database? Explain All Normal Forms with Examples

#### **What is Normalization?**

Normalization is the process of organizing data in a relational database to minimize redundancy and dependency. The primary goal of normalization is to ensure data consistency and integrity by dividing large, complex tables into smaller, manageable ones and establishing appropriate relationships between them. This process helps eliminate anomalies that can occur when inserting, updating, or deleting data.

#### **Why Do We Normalize a Database?**

Normalization is done to:
1. **Eliminate Redundancy:** By organizing data into smaller tables, you remove duplicated information, reducing storage requirements.
2. **Improve Data Integrity:** Minimizing redundancy reduces the chances of data inconsistencies.
3. **Avoid Anomalies:** Proper normalization prevents data anomalies like update, insert, and delete anomalies.
4. **Enhance Flexibility:** A normalized database structure is more adaptable to changes in business requirements.

---

### **Normal Forms**

Normalization involves breaking down a database into smaller tables and ensuring they satisfy certain conditions, which are defined in "normal forms." There are several normal forms, each building on the previous one. Here’s an explanation of each normal form along with examples:

#### **1. First Normal Form (1NF):**

A table is in **1NF** if:
- It only contains atomic (indivisible) values.
- Each record is unique.
- Each field contains only a single value (no repeating groups or arrays).

**Example of 1NF:**

Consider a table of students and their courses:

| StudentID | StudentName | Courses          |
|-----------|-------------|------------------|
| 1         | Alice       | Math, Physics    |
| 2         | Bob         | Chemistry, Math  |

This table is not in **1NF** because the "Courses" column contains multiple values (i.e., the values are not atomic).

To convert it to **1NF**, we break the "Courses" column into individual rows:

| StudentID | StudentName | Course      |
|-----------|-------------|-------------|
| 1         | Alice       | Math        |
| 1         | Alice       | Physics     |
| 2         | Bob         | Chemistry   |
| 2         | Bob         | Math        |

Now, the table is in **1NF**, as each value is atomic and each record is unique.

---

#### **2. Second Normal Form (2NF):**

A table is in **2NF** if:
- It is in **1NF**.
- All non-key attributes are fully functionally dependent on the entire primary key. There are no partial dependencies (i.e., if the primary key is composite, every non-key attribute must depend on all parts of the composite key).

**Example of 2NF:**

Consider the following table where the primary key is a combination of `StudentID` and `CourseID`:

| StudentID | CourseID | StudentName | Instructor |
|-----------|----------|-------------|------------|
| 1         | CS101    | Alice       | Prof. A    |
| 1         | MATH101  | Alice       | Prof. B    |
| 2         | CS101    | Bob         | Prof. A    |

Here, the primary key is a composite of `StudentID` and `CourseID`. However, the `StudentName` depends only on `StudentID`, and the `Instructor` depends only on `CourseID`. These are partial dependencies.

To bring the table into **2NF**, we remove partial dependencies by creating two tables:

- **Student Table:**
  
  | StudentID | StudentName |
  |-----------|-------------|
  | 1         | Alice       |
  | 2         | Bob         |

- **Enrollment Table:**

  | StudentID | CourseID | Instructor |
  |-----------|----------|------------|
  | 1         | CS101    | Prof. A    |
  | 1         | MATH101  | Prof. B    |
  | 2         | CS101    | Prof. A    |

Now, the table is in **2NF** because there are no partial dependencies.

---

#### **3. Third Normal Form (3NF):**

A table is in **3NF** if:
- It is in **2NF**.
- No transitive dependencies exist, i.e., non-key attributes must not depend on other non-key attributes.

**Example of 3NF:**

Consider the following table where the primary key is `StudentID`:

| StudentID | StudentName | Department | DepartmentHead |
|-----------|-------------|------------|----------------|
| 1         | Alice       | CS         | Dr. Smith      |
| 2         | Bob         | Math       | Dr. Johnson    |

Here, `DepartmentHead` is dependent on `Department`, which is a non-key attribute. This is a **transitive dependency**: `DepartmentHead` depends on `Department`, and `Department` depends on `StudentID`.

To convert this to **3NF**, we remove the transitive dependency by splitting the table into two:

- **Student Table:**

  | StudentID | StudentName | Department |
  |-----------|-------------|------------|
  | 1         | Alice       | CS         |
  | 2         | Bob         | Math       |

- **Department Table:**

  | Department | DepartmentHead |
  |------------|----------------|
  | CS         | Dr. Smith      |
  | Math       | Dr. Johnson    |

Now, the table is in **3NF** because all non-key attributes depend only on the primary key, with no transitive dependencies.

---

#### **4. Boyce-Codd Normal Form (BCNF):**

A table is in **BCNF** if:
- It is in **3NF**.
- For every functional dependency (A → B), A must be a superkey. In other words, every determinant (attribute on the left side of a functional dependency) must be a candidate key.

**Example of BCNF:**

Consider the following table:

| StudentID | CourseID | Instructor |
|-----------|----------|------------|
| 1         | CS101    | Prof. A    |
| 1         | MATH101  | Prof. B    |
| 2         | CS101    | Prof. A    |

Here, `CourseID` → `Instructor` is a functional dependency, but `CourseID` is not a superkey. This violates BCNF.

To convert this to **BCNF**, we split the table into two:

- **Course Table:**

  | CourseID | Instructor |
  |----------|------------|
  | CS101    | Prof. A    |
  | MATH101  | Prof. B    |

- **Enrollment Table:**

  | StudentID | CourseID |
  |-----------|----------|
  | 1         | CS101    |
  | 1         | MATH101  |
  | 2         | CS101    |

Now, the table is in **BCNF** because all functional dependencies have a superkey on the left side.

---

#### **5. Fourth Normal Form (4NF):**

A table is in **4NF** if:
- It is in **BCNF**.
- It has no multi-valued dependencies (i.e., one attribute determines multiple independent attributes).

**Example of 4NF:**

Consider a table storing students and their multiple phone numbers and email addresses:

| StudentID | PhoneNumber | Email              |
|-----------|-------------|--------------------|
| 1         | 12345       | alice@mail.com     |
| 1         | 67890       | alice@gmail.com    |
| 2         | 11111       | bob@mail.com       |

Here, `PhoneNumber` and `Email` are independent of each other but are both related to `StudentID`. This violates **4NF** because we have multi-valued dependencies.

To bring this into **4NF**, we separate the multi-valued attributes into separate tables:

- **Student Table:**

  | StudentID |
  |-----------|
  | 1         |
  | 2         |

- **PhoneNumber Table:**

  | StudentID | PhoneNumber |
  |-----------|-------------|
  | 1         | 12345       |
  | 1         | 67890       |
  | 2         | 11111       |

- **Email Table:**

  | StudentID | Email         |
  |-----------|---------------|
  | 1         | alice@mail.com|
  | 1         | alice@gmail.com|
  | 2         | bob@mail.com  |

Now, the data is in **4NF** as each multi-valued dependency has been eliminated.

---

#### **Conclusion:**

Normalization is a crucial step in database design that aims to reduce redundancy and ensure data integrity. Each **normal form** (1NF, 2NF, 3NF, BCNF, and 4NF) refines the database structure by addressing specific types of anomalies or dependencies, ensuring that the database is both efficient and logically sound. By applying normalization, you achieve a balance between reducing redundancy and making the database easier to maintain and query.

---

### Q4b) Three Basic Relational Algebra Operators:

Relational algebra provides a set of operations that can be used to query and manipulate data in relational databases. The basic operators are:

1. **Select (σ):**
   The select operator is used to filter rows based on a given condition (predicate). It returns a subset of rows from a table.
   - Example: `σ(condition)(Table)`
   - Query: Select all students who scored above 90 in a table of student scores.
   
   ``` 
   σ(Score > 90)(Students)
   ```

2. **Project (π):**
   The project operator is used to select specific columns from a table. It helps in eliminating unwanted attributes and focusing on the relevant ones.
   - Example: `π(column1, column2, ...)(Table)`
   - Query: Retrieve the names and ages of all employees from an employees table.

   ``` 
   π(Name, Age)(Employees)
   ```

3. **Join (⨝):**
   The join operator is used to combine related tuples from two relations based on a common attribute. There are various types of joins, but the most basic is the **natural join**.
   - Example: `R ⨝ S` where `R` and `S` are tables that share one or more common attributes.
   - Query: Retrieve all details of students and their respective courses by joining the Students and Courses tables on `StudentID`.
   
   ``` 
   Students ⨝ Courses
   ```

These operators are fundamental in manipulating relational data and forming complex queries for retrieving useful information from a database.


### Q5a) Definitions:

**i) Candidate Key:**
A *candidate key* is a set of one or more attributes (columns) that can uniquely identify a record in a database table. It is a minimal superkey, meaning no subset of the candidate key can uniquely identify the record. A table can have multiple candidate keys, but one will be chosen as the primary key.

**ii) Primary Key:**
A *primary key* is a special candidate key chosen to uniquely identify each record in a database table. It must have the following properties:
- Uniqueness: No two rows can have the same value for the primary key.
- Non-nullability: Every record must have a value for the primary key (cannot be NULL).

A table can only have one primary key.

**iii) Alternate Key:**
An *alternate key* refers to any candidate key that is not selected as the primary key. These are essentially secondary options that could uniquely identify records, but are not used as the primary key.

---

### Q5b) What is Mapping Cardinality? Explain ALTER and UPDATE command:

**Mapping Cardinality:**
Mapping cardinality refers to the relationship between two sets or tables in a database. It defines how many instances of one entity are related to instances of another entity. In relational databases, it is typically represented by the cardinality of relationships between tables. The types of cardinalities are:
- **One-to-One (1:1):** One record in a table is related to exactly one record in another table.
- **One-to-Many (1:M):** One record in a table is related to multiple records in another table.
- **Many-to-Many (M:N):** Multiple records in one table are related to multiple records in another table.

**ALTER Command:**
The `ALTER` command is used to modify the structure of an existing database object (like a table). It can perform operations such as adding, deleting, or modifying columns, or even renaming a table. Example:
- `ALTER TABLE table_name ADD column_name data_type;`
- `ALTER TABLE table_name DROP COLUMN column_name;`

**UPDATE Command:**
The `UPDATE` command is used to modify the data within a table. It allows you to change existing records based on specific conditions. Example:
- `UPDATE table_name SET column_name = new_value WHERE condition;`

---

### Q5c) What is Null?

**Null:**
In database terminology, *NULL* represents the absence of a value or the lack of data in a field. It is not the same as an empty string or zero; it simply means that the value is unknown, undefined, or missing. A field containing a NULL value does not hold any actual data, and special handling is required when querying or performing operations involving NULL values (e.g., `IS NULL` or `IS NOT NULL`).
