# Lab 01 · SQL injection in a WHERE clause

<small>Status: **Not started** · Platform: PortSwigger Web Security Academy · Level: Apprentice</small>

## Objective

Use the category filter in the deliberately vulnerable shop to make the application display at least one product that is not released.

**Authorized scope:** this exercise must be performed only in the temporary lab instance created by PortSwigger. Do not reuse the test input on real websites.

[Open the lab](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)

## 1. Understand the expected query

PortSwigger describes the application's query as:

```sql
SELECT * FROM products
WHERE category = 'Gifts'
  AND released = 1
```

The category is controlled by a request parameter. The `released = 1` condition is intended to exclude unreleased products.

## 2. Observe before changing anything

1. Open the lab page and select **Access the lab**.
2. In the lab shop, choose a product category.
3. Look at the browser address bar. Find the `category` parameter.
4. Record the normal category value and what the page displays.

Record your observations:

- **Category selected:**
- **Parameter name:**
- **Example request URL (remove any personal/session data):**
- **What products were displayed:**

## 3. Work out the query logic

Before trying an input, answer these questions:

1. Which part of the SQL query receives the category value?
2. Is that value inside single quotes?
3. What would happen if the input could close the quoted string?
4. What would happen if the condition in the `WHERE` clause became true for every row?
5. Why might a SQL comment marker matter at the end of the input?

Write down your hypothesis before testing it.

## 4. Test the lab

Use the lab's category parameter to test whether the input changes the query logic. You can edit the request with Burp Suite Community Edition, or carefully edit the category value in the lab URL.

- Change only the category parameter.
- Submit the request to the PortSwigger lab instance.
- Observe whether the response changes.
- Stop once the lab confirms completion and at least one unreleased product is visible.

Do not test this input on any other website.

## 5. Results

_To be completed after the lab._

- **Did the lab show an unreleased product?**
- **What input did you test?**
- **What changed in the response?**
- **Did the lab mark the exercise as solved?**
- **What evidence can be captured without exposing session data?**

## 6. Explain the finding

In your own words:

- **Root cause:**
- **Why the query could be changed:**
- **Potential impact:**
- **Primary mitigation:**

Hint: the core prevention is to use parameterized queries so the category is treated as data, not executable SQL syntax.

## 7. Lessons learned

_To be completed after the lab. Do not mark this report as complete until you have personally reproduced and understood the result._

## 8. References

- [PortSwigger lab brief and solution](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)
- [PortSwigger SQL injection learning path](https://portswigger.net/web-security/learning-paths/sql-injection)
- [OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
