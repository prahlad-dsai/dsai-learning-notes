# Programming Languages Reference

A self-contained reference for relearning the core ideas of Python, SQL, C, and the basics of web languages (HTML, CSS, JavaScript). Each topic explains what the concept is, shows the syntax, and lists common mistakes.

## Contents

1. [Python](#1-python)
2. [Python OOP](#2-python-oop)
3. [SQL / SQLite](#3-sql--sqlite)
4. [C](#4-c)
5. [Web Languages: HTML, CSS, JavaScript](#5-web-languages-html-css-javascript)
6. [Choosing the Right Language](#6-choosing-the-right-language)
7. [Debugging Reference](#7-debugging-reference)
8. [Project: API Data Explorer](#8-project-api-data-explorer)
---

# 1. Python

Python is a high-level, general-purpose programming language. Its syntax is readable, and its ecosystem contains major data-science and machine-learning libraries.

## 1.1 Running Python

Python code can be run interactively or from a `.py` file. A script is a text file containing Python statements.

```python
print("Hello, world!")
name = "Prahlad"
print(name)
```

- `print()` displays a value.
- Variables store references to values. Python does not require a type declaration before assigning a variable.

**Common mistakes**
- Do not name a file after a standard library or installed module (for example `matplotlib.py`) if you intend to import that module. The local file shadows it.
- Indentation is part of Python syntax.

## 1.2 Variables and Data Types

A variable is a name referring to a value. Common built-in types are `int`, `float`, `str`, `bool`, `list`, `tuple`, `dict`, and `set`.

```python
age = 19
marks = 85.5
name = "Prahlad"
passed = True
skills = ["Python", "SQL"]
```

Here `age` is an integer, `marks` a floating-point number, `name` a string, `passed` a Boolean, and `skills` a list.

**Common mistakes**
- Python is dynamically typed: the variable name itself does not carry a declared type.
- Use `type(x)` to inspect a value's type.

## 1.3 Input and Output

`input()` reads text from the user. `print()` displays values. Convert the input when you need a number.

```python
name = input("Name: ")
age = int(input("Age: "))
print("Hello", name)
print("Next year:", age + 1)
```

`input()` returns a string. `int()` converts the text to an integer before arithmetic.

**Common mistakes**
- `input()` does not automatically produce an integer.
- Do not add a string directly to an integer.

## 1.4 Operators

Arithmetic operators perform calculations, comparison operators produce Boolean results, and logical operators combine conditions.

```python
marks = 85
print(marks + 5)
print(marks >= 40)
print(marks >= 40 and marks <= 100)
```

`+` adds, `>=` compares, and `and` requires both conditions to be true.

**Common mistakes**
- Use `==` to test equality. `=` is assignment.
- Parentheses can make complex conditions easier to read.

## 1.5 Conditions

`if` / `elif` / `else` lets a program choose between paths based on conditions.

```python
marks = 72

if marks >= 85:
    grade = "A"
elif marks >= 70:
    grade = "B"
else:
    grade = "C"

print(grade)
```

Python uses indentation to define the blocks belonging to `if`, `elif`, and `else`.

**Common mistakes**
- A missing colon after a condition causes a syntax error.
- Keep indentation consistent.

## 1.6 Loops

Loops repeat a block of code. `for` is commonly used to iterate over a sequence or range. `while` repeats while a condition remains true.

```python
for i in range(5):
    print(i)

count = 3
while count > 0:
    print(count)
    count -= 1
```

`range(5)` produces 0 through 4. The `while` loop continues until `count > 0` becomes false.

**Common mistakes**
- The stop value of `range` is excluded.
- A `while` loop must eventually make its condition false, or it runs forever.

## 1.7 Strings

A string is a sequence of characters. Strings support indexing, slicing, searching, formatting, and many methods.

```python
name = "Prahlad"
print(name[0])
print(name[0:4])
print(name.upper())
print(f"Hello, {name}")
```

Indexing gets one character, slicing gets a portion, `upper()` returns a new string in upper case, and an f-string inserts values into text.

**Common mistakes**
- Strings are immutable: methods return new strings rather than changing the original in place.

## 1.8 Lists, Tuples, Dictionaries, Sets

Lists are ordered and mutable. Tuples are ordered and immutable. Dictionaries store key-value pairs. Sets store unique values.

```python
numbers = [10, 20, 30]
numbers.append(40)

point = (3, 5)

student = {"name": "Prahlad", "marks": 85}
print(student["marks"])

unique = {1, 2, 2, 3}
print(unique)
```

Choose the structure for the job: a list for an editable sequence, a tuple for fixed grouped values, a dictionary for key-value lookup, and a set for uniqueness.

**Common mistakes**
- Dictionary keys must be hashable.
- A set automatically removes duplicates.
- Do not confuse `[]` (list) with `{}` (dictionary or set).

## 1.9 Functions

A function packages reusable logic. Parameters receive inputs, and `return` sends a result back to the caller.

```python
def average(a, b):
    return (a + b) / 2

result = average(80, 90)
print(result)
```

`def` defines the function. `a` and `b` are parameters. `return` produces the function's result.

**Common mistakes**
- `return` is different from `print`: `return` gives a value back to the caller.
- Keep functions focused on one clear task when possible.

## 1.10 Scope

Scope describes where a name can be accessed. Local variables normally exist inside the function where they are created. Global names exist at module level.

```python
x = 10

def show():
    x = 20
    print(x)

show()
print(x)
```

The function prints its local `x` (20), while the outer `print` sees the global `x` (10).

**Common mistakes**
- Avoid excessive global state. Pass values into functions and return results when practical.
- Assigning to a name again discards what it held before. Two different things need two different names.

## 1.11 Files

File handling lets programs keep information beyond one run.

```python
with open("notes.txt", "w") as file:
    file.write("Python notes")

with open("notes.txt", "r") as file:
    text = file.read()

print(text)
```

`with` manages the file safely. `'w'` writes (and overwrites), `'r'` reads, and `'a'` appends.

**Common mistakes**
- Opening with `'w'` overwrites an existing file.
- Use `with` so files are closed automatically.

## 1.12 Exceptions

Exceptions represent runtime problems such as an invalid conversion or a missing file. `try` / `except` lets a program handle expected failures.

```python
try:
    age = int(input("Age: "))
except ValueError:
    print("Please enter a valid integer.")
```

Code in `try` is attempted. Matching exceptions are handled by `except`.

**Common mistakes**
- Do not use a bare `except` for everything. Catch the specific errors you expect.

## 1.13 Modules and Imports

A module is a Python file or package that provides reusable code.

```python
import math

print(math.sqrt(25))
```

`import` makes the module available. A module can contain functions, classes, and constants.

**Common mistakes**
- The name of a local file can accidentally shadow an installed module.

---

# 2. Python OOP

Object-oriented programming organizes code around objects that combine data and behavior.

## 2.1 Class and Object

A class is a blueprint. An object is an instance created from that blueprint.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def show(self):
        print(self.name, self.marks)

s1 = Student("Prahlad", 85)
s1.show()
```

`self` refers to the current object. `__init__` initializes its attributes.

## 2.2 Inheritance and `super()`

Inheritance lets a child class reuse or extend a parent class.

```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, marks):
        super().__init__(name)
        self.marks = marks
```

`super()` lets the child call functionality from its parent class.

## 2.3 Overriding and Polymorphism

A child class can redefine a method from its parent. Polymorphism means code can work with objects through a common interface while each object provides its own behavior.

```python
class Animal:
    def speak(self):
        print("Some sound")

class Dog(Animal):
    def speak(self):
        print("Bark")

animals = [Dog()]
for animal in animals:
    animal.speak()
```

---

# 3. SQL / SQLite

SQL (Structured Query Language) is used to define database structures, manipulate data, query data, and (depending on the database system) control access and transactions. SQLite is an embedded, file-based relational database engine.

## 3.1 SQL Command Categories

| Category | Purpose | Common commands |
| --- | --- | --- |
| DDL | Define or change database structure | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`* |
| DML | Change rows/data | `INSERT`, `UPDATE`, `DELETE` |
| DQL | Retrieve data | `SELECT` |
| DCL | Control access/permissions | `GRANT`, `REVOKE` |
| TCL | Manage transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

\*Support for specific commands varies by database system. SQLite in particular has a smaller feature set than server databases.

## 3.2 Creating a Table

```sql
CREATE TABLE students (
    id INTEGER,
    name TEXT,
    department TEXT,
    age INTEGER,
    marks REAL
);
```

`CREATE TABLE` defines columns and their declared types. Constraints such as `PRIMARY KEY`, `NOT NULL`, `UNIQUE`, `DEFAULT`, and `CHECK` can enforce rules.

## 3.3 SELECT, WHERE, ORDER BY, LIMIT

```sql
SELECT name, marks
FROM students
WHERE marks >= 70
ORDER BY marks DESC
LIMIT 5;
```

`FROM` chooses the source table, `WHERE` filters rows, `ORDER BY` sorts the result, and `LIMIT` restricts the number of returned rows.

## 3.4 Aggregates, GROUP BY, HAVING

```sql
SELECT department, AVG(marks) AS average_marks
FROM students
GROUP BY department
HAVING AVG(marks) >= 70;
```

Aggregate functions such as `COUNT`, `SUM`, `AVG`, `MAX`, and `MIN` summarize rows. `GROUP BY` creates groups. `HAVING` filters groups after aggregation.

## 3.5 CRUD

```sql
INSERT INTO students (id, name, marks)
VALUES (7, 'Anu', 82);

UPDATE students
SET marks = 90
WHERE id = 7;

DELETE FROM students
WHERE id = 7;
```

CRUD means Create, Read, Update, Delete. `INSERT`, `UPDATE`, and `DELETE` change data, while `SELECT` reads it.

> **Safety rule:** be extremely careful with `UPDATE` or `DELETE` without a `WHERE` clause. You may affect every row.

## 3.6 DISTINCT, Aliases, NULL, Wildcards, IN, BETWEEN, LIKE

```sql
SELECT DISTINCT department FROM students;

SELECT name AS student_name
FROM students;

SELECT *
FROM students
WHERE name LIKE 'A%';

SELECT *
FROM students
WHERE marks BETWEEN 70 AND 90;

SELECT *
FROM students
WHERE department IN ('CSE', 'ECE');

SELECT *
FROM students
WHERE marks IS NULL;
```

- `DISTINCT` removes duplicate result values.
- `AS` creates an alias.
- `NULL` represents missing or unknown data and is tested with `IS NULL` / `IS NOT NULL`.
- `LIKE` supports pattern matching: `%` matches any sequence of characters and `_` matches exactly one.
- `IN` tests membership.
- `BETWEEN` tests an inclusive range.

## 3.7 JOINs

```sql
SELECT students.name, departments.department_name
FROM students
INNER JOIN departments
ON students.department = departments.department_code;
```

A `JOIN` combines rows from related tables. `INNER JOIN` keeps matches. `LEFT JOIN` keeps all rows from the left table and matching rows from the right. Support for `RIGHT` / `FULL` joins depends on the database engine.

## 3.8 Table Aliases and Subqueries

```sql
SELECT s.name, d.department_name
FROM students AS s
JOIN departments AS d
ON s.department = d.department_code;

SELECT name
FROM students
WHERE marks > (
    SELECT AVG(marks)
    FROM students
);
```

Aliases shorten table names. A subquery is a query nested inside another query. It can return a scalar value, a list used with `IN`, or a derived table, depending on context.

## 3.9 CASE, EXISTS, COALESCE, Set Operations

```sql
SELECT name,
    CASE
        WHEN marks >= 85 THEN 'Excellent'
        WHEN marks >= 70 THEN 'Good'
        ELSE 'Needs Improvement'
    END AS performance
FROM students;

SELECT name
FROM students s
WHERE EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.department_code = s.department
);

SELECT COALESCE(marks, 0)
FROM students;
```

- `CASE` creates conditional output.
- `EXISTS` checks whether a related subquery returns at least one row.
- `COALESCE` returns the first non-`NULL` expression.
- Set operators (`UNION`, `UNION ALL`, `INTERSECT`, `EXCEPT`) combine or compare compatible query results.

## 3.10 DCL

DCL controls database permissions in systems that implement it. The core commands are `GRANT` and `REVOKE`.

```sql
GRANT SELECT ON students TO analyst;
REVOKE SELECT ON students FROM analyst;
```

This matters in shared, server-based database environments. It is not central to a single-user SQLite project.

## 3.11 TCL and Transactions

A transaction groups related database operations so they can be committed together or rolled back.

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE id = 2;

COMMIT;
```

`COMMIT` makes the transaction's changes permanent. `ROLLBACK` undoes uncommitted changes. `SAVEPOINT` creates an intermediate point within a transaction. Exact transaction syntax and features vary by database engine.

## 3.12 SQL Processing Mental Model

A useful simplified model for a grouped query is:

```
FROM / JOIN -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY -> LIMIT
```

This is the conceptual processing order, not the textual order in which SQL is written.

## 3.13 Using SQLite from Python

```python
import sqlite3

connection = sqlite3.connect("students.db")
cursor = connection.cursor()

cursor.execute("""
SELECT
    CASE
        WHEN marks >= 85 THEN 'Excellent'
        WHEN marks >= 70 THEN 'Good'
        ELSE 'Needs Improvement'
    END AS performance,
    COUNT(*) AS student_count
FROM students
GROUP BY performance;
""")

rows = cursor.fetchall()
```

`connect` opens (or creates) the database file, `execute` runs a query, and `fetchall` returns every result row as a list of tuples.

---

# 4. C

C is a compiled, low-level-oriented programming language.

## 4.1 Variables, Types, Conditions, Loops

```c
#include <stdio.h>

int main(void) {
    int marks = 85;

    if (marks >= 40) {
        printf("Pass\n");
    }

    for (int i = 0; i < 5; i++) {
        printf("%d\n", i);
    }

    return 0;
}
```

C requires type declarations such as `int marks`. Statements are generally terminated by semicolons. Blocks use braces.

## 4.2 Arrays and Strings

```c
int marks[5] = {80, 70, 90, 60, 85};
printf("%d\n", marks[0]);

char name[50] = "Prahlad";
printf("%s\n", name);
```

Array indexing starts at 0. C strings are character arrays terminated by a null character, `'\0'`.

## 4.3 Functions

```c
int add(int a, int b) {
    return a + b;
}

int main(void) {
    int result = add(3, 4);
    printf("%d\n", result);
    return 0;
}
```

A function has a return type, a name, a parameter list, and a body. `main` is the program entry point.

## 4.4 Structs

```c
struct Student {
    char name[50];
    int age;
    float marks;
};

struct Student s = {"Prahlad", 19, 85.0f};
```

A struct groups related fields of different types into one custom data type.

## 4.5 Pointers and Dynamic Memory

```c
int x = 10;
int *p = &x;
printf("%d\n", *p);
```

A pointer stores an address. `&` obtains an address. `*` dereferences a pointer to access the value at that address.

Dynamically allocated memory comes from the heap using functions such as `malloc`, `calloc`, and `realloc`, and is released with `free`.

```c
int *arr = malloc(5 * sizeof(int));
if (arr != NULL) {
    arr[0] = 10;
}
free(arr);
```

The pointer variable itself may live on the stack while the allocated array lives on the heap. Always free dynamically allocated memory when it is no longer needed.

**Stack vs heap:** the stack commonly stores automatic local variables and call frames. The heap is used for dynamically allocated memory.

## 4.6 File Persistence

```c
FILE *file = fopen("students.dat", "wb");
fwrite(&student, sizeof(student), 1, file);
fclose(file);
```

`fopen` opens a file, `fwrite` writes binary data, and `fclose` closes it. Reading can use `fread`. File persistence lets a program keep information between runs.

---

# 5. Web Languages: HTML, CSS, JavaScript

Learning order: **HTML, then CSS, then JavaScript.** Start with structure, then presentation, then behavior.

## 5.1 HTML

HTML (HyperText Markup Language) describes webpage structure and content. It is a markup language, not a general-purpose programming language.

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Profile</title>
</head>
<body>
    <h1>About Me</h1>
    <p>Hello, I am Prahlad.</p>
</body>
</html>
```

The doctype declares modern HTML. `html` is the root element. `head` contains metadata such as the title. `body` contains the visible page content. Elements commonly use opening and closing tags. Some, such as `br` and `hr`, are void elements with no closing tag.

## 5.2 CSS

CSS (Cascading Style Sheets) controls presentation: colors, fonts, spacing, sizing, layout, responsiveness, and more.

```css
p {
    font-size: 18px;
    margin: 10px;
}
```

`p` is the selector. The declarations inside the braces set properties and values.

## 5.3 JavaScript

JavaScript is a programming language commonly used in browsers to add behavior and interactivity. It can respond to events, manipulate the DOM, validate forms, fetch data, and more.

```javascript
const button = document.querySelector("#calculate");

button.addEventListener("click", function () {
    console.log("Clicked!");
});
```

`querySelector` finds an element. `addEventListener` registers code to run when an event occurs. JavaScript can modify HTML and CSS through the DOM.

---

# 6. Choosing the Right Language

| Need | Good starting tool |
| --- | --- |
| General programming | Python |
| Structured database queries | SQL |
| Embedded, lightweight database | SQLite |
| Low-level programming | C |
| Webpage structure | HTML |
| Webpage styling and layout | CSS |
| Webpage behavior and interactivity | JavaScript |

---

# 7. Debugging Reference

Debugging is the process of finding and fixing errors. Do not guess randomly: isolate the problem and inspect evidence.

| Problem | Typical cause | First check |
| --- | --- | --- |
| Syntax error | Invalid language syntax | Read the line and column in the error message |
| `NameError` | Name not defined, or a typo | Check spelling and scope |
| `TypeError` | Operation uses incompatible types | Inspect the types of the values |
| `FileNotFoundError` | Wrong path or working directory | Print the current directory and filename |
| SQL error | Invalid query, schema, or column | Run the query separately and inspect `.schema` and table names |

## A reliable debugging loop

1. Read the exact error.
2. Locate the first relevant line.
3. Inspect variables and types.
4. Reduce the problem to a small test.
5. Fix one thing at a time.
6. Re-run.
7. Add a test for the bug if it could return later.

> An error message is evidence, not an insult. Learn to use it.

---

# 8. Project: API Data Explorer

A browser-based application that retrieves posts from an external API, displays them through FastAPI and Jinja2, supports filtering and pagination, opens individual post details, and presents basic statistics.

- **Stack:** Python, FastAPI, `requests`, Jinja2, HTML, JSONPlaceholder API. CSS is the next stage.
- **Environment:** WSL/Linux, VS Code, project folder `/home/prahlad/API`, virtual environment `myenv`.
- **File rule:** work in `webapp.py` and `templates/`. Do not modify the older `main.py` or `lab9.py` projects.

## 8.1 Project Structure

```
API/
├── static/            # CSS files (being set up)
│   └── style.css
├── templates/
│   ├── index.html         # Posts list, filters, pagination, statistics
│   └── post_details.html  # Individual post page
├── webapp.py          # FastAPI application and routes
├── main.py            # Separate older project; leave unchanged
├── lab9.py            # Separate lab project; leave unchanged
└── myenv/             # Virtual environment
```

The `static/` folder and stylesheet are the planned CSS setup. They should exist once the CSS setup step is complete.

## 8.2 How the Application Works

```
JSONPlaceholder API
        |
        |  HTTP GET request (requests)
        v
FastAPI backend (webapp.py)
        |
        |  Python data + template context
        v
Jinja2 template (templates/*.html)
        |
        |  rendered HTML
        v
Browser
```

**Key distinction:** the API returns JSON. `response.json()` parses that JSON into normal Python data (here, a list of dictionaries). It does not create a JSON file.

## 8.3 Important Python and FastAPI Concepts

### HTTP request with `requests`

```python
response = requests.get(url, timeout=10)
response.raise_for_status()
data = response.json()
```

- `requests.get()` sends a GET request.
- `timeout=10` prevents waiting indefinitely.
- `raise_for_status()` raises an exception for unsuccessful HTTP status codes.
- `response.json()` parses the response body.

### Path parameters

```python
@app.get("/posts/{post_id}")
def post_details(request: Request, post_id: int):
    ...
```

The value in the URL, such as `/posts/4`, is passed into `post_id`. A path parameter identifies which resource to retrieve.

### Query parameters

```python
@app.get("/")
def home(
    request: Request,
    page: int = Query(1, ge=1),
    limit: int = Query(5, ge=5, le=50),
    user_id: int = Query(0, ge=0, le=10)
):
    ...
```

Query parameters control how a collection is shown, for example `/?page=2&limit=10&user_id=1`. `Query()` provides defaults and validation constraints.

### Template rendering

```python
return templates.TemplateResponse(
    request=request,
    name="index.html",
    context={
        "posts": posts,
        "page": page,
        "limit": limit,
        "user_id": user_id,
        "total_pages": total_pages,
        "total_posts": total_posts,
        "posts_per_user": posts_per_user
    }
)
```

The `context` dictionary passes Python variables into the Jinja2 template. In HTML, a value is displayed with `{{ variable }}`.

## 8.4 Fetching Posts and Separating Helper Logic

Keep the API-fetching helper separate from the route so the retrieval logic can be reused.

```python
def get_posts(limit, start, user_id=None):
    url = "https://jsonplaceholder.typicode.com/posts"
    params = {
        "_start": start,
        "_limit": limit,
    }
    if user_id is not None:
        params["userId"] = user_id

    response = requests.get(url, timeout=10, params=params)
    response.raise_for_status()
    total = int(response.headers.get("X-Total-Count"))
    return response.json(), total
```

- `_start` is the zero-based offset.
- `_limit` is the maximum number of posts returned.
- `userId` filters posts by owner.
- The response header `X-Total-Count` supplies the total matching count for pagination.

**Why `params=`?** Passing a dictionary through `params` lets the `requests` library construct and encode the query string safely.

## 8.5 Filtering and Pagination

```python
start = (page - 1) * limit
posts, total = get_posts(
    limit,
    start,
    user_id if user_id != 0 else None
)
total_pages = (total + limit - 1) // limit
```

The first line converts a human-friendly page number (starting at 1) into the API's zero-based offset. The last line performs ceiling division using integer arithmetic.

**Example:** page 3 with 10 posts per page gives `start = (3 - 1) * 10 = 20`, so the API starts at the 21st matching item.

**All Users convention:** the dropdown uses `user_id=0` to mean "no user filter". The helper receives `None` in that case, so the API returns posts from all users.

**Validation:** `page` must be at least 1, `limit` is constrained to the dropdown range (5 to 50), and the user ID is 0 to 10.

### Filter form

Use **one** GET form containing both dropdowns. When Apply is submitted, the selected values are sent as query parameters. Selected options are preserved with Jinja2 conditions.

```html
<select name="limit" id="limit">
    <option value="5" {% if limit == 5 %}selected{% endif %}>5</option>
    ...
</select>
```

### Pagination links must preserve filters

```html
{% if page > 1 %}
    <a href="/?page={{ page - 1 }}&limit={{ limit }}&user_id={{ user_id }}">
        Previous
    </a>
{% endif %}

<span>Page {{ page }} of {{ total_pages }}</span>

{% if page < total_pages %}
    <a href="/?page={{ page + 1 }}&limit={{ limit }}&user_id={{ user_id }}">
        Next
    </a>
{% endif %}
```

- Use `page - 1` for Previous and `page + 1` for Next.
- The condition for Next is `page < total_pages`.
- Including `limit` and `user_id` keeps the current selection while navigating.

**Variable-name warning:** use distinct names inside statistics loops (such as `stat_user_id`) so they do not overwrite the selected filter variable `user_id`. A name is just a label, and assigning to it again discards what it held before.

## 8.6 Individual Post Details

Clicking a post title opens a dedicated page at `/posts/{post_id}`.

```python
@app.get("/posts/{post_id}")
def post_details(request: Request, post_id: int):
    url = f"https://jsonplaceholder.typicode.com/posts/{post_id}"
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    post = response.json()

    return templates.TemplateResponse(
        request=request,
        name="post_details.html",
        context={"post": post}
    )
```

**Important:** the route needs `request: Request` because the template response uses `request=request`. Leaving it out caused a `NameError`.

On `index.html`, make the title link to the detail route:

```html
{% for post in posts %}
    <h3>
        <a href="/posts/{{ post.id }}">{{ post.title }}</a>
    </h3>
    <p>{{ post.body }}</p>
{% endfor %}
```

The details template can display `post.id`, `post.userId`, `post.title`, and `post.body`. A link with `href="/"` returns to the posts list.

## 8.7 Statistics

### Total posts

Fetch the complete posts collection, parse it, then count the list. Store it in its **own variable** (here `all_posts`) so it does not overwrite the paginated `posts` that the page displays.

```python
response = requests.get(
    "https://jsonplaceholder.typicode.com/posts",
    timeout=10
)
response.raise_for_status()
all_posts = response.json()
total_posts = len(all_posts)
```

`len(all_posts)` counts the list items. `len(response)` would not work, because `response` is a `requests` Response object and not the list of post dictionaries.

### Posts per user

Count occurrences of each `userId` with a dictionary.

```python
posts_per_user = {}
for post in all_posts:
    stat_user_id = post["userId"]
    if stat_user_id in posts_per_user:
        posts_per_user[stat_user_id] += 1
    else:
        posts_per_user[stat_user_id] = 1
```

Dictionary keys are user IDs and values are post counts. `+= 1` increments the existing count. Writing `= 1` on every occurrence would keep resetting the count.

### Display the statistics in Jinja2

```html
<p>Total Posts: {{ total_posts }}</p>

<h2>Posts per User</h2>
{% for stat_user_id, count in posts_per_user.items() %}
    <p>User {{ stat_user_id }}: {{ count }} posts</p>
{% endfor %}
```

The statistics dictionary is passed through the route's template context. `.items()` yields key-value pairs for the loop.

**Design choice:** the statistics describe the full API dataset, even when the posts list is filtered to one user. This keeps the overview independent of the current list filter.

## 8.8 Jinja2 and HTML Reference

| Purpose | Syntax |
| --- | --- |
| Output a variable | `{{ value }}` |
| Conditional | `{% if condition %} ... {% endif %}` |
| Loop | `{% for item in items %} ... {% endfor %}` |
| HTML link | `<a href="/path">Visible text</a>` |
| GET form | `<form method="get">` sends its named control values in the URL as query parameters |

For a link, `href` is the destination, and the text between the tags is what the user clicks.

## 8.9 CSS Setup (Next Step)

Mount a static directory in `webapp.py`:

```python
from fastapi.staticfiles import StaticFiles

app = FastAPI()
app.mount(
    "/static",
    StaticFiles(directory="static"),
    name="static"
)
```

Create `static/style.css`. In the `<head>` of both HTML templates, link it with:

```html
<link rel="stylesheet"
      href="{{ url_for('static', path='/style.css') }}">
```

This mounts the local `static` directory at `/static` and lets Starlette/FastAPI generate the stylesheet URL. The CSS file itself has not yet been written or tested.

## 8.10 Project Progress

| Feature | Status |
| --- | --- |
| API fetch and display | Finished |
| Pagination | Finished |
| Posts-per-page selection | Finished |
| User ID filtering | Finished |
| Filter preservation during pagination | Implemented; re-test after recent template changes |
| Individual post details page | Finished |
| Total posts statistic | Implemented and confirmed working |
| Posts-per-user calculation and display | Implemented; final end-to-end check still to do |
| CSS static-file setup | Next step; not yet confirmed |
| CSS visual styling | Not started |

## 8.11 Running and Troubleshooting

```bash
# Activate the project environment (from API/)
source myenv/bin/activate

# Run the FastAPI app
uvicorn webapp:app --reload
```

Open the local development address shown by Uvicorn in your browser.

When debugging, read the terminal traceback from the bottom upward and identify the final exception and the line in your own code. For an HTTP 500, inspect the server traceback and don't guess.

**Imports used in this project:**

```python
from fastapi import FastAPI, Query
from fastapi.templating import Jinja2Templates
from starlette.requests import Request
from fastapi.staticfiles import StaticFiles
import requests
```

In this environment, importing `Request` from `starlette.requests` resolved a forward-reference issue. Keep `import requests` separate, since it is the HTTP client library.

## 8.12 Verification Checklist

- [ ] Open the homepage and confirm posts render.
- [ ] Change posts per page and apply. Confirm the number of displayed posts changes.
- [ ] Choose a user. Confirm only that user's posts appear.
- [ ] Navigate forward and backward. Confirm the page number and filters remain correct.
- [ ] Click a post title. Confirm its ID, user ID, title, and body appear.
- [ ] Use Back to Posts. Confirm the homepage opens.
- [ ] Confirm Total Posts displays 100 for the full JSONPlaceholder dataset.
- [ ] Confirm Posts per User shows the expected counts for all users.
- [ ] After CSS setup, inspect both the homepage and post details page for stylesheet loading.
