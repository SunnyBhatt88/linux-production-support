# SQL Troubleshooting

## Problem

Application issues can sometimes be related to database connectivity, incorrect SQL queries, missing data, slow queries, or database-related errors.

## Step 1: Check Database Connectivity

Verify whether the application is able to connect to the database.

Check the application logs for database connection errors:

```bash
grep -i "database" application.log
```

Search for connection-related errors:

```bash
grep -i "connection" application.log
```

## Step 2: Check SQL Query

Review the SQL query reported by the application or development team.

Example:

```sql
SELECT order_id, order_status
FROM orders
WHERE order_id = 12345;
```

Verify:

* Table name
* Column names
* WHERE condition
* Data type
* Expected result

## Step 3: Check Record Availability

Verify whether the required record exists in the database.

```sql
SELECT *
FROM orders
WHERE order_id = 12345;
```

If no record is returned, investigate whether the record was created successfully or whether there is an upstream processing issue.

## Step 4: Check Multiple Records

Use SQL queries to investigate related records.

```sql
SELECT order_id, order_status, created_date
FROM orders
WHERE order_id = 12345;
```

You can also check recent records:

```sql
SELECT order_id, order_status, created_date
FROM orders
ORDER BY created_date DESC;
```

## Step 5: Check for Duplicate Records

Duplicates can sometimes cause application processing issues.

```sql
SELECT order_id, COUNT(*)
FROM orders
GROUP BY order_id
HAVING COUNT(*) > 1;
```

## Step 6: Check NULL or Missing Values

Check whether important fields contain NULL values.

```sql
SELECT *
FROM orders
WHERE customer_id IS NULL;
```

This can help identify incomplete or unexpected data.

## Step 7: Check Query Performance

For slow SQL queries, review the execution plan where permitted.

For Oracle:

```sql
EXPLAIN PLAN FOR
SELECT *
FROM orders
WHERE order_id = 12345;
```

Then review the execution plan using the appropriate database tools.

## Step 8: Troubleshooting Approach

1. Understand the reported application issue.
2. Identify the affected transaction or order ID.
3. Check application logs.
4. Verify database connectivity.
5. Validate the SQL query.
6. Check whether the required records exist.
7. Check for duplicate or missing data.
8. Review query performance if required.
9. Identify the probable root cause.
10. Coordinate with the DBA or application team when required.
11. Retest the application after the issue is resolved.
12. Document the incident and resolution.

## Resolution

After the corrective action has been completed, verify that the application can successfully process the transaction.

Re-run the appropriate SELECT query and confirm that the expected data is available.

## Production Support Best Practices

* Use SELECT queries for investigation whenever possible.
* Do not execute UPDATE or DELETE statements in production without proper authorization.
* Never expose database passwords or credentials in GitHub.
* Do not publish real customer or production data.
* Use sample data in documentation and examples.
* Capture transaction IDs when investigating application issues.
* Coordinate with the DBA team for database-level issues.
* Document the root cause and resolution.

## Key SQL Commands

```sql
SELECT
WHERE
JOIN
GROUP BY
ORDER BY
HAVING
COUNT()
```

## Key Skills Demonstrated

* SQL Troubleshooting
* Database Investigation
* Application Support
* Incident Analysis
* Data Validation
* Root Cause Analysis
