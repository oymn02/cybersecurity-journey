# SQL Injection (SQLi)

## 1. What it is

SQL injection is a vulnerability that occurs when an application builds a database query using untrusted input in a way that lets that input change the query's structure.

The important distinction is between **data** and **SQL instructions**. User input should be treated as data only. With SQL injection, input is interpreted as part of the SQL command.

## 2. A simplified example

Imagine a shop that lets users filter products by category. The application might build a query like this:

```sql
SELECT * FROM products
WHERE category = 'Gifts'
  AND released = 1;
```

- `SELECT *` asks for all columns.
- `FROM products` identifies the table.
- `category = 'Gifts'` applies the selected category.
- `released = 1` limits the results to products marked as released.

If the application inserts the category value directly into the query, a carefully crafted input could change the logic of the `WHERE` clause. The result may include records the application intended to hide.

## 3. Why it happens

A common root cause is constructing SQL through string concatenation instead of using parameterized queries.

Conceptually, unsafe code mixes the query structure and the user's input. Secure code keeps them separate.

## 4. How to prevent it

**Use parameterized queries (prepared statements)** for values supplied by users. The database receives the SQL structure separately from the parameter values, so the input cannot redefine the query.

Additional safeguards:

- Apply least-privilege permissions to database accounts.
- Validate input according to the expected business rules.
- Use allow-lists when dynamic identifiers such as sort-column names are required.
- Handle database errors safely and avoid exposing internal details.
- Do not rely on keyword blacklists or ad hoc escaping as the primary defense.

## 5. Practical exercise

The first exercise is the PortSwigger Web Security Academy lab:

[SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)

See the [lab notes](../labs/portswigger-retrieve-hidden-data.md) for the objective and observation checklist.

## 6. Key terms

| Term | Meaning |
|---|---|
| SQL | Structured Query Language, used to work with relational databases |
| Query | An instruction sent to a database |
| WHERE clause | Filters which rows a query returns or changes |
| Parameterized query | A query whose structure is separated from its input values |
| Injection | Untrusted input changes the meaning or structure of a command |

## 7. What I learned

_To be completed after the practical exercise._

## 8. References

- [PortSwigger: What is SQL injection?](https://portswigger.net/web-security/sql-injection)
- [PortSwigger: SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [OWASP: SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
