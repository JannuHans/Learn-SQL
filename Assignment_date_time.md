## 1. Function to find out which day of the week it was from a given date?

SELECT TO_CHAR(DATE '2026-06-10', 'Day') AS day_name;
```sql
SELECT TO_CHAR(DATE '2026-06-10', 'Day') AS day_name;

```

## 2. what is epoch?

## Definition

Epoch is the number of seconds that have elapsed since:

```text
1970-01-01 00:00:00 UTC
```

This date and time is known as the **Unix Epoch**.

---

## Convert Timestamp to Epoch

```sql
SELECT EXTRACT(EPOCH FROM TIMESTAMP '2026-06-10 12:00:00');
```

### Output

```text
1781092800
```

This means:

```text
2026-06-10 12:00:00 UTC
```

is 1,781,092,800 seconds after:

```text
1970-01-01 00:00:00 UTC
```