## Even or Odd

**SQL Notes:**

You will be given a table, `numbers`, with one column `number`.


Return a table with a column `is_even` containing "Even" or "Odd" depending on `number` column values.

*numbers table schema*
* number INT

*output table schema*

* is_even STRING


**My solutions:**
  
```sql
SELECT 
CASE
  WHEN number % 2 = 0 THEN 'Even'
    ELSE 'Odd'
END AS is_even
FROM numbers;
```

```sql
Select
case
  when mod(number,2) = 0 then 'Even'
  when mod(number,2) != 0 then 'Odd'
end as is_even
from numbers; 
```
