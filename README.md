# -AUCA-System-Access-Policy-

AUCA PL/SQL Triggers & Package Project

Done by:
Paule Céleste 27086
Khadidja Adam 28041
Ingabire Bienvenu 24000

⸻

🔎 1. Objective of the Assignment

This project contains our group’s solution to two PL/SQL scenarios:

⸻

A. Scenario 1 — AUCA System Access Policy (Triggers)

Based on the given scenario, we needed to implement:
	•	A mechanism to block system access during:
	•	Weekends (Saturday & Sunday)
	•	Weekdays outside 08:00–17:00
	•	A second trigger that records every violation attempt for auditing.

The scenario provided in class described the business rules clearly, and our solution implements them using Oracle database triggers.

⸻

B. Scenario 2 — HR Employee Management Package

We were asked to design an HR employee salary management package containing:
	•	A function that computes RSSB tax and net salary
	•	A dynamic SQL procedure capable of updating or inserting employee salary data
	•	Correct use of:
	•	USER
	•	CURRENT_USER
	•	Definer rights
	•	Invoker rights

Sample calls and demonstrations are included.

⸻

🛠️ 2. How We Implemented the Solution

⸻

A. Triggers

✔ Trigger 1 — Block Unauthorized Access
	•	Checks current day and time
	•	If action occurs outside allowed time, it raises an application error
	•	Prevents the DML operation (insert/update/delete)

✔ Trigger 2 — Log Violations
	•	Uses an autonomous transaction
	•	Inserts information into a log table:
	•	Username
	•	Operation type
	•	Exact timestamp
	•	Target table

This ensures that even blocked attempts leave an audit trail.

⸻

B. HR Employee Management Package

✔ Function: calculate_net_salary
	•	Calculates RSSB tax (3%)
	•	Returns net salary after deductions
	•	Includes comments explaining the formula

✔ Procedure: update_salary_dynamic
	•	Uses EXECUTE IMMEDIATE
	•	Allows dynamic update of any employee’s salary
	•	Demonstrates dynamic SQL correctly

✔ Security Context Demonstrated
We illustrated:
	•	USER = schema owner executing the code
	•	CURRENT_USER = invoker when using invoker rights
	•	How definer/invoker rights affect table access

*5. How to Run This Project*
	1.	Run access_log_table.sql
	2.	Run trg_block_unauthorized_access.sql
	3.	Run trg_log_violations.sql
	4.	Compile the package (emp_mgmt_pkg_spec.sql + emp_mgmt_pkg_body.sql)
	5.	Execute examples.sql to test everything

7. *Group Member Contributions*

Paule
	•	Wrote Trigger 1 (access blocking)
	•	Tested time/day restrictions
	•	Generated screenshots (block + allowed)
	•	Added comments on time validation

Khadidja
	•	Wrote Trigger 2 (logging violations)
	•	Created & tested access_log table
	•	Generated screenshots (log results)
	•	Added comments on autonomous transactions

Bienvenu
	•	Wrote the HR package (spec & body)
	•	Created dynamic SQL procedure
	•	Generated screenshots (package, salary calc, dynamic updating)
	•	Added comments on USER / CURRENT_USER and rights
