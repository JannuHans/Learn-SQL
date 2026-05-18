### Assignment 1 - Transaction Management at Scale

## Problem Statement

A nightly billing job needs to update 1 million records.  
It crashed midway last week and the entire job had to restart from scratch.

Write a SQL script that commits 1 million transactions efficiently.  
Your script should handle failures gracefully so the entire job never needs to restart from zero.

---

## My Approach

I will solve this problem by not updating all 1 million records at one time. I will divide the records into small batches like 10,000 records.
After every batch update, I will use COMMIT so the changes get saved permanently. If the system crashes, only the current batch will be affected, not the whole process.
I will also maintain a checkpoint table where I store the last updated record ID. So when the job starts again, it can continue from the last saved point instead of starting from zero.

If any error happens during a batch update, I will use `ROLLBACK` to undo only that batch transaction.

---

## Solution

```sql
CREATE TABLE billing (
    id INT PRIMARY KEY,
    status VARCHAR(20)
);

CREATE TABLE checkpoint (
    last_id INT
);

INSERT INTO checkpoint VALUES (0);

DELIMITER $$

CREATE PROCEDURE update_records()
BEGIN

    DECLARE start_id INT;
    DECLARE batch_size INT DEFAULT 10000;

    SELECT last_id INTO start_id
    FROM checkpoint;

    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        ROLLBACK;
    END;

    WHILE start_id < 1000000 DO

        START TRANSACTION;

        UPDATE billing
        SET status = 'PAID'
        WHERE id > start_id
        AND id <= start_id + batch_size;

        UPDATE checkpoint
        SET last_id = start_id + batch_size;

        COMMIT;

        SET start_id = start_id + batch_size;

    END WHILE;

END $$

DELIMITER ;

CALL update_records();
```