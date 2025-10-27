# task5
# ☁️ Task 5: Create and Connect to a Cloud Database Instance (MSSQL)

## 🎯 Objective
To understand how *Cloud Databases* work by creating and connecting to a *managed SQL database instance* and performing basic operations (CRUD).

This task helps in learning:
- How to *create* a database in the cloud
- How to *connect* from SQL Server Management Studio (SSMS)
- How to perform *basic SQL operations* (Create, Read, Update, Delete)

---

## 🛠️ Tools Used
- *Platform:* AWS RDS (MySQL) / Azure SQL / Local SQL Server  
- *Client Tool:* SQL Server Management Studio (SSMS)  
- *Database Engine:* Microsoft SQL Server (MSSQL)  

---

## ⚙️ Steps Followed

### 1️⃣ Create a Cloud Database Instance
- Logged in to *AWS Console → RDS*  
- Chose *MySQL (Free Tier)* or used *Azure SQL Server*  
- Set:
  - *Instance name:* intern-db
  - *Username:* admin
  - *Password:* (strong password)
- Enabled *public access*
- Waited until instance status showed *Available*

### 2️⃣ Configure Access
- Added my *local IP* in the security group inbound rule  
- Allowed port *3306 (MySQL)* or *1433 (MSSQL)* for SQL Server  
- Copied the *endpoint / public IP*

### 3️⃣ Connect to the Database
- Opened *SQL Server Management Studio (SSMS)*  
- Used:
  - Server name: your-endpoint.amazonaws.com
  - Authentication: SQL Server Authentication  
  - Login: admin
  - Password: yourpassword
- Clicked *Connect* ✅  

---

## 🧱 SQL Commands Used

```sql
-- Use database
USE intern_demo;
GO

-- Drop table if already exists
DROP TABLE IF EXISTS students;
GO

-- Create new table
CREATE TABLE students (
    id INT IDENTITY(1,1) PRIMARY KEY,
    name VARCHAR(50),
    domain VARCHAR(30),
    score INT
);
GO

-- Insert sample data
INSERT INTO students (name, domain, score)
VALUES 
('Aarav', 'Cloud', 95),
('Diya', 'DevOps', 89);
GO

-- View data
SELECT * FROM students;
GO

-- Update data
UPDATE students
SET score = 98
WHERE name = 'Aarav';
GO

-- Delete a record
DELETE FROM students
WHERE name = 'Diya';
GO

-- Final view
SELECT * FROM students;
GO
