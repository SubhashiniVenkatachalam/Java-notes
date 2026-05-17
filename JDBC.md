# JDBC (Java Database Connectivity)

## Connection Setup

```java
String url  = "jdbc:mysql://localhost:3306/";
String username = "root";
String pwd  = "Vsubha";
```

---

## 7 Steps to Connect Java with a Database

### Step 1 — Import the Required Package
```java
import java.sql.*;   // accepts a class name
```

### Step 2 — Load & Register the Class *(now optional)*
```java
// Static method — it's accepting a class name
Class.forName("com.mysql.jdbc.Driver");
// Note: This step is now optional; the driver is loaded automatically
```

### Step 3 — Establish the Connection
```java
Connection con = DriverManager.getConnection(url, username, pwd);
// Connection is an INTERFACE — so we can't do new Connection()
// DriverManager is a CLASS that acts as a factory to give us a Connection object
// The con object is then used to create statements
```

### Step 4 — Create a Statement
```java
// Statement is also an INTERFACE — con.createStatement() gives us the object
// You can create a Statement, PreparedStatement, or CallableStatement
Statement st = con.createStatement();
```

### Step 5 — Execute the Query
```java
// Always create the table in SQL before running SELECT
String sql = "SELECT * FROM students WHERE row = 2";

// executeQuery()  → for SELECT (returns ResultSet)
// executeUpdate() → for INSERT, UPDATE, DELETE, CREATE, ALTER, DROP
// execute()       → general; returns boolean
```

### Step 6 — Process the Result
```java
ResultSet res = st.executeQuery(sql);

while (res.next()) {           // res.next() — skips headers, reads row by row
    s.o.p(res.getInt("id"));
    s.o.p(res.getString("name")).getString();
}
```

### Step 7 — Close the Connection
```java
res.close();
st.close();
con.close();
```

---

## Return Types at a Glance

| Method | Returns |
|---|---|
| `executeQuery()` | `ResultSet` |
| `executeUpdate()` | `int` (rows affected) |
| `execute()` | `boolean` |

---

## SQL Injection & How to Avoid It

If user inputs are concatenated directly into a query string, a hacker can exploit it.

**Example of a vulnerable query:**
```sql
SELECT * FROM std WHERE username = "" OR '1' = '1'
```
When `username = " " OR '1'='1'` is passed, the database considers the condition always true and returns all data.

**Solution → Always use `PreparedStatement`** (see below).

---

## PreparedStatement

Use `PreparedStatement` to:
- Avoid many quotations
- Prevent SQL Injection
- Avoid normal recompilation every time *(pre-compiled — compiled once and reused)*

### 4-Step Pattern

```java
// Step 1 — Write the SQL with ? placeholders
String sql = "INSERT INTO student VALUES(?, ?, ?)";

// Step 2 — Create PreparedStatement
PreparedStatement pst = con.prepareStatement(sql);

// Step 3 — Bind parameters  (index starts at 1)
int row = 1;
String name = "Selbin";
String loc  = "Salem";

pst.setInt(1, row);
pst.setString(2, name);
pst.setString(3, loc);

// Step 4 — Execute
int val = pst.executeUpdate();
System.out.println(val);
```

> **Rule:** When user inputs are involved, always use `PreparedStatement`.  
> It locks the query structure so parameters cannot alter the SQL logic.
