Below is the implementation of the stored procedure `proc_Grade` and a PL/SQL block to use it:

```sql
-- Stored Procedure: proc_Grade
create OR REPLACE PROCEDURE proc_Grade (
    name_in  IN VARCHAR2,
    marks_in IN NUMBER,
    class_out OUT VARCHAR2
) AS
BEGIN
    IF marks_in >= 990 AND marks_in <= 1500 THEN
        class_out := 'Distinction';
    ELSIF marks_in >= 900 AND marks_in <= 989 THEN
        class_out := 'First Class';
    ELSIF marks_in >= 825 AND marks_in <= 899 THEN
        class_out := 'Higher Second Class';
    ELSE
        class_out := 'not Classified';
    END IF;
END proc_Grade;
/

-- PL/SQL Block to use the procedure
DECLARE
    v_name   VARCHAR2(100);
    v_marks  NUMBER;
    v_class  VARCHAR2(100);
BEGIN
    -- Assuming 'Stud_Marks' is the table where student marks are stored
    -- Here, you would replace 'Stud_Marks' with the actual table name
    
    -- Fetching student's name and marks from Stud_Marks table
    select name, total_marks into v_name, v_marks
    from Stud_Marks
    where name = 'John'; -- Replace 'John' with the desired student's name
    
    -- Calling the stored procedure to determine the class
    proc_Grade(v_name, v_marks, v_class);
    
    -- Inserting the result into the Result table
    insert into Result (Roll, Name, Class)
    values (1, v_name, v_class); -- Assuming Roll number is 1 for simplicity
    COMMIT;
    
    DBMS_OUTPUT.PUT_LINE('Student ' || v_name || ' has been classified as ' || v_class);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Student not found!');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```

This PL/SQL block fetches the student's name and marks from the `Stud_Marks` table, calls the `proc_Grade` procedure to determine the class based on the marks, inserts the result into the `Result` table, and handles exceptions if any occur. You may need to adjust it based on your specific table structures and requirements.