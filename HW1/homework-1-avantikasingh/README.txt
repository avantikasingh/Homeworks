Design Approach:

The ER diagram is intented to be as simple as possible. 
The software is called Covid Tracing System but there are no entites to store the alerts or traces of contact. 
This is intentional to ensure minimum data redundancy and ensure future scalabilityy of the system.

Explanation on how some of the functionalities/features from the problem statement can be achieved from the proposed ER diagram:

1. TEST_RESULT:

test_reason is an enum variable which will store why the test was taken. The values are:
    i.  chosen randomly on office premise
    ii. fever
    iii. self-report
    iv. notified by system 

test_facility will hold information on whether the test was conducted on-premise or outside in some other medical centre

test_result will hold whether the test outcome was positive or negative

2. SICK_STATUS

here, 'status' attribute is enum which values:
    i. well
    ii. hospitalised
    iii. sick 
    iv. deceased

3. When 'test_result' is positive

- employee_id is fetched for the employee who tested positive.
- all meeting_record are fetched where this employee was a participant within the last 2 weeks (let's assume)
- all other employees who were a part of these meeting_record can be notified and they can go for testing. 
  Their test result will be stored in TEST_RESULT table with test_reason as 'notified by system'
- a list of floor numbers of all meeting_record can be gathered and employees who work at these floors will also be notified for optional testing.
  Employees working in each floor can be filtered out easily since the COVID_TRACING_SYSTEM table has information about the floor number that an employee works at.

- If any further employee is tested positive, the same steps is followed

4. Once an employee is tested positive

- the employee can report is status and the data is recorded in the SICK_STATUS table.

5. All other mandatory procedures like returning back to work after 2 weeks of no symptom or taking mandatory test after direct contact can be achieved via other features on the app.
The databse design should not be inspired by these operational or business rules since that would require more constraints and rigid primary keys.
There could come a scenario where any operational level change cannot be handled with the present DB design hence the databse design would then fail.
