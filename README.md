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

Screenshots

(Add your own screenshots below)

1️⃣ Database instance running (AWS RDS or Azure SQL)
2️⃣ Successful connection in SSMS
3️⃣ Query result (table data output)


---

🧠 What I Learned

How to create a cloud database instance (DBaaS)

How to connect using SSMS

How to run SQL queries to manage data

The importance of security groups and IP whitelisting

Basics of CRUD operations (Create, Read, Update, Delete)



---

💬 Interview Prep

Question	Simple Answer

What is DBaaS?	Database-as-a-Service — managed by the cloud provider.
Why use cloud databases?	No need for manual setup, auto backups, easy scaling, high availability.
What’s the difference between self-hosted and managed DB?	Managed DBs are handled by the provider (patching, backup, HA).
How to connect securely?	Use your IP in inbound rules, use SSL, avoid 0.0.0.0/0.
What is scalability?	Ability to increase resources easily (CPU, storage).



---

🧹 Clean-up

After testing, delete or stop your instance to avoid unnecessary charges:

In AWS → RDS → Databases → Select your DB → Delete

Uncheck snapshot (for testing)

Confirm deletion ✅



---

📚 Author

Ashwini Rathod
Simplilearn Certified Cloud Architect (2024)
GitHub: https://github.com/Ashwinigrathod

---

