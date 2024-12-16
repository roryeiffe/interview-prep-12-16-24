### **Databases: SQL and NoSQL**


### **1. SQL Databases (Relational)**
Relational databases store data in structured tables with predefined schemas. Each table represents an entity, with rows as records and columns as attributes.

#### **Key Concepts**
- **Schema:** The structure of the database, including tables, columns, and data types.
- **Primary Key:** A unique identifier for each record in a table.
- **Foreign Key:** A reference to the primary key in another table, enabling relationships between tables.
- **Normalization:** The process of organizing data to reduce redundancy and dependency.

#### **Common SQL Commands**
1. **Data Retrieval:**
   - `SELECT`: Retrieve data.
     - Example: `SELECT name, age FROM users WHERE age > 25;`
   - `JOIN`: Combine data from multiple tables.
     - Example: `SELECT orders.id, customers.name FROM orders JOIN customers ON orders.customer_id = customers.id;`
   - `GROUP BY` and `HAVING`: Aggregate and filter grouped data.
     - Example: `SELECT department, AVG(salary) FROM employees GROUP BY department HAVING AVG(salary) > 50000;`
2. **Data Manipulation:**
   - `INSERT`: Add new records.
     - Example: `INSERT INTO users (name, email) VALUES ('John', 'john@example.com');`
   - `UPDATE`: Modify existing records.
     - Example: `UPDATE users SET age = 30 WHERE id = 1;`
   - `DELETE`: Remove records.
     - Example: `DELETE FROM users WHERE id = 5;`
3. **Data Definition:**
   - `CREATE TABLE`: Define a new table.
     - Example:
       ```sql
       CREATE TABLE users (
           id INT PRIMARY KEY,
           name VARCHAR(100),
           email VARCHAR(100) UNIQUE
       );
       ```
   - `ALTER TABLE`: Modify an existing table.
     - Example: `ALTER TABLE users ADD COLUMN phone VARCHAR(15);`
4. **Indexing:**
   - Improve query performance by creating indexes.
     - Example: `CREATE INDEX idx_name ON users (name);`

#### **Advanced SQL Topics**
- **Transactions:**
  - Ensure consistency with ACID properties (Atomicity, Consistency, Isolation, Durability).
  - Example:
    ```sql
    BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 100 WHERE id = 1;
    UPDATE accounts SET balance = balance + 100 WHERE id = 2;
    COMMIT;
    ```
- **Window Functions:**
  - Perform calculations across a set of table rows related to the current row.
  - Example: `SELECT name, salary, RANK() OVER (ORDER BY salary DESC) AS rank FROM employees;`
- **Stored Procedures and Triggers:**
  - Encapsulate business logic in the database.
  - Example (Stored Procedure):
    ```sql
    CREATE PROCEDURE GetUserCount()
    BEGIN
      SELECT COUNT(*) FROM users;
    END;
    ```

---

### **2. NoSQL Databases (Non-Relational)**
NoSQL databases are designed for flexible schemas, scalability, and unstructured or semi-structured data. Types include key-value stores, document stores, column-family stores, and graph databases.

#### **Key Concepts**
- **Schema-Less:** No rigid schema; documents can have different fields.
- **Horizontal Scaling:** Easily distribute data across servers.
- **CAP Theorem:** Trade-offs between Consistency, Availability, and Partition tolerance.

#### **Popular NoSQL Database Types**
1. **Key-Value Stores:**
   - Data is stored as key-value pairs.
   - Example: Redis, DynamoDB.
   - Use case: Caching, session storage.
   - Example:
     ```bash
     SET user:1 "John Doe"
     GET user:1
     ```
2. **Document Stores:**
   - Store data as JSON-like documents.
   - Example: MongoDB, CouchDB.
   - Use case: Content management, user profiles.
   - Example (MongoDB):
     ```javascript
     db.users.insertOne({ name: "John", age: 30, hobbies: ["reading", "coding"] });
     db.users.find({ age: { $gt: 25 } });
     ```
3. **Column-Family Stores:**
   - Store data in column families (wide-column model).
   - Example: Cassandra, HBase.
   - Use case: Event logging, time-series data.
   - Example (CQL - Cassandra Query Language):
     ```sql
     CREATE TABLE users (id UUID PRIMARY KEY, name TEXT, email TEXT);
     INSERT INTO users (id, name, email) VALUES (uuid(), 'John', 'john@example.com');
     ```

---

### **SQL vs. NoSQL**
| Feature                  | SQL                          | NoSQL                     |
|--------------------------|------------------------------|---------------------------|
| **Schema**               | Fixed, predefined schema     | Flexible, schema-less     |
| **Data Relationships**   | Strong (joins, constraints) | Weak or embedded          |
| **Scalability**          | Vertical (scale up)          | Horizontal (scale out)    |
| **Query Language**       | SQL                         | Varies (e.g., JSON queries, CQL) |
| **Consistency**          | High                        | Eventual or tunable       |
| **Use Cases**            | Financial systems, ERPs     | Big data, IoT, social networks |

---

### **Interview Preparation Tips**
1. **SQL:**
   - Practice writing complex queries with joins, subqueries, and aggregations.
   - Study indexing and query optimization techniques.
   - Understand normalization vs. denormalization trade-offs.

2. **NoSQL:**
   - Get familiar with at least one NoSQL database like MongoDB or Cassandra.
   - Understand when to use NoSQL (e.g., high scalability, flexible schemas).
   - Practice schema design for document stores or graph databases.

3. **Hands-On Projects:**
   - Build a small SQL database for an inventory or library system.
   - Create a MongoDB-based API for managing user data.

4. **Sample Questions:**
   - SQL:
     - "Write a query to find the top 3 highest-paid employees in each department."
     - "Optimize this query: `SELECT * FROM employees WHERE salary > 50000;`"
   - NoSQL:
     - "Design a schema for a blogging platform using MongoDB."
     - "Explain how you would scale a Cassandra cluster for high write throughput.