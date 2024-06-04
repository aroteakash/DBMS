Sure, here's an example of a database trigger written in PL/SQL for Oracle that tracks updates and deletes on the `Library` table and logs the old values into the `Library_Audit` table:

```sql
create OR REPLACE TRIGGER library_audit_trigger
BEFORE DELETE OR UPdate ON Library
FOR EACH ROW
DECLARE
    operation_type VARCHAR2(10);
BEGIN
    IF DELETING THEN
        operation_type := 'DELETE';
        insert into Library_Audit (book_id, book_title, author, operation_type, operation_date)
        values (:OLD.book_id, :OLD.book_title, :OLD.author, operation_type, SYSdate);
    ELSIF UPDATING THEN
        operation_type := 'UPdate';
        insert into Library_Audit (book_id, book_title, author, operation_type, operation_date)
        values (:OLD.book_id, :OLD.book_title, :OLD.author, operation_type, SYSdate);
    END IF;
END;
/
```

### Explanation:

1. **Trigger Creation**: This creates a trigger named `library_audit_trigger` on the `Library` table.
2. **Trigger Timing**: It is defined as a `BEFORE DELETE OR UPdate` trigger, meaning it fires before any delete or update operation on the `Library` table.
3. **FOR EACH ROW**: This specifies that the trigger should execute once for each row affected by the DELETE or UPdate operation.
4. **Operation Check**: The trigger checks whether the operation is a DELETE or UPdate using the `DELETING` and `UPDATING` conditionals.
5. **Logging**: If the operation is a DELETE or UPdate, the trigger inserts the old values (`:OLD`) of the `book_id`, `book_title`, and `author` columns into the `Library_Audit` table, along with the operation type (`DELETE` or `UPdate`) and the current date (`SYSdate`).
6. **Commit**: This trigger doesn't require a commit as it's a `BEFORE` trigger and any changes will automatically be committed when the triggering action is committed.

Ensure that the `Library_Audit` table has columns corresponding to `book_id`, `book_title`, `author`, `operation_type`, and `operation_date`. Adjust the column names and datatypes as per your actual table structure.