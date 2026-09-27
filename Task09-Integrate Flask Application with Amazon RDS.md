# Task 09 - Integrate Flask Application with Amazon RDS

## Objective

Integrate the Flask backend application with Amazon RDS MySQL and validate data storage.

---

## Why Integration?

Before:

```text
User
   │
   ▼
Flask
```

User data is processed but not stored permanently.

After:

```text
User
   │
   ▼
Flask
   │
   ▼
Amazon RDS MySQL
```

User data is stored in the database.

---

## Services Used

- Flask
- Amazon RDS MySQL
- PyMySQL
- EC2

---

## Implementation Steps

### Step 1

Create RDS MySQL database.

```sql
CREATE DATABASE feedbackdb;
```

### Step 2

Create feedback table.

```sql
CREATE TABLE feedback (
 id INT AUTO_INCREMENT PRIMARY KEY,
 name VARCHAR(100),
 email VARCHAR(100),
 feedback TEXT
);
```

### Step 3

Update Flask application.

```python
DB_CONFIG = {
    'host': 'RDS-ENDPOINT',
    'user': 'admin',
    'password': 'password',
    'db': 'feedbackdb'
}
```

### Step 4

Restart Flask application.

```bash
python3 app.py
```

### Step 5

Send test request.

```bash
curl -X POST http://localhost:5000/submit
```

### Step 6

Validate data insertion.

```sql
SELECT * FROM feedback;
```

---

## Architecture

```text
User
   │
   ▼
Web Tier
   │
   ▼
Flask Application
   │
   ▼
Amazon RDS MySQL
```

---

## Validation

Verified:

- Successful database connection
- Successful insertion of user feedback
- Records available in MySQL table

---

## Outcome

Successfully integrated Flask with Amazon RDS MySQL and validated end-to-end database operations.
