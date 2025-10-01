This is created by Manan Khandelwal. 
Sap ID : 590014164 
Batch : 01

About this code:
It’s a SQL Query Simulator built entirely in HTML + CSS + JavaScript.
It doesn’t connect to a real database (like MySQL/Oracle/Postgres).
Instead, it uses JavaScript arrays of objects (in-memory tables).
You can type SQL-like queries (a safe subset) and see results instantly.
It also shows parsed clauses (EXPLAIN PLAN) for understanding how queries work.
👉 In short: This is an educational web app for learning SQL queries without needing a database server.

⚙️ What it is doing (step by step)
1. HTML Structure
<header> → Title and “Load Sample Queries” button.
<main> → The main query editor:
A textarea for typing SQL queries.
Buttons: Run, Explain Plan, Clear.
Output area for results (#output).
JSON output view (#resultJson).
<aside> → Sidebar:
Shows available tables (employees, customers, etc.) from memory.
Quick SQL examples you can copy.
<footer> → Disclaimer that it’s limited and for learning.

2. CSS Styling
Uses a clean, light theme with blue accents.
.card → box-style sections for input/output.
textarea.query → styled like a SQL editor.
pre.res → dark background block to show JSON results.
table → simple grid with borders for query results.

3. Table Viewer
Dropdown lets you choose which table (employees, orders, etc.).
JavaScript renders the selected table as an HTML <table> in the sidebar.

4. Query Execution
The real “engine” is in functions like runSQL(), execSingle(), and helpers.
It supports:
SELECT … FROM table
WHERE filters
GROUP BY with aggregates (COUNT, SUM, AVG, MIN, MAX)
HAVING conditions on groups
ORDER BY sorting
UNION / INTERSECT / EXCEPT (set operations)
Simple nested subqueries with IN (SELECT …)

5. Safe Evaluation
Conditions (WHERE salary > 3000) are parsed into JavaScript expressions.
A “safe eval” mechanism (safeEvalExpr) is used to prevent malicious code.
Only limited SQL subset is allowed (no DROP TABLE, no injections).

6. Result Display
Query results are shown in two formats:
HTML Table (rows and columns).
JSON ([ { dept:"IT", cnt:2, avg_sal:52500 }, ... ]) for developers.

7. Sample Queries
Button “Load Sample Queries” preloads an example query into the editor.
Sidebar shows more quick examples like:
Select employees in IT dept.
Group salaries by department.
Subquery with IN.
UNION between employees and contractors.

🧑‍🎓 Why this is generated
This project was clearly made for learning and practicing SQL without a real database.
Beginners often struggle setting up MySQL/Oracle.
Teachers want a safe, browser-only sandbox.
Students can type queries → instantly see results → understand SQL logic.
Since data is small & in-memory, it’s fast and safe.
👉 It’s like a mini SQL engine inside your browser.

🔍 How it works internally
User types SQL query.
runSQL() is called.
It checks if query has set operations (UNION, INTERSECT, etc.).
Otherwise, execSingle() parses the query:
Extracts SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY.
Filters rows (WHERE).
Groups rows (GROUP BY).
Computes aggregates (COUNT, AVG, …).
Applies HAVING.
Sorts results (ORDER BY).
Results are returned as an array of objects.
UI renders results in both table and JSON form.

Summary:
What it is: A browser-based SQL simulator.
What it does: Runs a subset of SQL queries on in-memory JS objects, shows results & explanations.
Why generated: For teaching/learning SQL without installing databases.
How it works: JavaScript parses SQL → applies conditions/grouping/aggregates → renders output.
