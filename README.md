# SQL Style Guide

__*Above all other rules, Rule #1: Be consistent.*__

### Keywords are in all CAPS.  Non-keywords are in all lowercase.

There is a structure to SQL queries that we rely on for comprehension.  Bolding the keywords, which mark the different components of a query, make it easier to decompose.

```sql
SELECT [fieldnames]
FROM [tablenames]
WHERE [condition1]
AND [condition2]
ORDER BY;
```

### First SELECT element is on own line with 1 space indent.  Subsequent elements are preceeded with a comma.

```sql
SELECT
 field1
 , field2
 , field3
FROM ...
```

### Nested statements are indented 4 spaces.

```sql
SELECT *
FROM [table1]
INNER JOIN (
	SELECT
	 field1
	FROM ...
) tab2 ON ()

```

### Join condition is on a single line if possible and enclosed in parentheses.

```sql
SELECT *
FROM table1
INNER JOIN table2 ON (table1.pk = table2.fk)
```

### Similar joins listed in alpha order where possible.

I really only sort in alpha order within clusters of tables/joins.  This ends up being limited to just the lookup tables as the order of the more important tables are dictacted by how the data is stored in the database.

```sql
SELECT *
FROM main_table
LEFT OUTER JOIN lookup_alpha ON ()
LEFT OUTER JOIN lookup_beta ON ()
```