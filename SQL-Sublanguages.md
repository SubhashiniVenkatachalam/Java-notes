# SQL Sub-Languages

> **Memory trick: "D D D D T" = 4 D's, 1 T**

---

## DDL — Data Definition Language
Deals with the **structure** of the table (create / alter the form of the table).

| Command | Description |
|---|---|
| `CREATE` | Create a new table |
| `ALTER` | Modify existing structure |
| `DROP` | Delete the table entirely |
| `TRUNCATE` | Remove all rows but keep structure |
| `RENAME` | Rename a table |

---

## DML — Data Manipulation Language
Used to **manipulate data** inside the table (random/any rows).

| Command | Description |
|---|---|
| `INSERT` | Add new rows |
| `UPDATE` | Modify existing rows |
| `DELETE` | Remove specific rows |

---

## DQL — Data Query Language
Used to **query / read data** from the table.

| Command | Description |
|---|---|
| `SELECT` | Fetch data from table |

---

## DCL — Data Control Language
Controls **access** to the data.

| Command | Description |
|---|---|
| `GRANT` | Give permission to a user |
| `REVOKE` | Remove permission from a user |

---

## TCL — Transaction Control Language
Used to **manage transactions** (save / undo operations).

| Command | Description |
|---|---|
| `COMMIT` | Save the transaction permanently |
| `ROLLBACK` | Undo changes back to last commit |
| `SAVEPOINT` | Set a checkpoint to rollback to |

> `COMMIT` = save, `ROLLBACK` = undo
