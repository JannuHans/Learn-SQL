# PostgreSQL JSONB Flattening Assignment

## Problem Statement

Store raw API JSON data in one PostgreSQL table and flatten the JSON data into a relational table for reporting and analytics.

---

## Source Table (Raw JSON Data)

```sql
CREATE TABLE api_data (
    id SERIAL PRIMARY KEY,
    payload JSONB
);

INSERT INTO api_data (payload)
VALUES
('{
    "sale_id": 11,
    "rep_name": "Rohan Bajaj",
    "department": "Engineering",
    "city": "Hyderabad",
    "amount": 78000,
    "status": "open"
}'),
('{
    "sale_id": 12,
    "rep_name": "Pooja Iyer",
    "department": "HR",
    "city": "Chennai",
    "amount": 44000,
    "status": "open"
}');

SELECT * FROM api_data;
```

---

## Target Table (Flattened Data)

```sql
CREATE TABLE sales (
    sale_id INT,
    rep_name TEXT,
    department TEXT,
    city TEXT,
    amount NUMERIC,
    status TEXT
);
```

---

## Flatten JSON Object Using jsonb_to_record()

```sql
SELECT *
FROM api_data,
jsonb_to_record(payload)
AS x(
    sale_id INT,
    rep_name TEXT,
    department TEXT,
    city TEXT,
    amount NUMERIC,
    status TEXT
);
```


## Insert Flattened Data into Target Table

```sql
INSERT INTO sales
(
    sale_id,
    rep_name,
    department,
    city,
    amount,
    status
)
SELECT
    x.sale_id,
    x.rep_name,
    x.department,
    x.city,
    x.amount,
    x.status
FROM api_data,
jsonb_to_record(payload)
AS x(
    sale_id INT,
    rep_name TEXT,
    department TEXT,
    city TEXT,
    amount NUMERIC,
    status TEXT
);
```

## Verify Data

```sql
SELECT * FROM sales;
```

