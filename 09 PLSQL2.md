Certainly! Below is an example of a PL/SQL block that uses a parameterized cursor to merge data from a newly created table `N_RollCall` with an existing table `O_RollCall`. If a record from `N_RollCall` already exists in `O_RollCall`, it will be skipped.

For this example, let's assume both tables have the same structure with the following columns: `id`, `student_name`, and `attendance_date`.

```sql
DECLARE
  CURSOR new_rollcall_cursor IS
    select id, student_name, attendance_date
    from N_RollCall;

  v_id N_RollCall.id%TYPE;
  v_student_name N_RollCall.student_name%TYPE;
  v_attendance_date N_RollCall.attendance_date%TYPE;

  -- Exception handling for duplicate keys
  duplicate_record EXCEPTION;
  PRAGMA EXCEPTION_INIT(duplicate_record, -00001);
  
BEGIN
  -- Open the cursor and loop through each record
  OPEN new_rollcall_cursor;
  LOOP
    FETCH new_rollcall_cursor into v_id, v_student_name, v_attendance_date;
    EXIT WHEN new_rollcall_cursor%notFOUND;
    
    -- Merge operation using insert
    BEGIN
      insert into O_RollCall (id, student_name, attendance_date)
      values (v_id, v_student_name, v_attendance_date);
    EXCEPTION
      WHEN duplicate_record THEN
        -- Handle duplicate record, here we just skip it
        null;
    END;
  END LOOP;
  
  -- Close the cursor
  CLOSE new_rollcall_cursor;
  
  -- Optional: Commit the transaction if not in an autonomous transaction
  COMMIT;
  
  DBMS_OUTPUT.PUT_LINE('Data merge completed successfully.');

EXCEPTION
  WHEN OTHERS THEN
    -- Rollback in case of any other errors
    ROLLBACK;
    DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```

### Explanation:
1. **Cursor Declaration**: The cursor `new_rollcall_cursor` selects all records from the `N_RollCall` table.
2. **Cursor Variables**: Variables `v_id`, `v_student_name`, and `v_attendance_date` are declared to hold the values fetched by the cursor.
3. **Cursor Loop**: The cursor is opened, and a loop fetches each record from `N_RollCall`.
4. **Insert Operation**: Each fetched record is attempted to be inserted into `O_RollCall`.
5. **Exception Handling**: If a `duplicate_record` exception is raised (due to a unique constraint violation), the exception block will catch it and simply skip the insertion for that record.
6. **Commit**: The transaction is committed after processing all records.
7. **Exception Handling**: If any other error occurs, the transaction is rolled back, and an error message is printed.

This script assumes that `id` is a unique key in both tables. Adjust the structure and keys based on your actual table definitions.