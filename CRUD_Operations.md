# CRUD Operations

## What is CRUD?

| Letter | Operation | SQL Equivalent |
|---|---|---|
| **C** | Create a table / Insert a row | `CREATE`, `INSERT` |
| **R** | Read / Fetch records | `SELECT` |
| **U** | Update rows | `UPDATE` |
| **D** | Delete rows | `DELETE` |

---

## PreparedStatement for CRUD

Use `PreparedStatement` instead of plain `Statement` to:
- Avoid manual quotation handling
- Prevent **SQL Injection**
- Skip recompilation on every call *(queries are pre-compiled once)*

### How it works — INSERT Example

```java
// 1. Write SQL with ? placeholders
String sql = "INSERT INTO student VALUES(?, ?, ?)";

// 2. Create PreparedStatement
PreparedStatement pst = con.prepareStatement(sql);

// 3. Set values for each placeholder (index starts at 1)
pst.setInt(1, row);       // int parameter
pst.setString(2, name);   // String parameter
pst.setString(3, loc);    // String parameter

// 4. Execute and check rows affected
int val = pst.executeUpdate();
System.out.println(val);
```

---

## Quick Reference — Execute Methods

| Method | Use for | Returns |
|---|---|---|
| `executeQuery(sql)` | `SELECT` | `ResultSet` |
| `executeUpdate(sql)` | `INSERT`, `UPDATE`, `DELETE`, `CREATE`, `ALTER`, `DROP` | `int` (rows affected) |
| `execute(sql)` | Any statement | `boolean` |

> **Tip:** Prefer `executeUpdate()` for data-changing operations.  
> Avoid `execute()` when possible — its return value requires extra handling.
