# Testing, Error Logs, & Reflection -- Task 2

## Test 1: Attempt to insert a student without `first_name`

**SQL attempted:**

``` sql
INSERT INTO club_members (last_name, email, major, join_date)
VALUES ('Smith', 'john.smith@university.edu', 'Physics', '2025-03-15');
```

**Exact PostgreSQL error:**

``` text
ERROR:  null value in column "first_name" of relation "club_members" violates not-null constraint
Failing row contains (2, null, Smith, john.smith@university.edu, Physics, 2025-03-15). 

SQL state: 23502
Detail: Failing row contains (2, null, Smith, john.smith@university.edu, Physics, 2025-03-15).
```

**Why it was rejected:** The `first_name` column has `NOT NULL`, so
omitting it from the INSERT causes PostgreSQL to try inserting `NULL`,
which violates the constraint.

------------------------------------------------------------------------


## Test 2: Attempt to insert a student without `email`

**SQL attempted:**

``` sql
INSERT INTO club_members (first_name, last_name, major, join_date)
VALUES ('Jane', 'Doe', 'Mathematics', '2025-03-16');
```

**Exact PostgreSQL error:**

``` text
ERROR:  null value in column "email" of relation "club_members" violates not-null constraint
Failing row contains (3, Jane, Doe, null, Mathematics, 2025-03-16). 

SQL state: 23502
Detail: Failing row contains (3, Jane, Doe, null, Mathematics, 2025-03-16).
```

**Why it was rejected:** The `email` column has `NOT NULL`, so omitting
it triggers the same constraint violation as Test 1.

------------------------------------------------------------------------

## Test 3: Attempt to manually insert a `member_id` 

**SQL attempted:**

``` sql
INSERT INTO club_members (member_id, first_name, last_name, email, major, join_date)
VALUES (100, 'Chris', 'Evans', 'chris@university.edu', 'Film', '2025-03-18');
```

**Exact PostgreSQL error:**

``` text
ERROR:  cannot insert a non-DEFAULT value into column "member_id"
Column "member_id" is an identity column defined as GENERATED ALWAYS. 

SQL state: 428C9
Detail: Column "member_id" is an identity column defined as GENERATED ALWAYS.
Hint: Use OVERRIDING SYSTEM VALUE to override.
```

**Why it was rejected:** The `member_id` column is defined as
`GENERATED ALWAYS AS IDENTITY`, meaning PostgreSQL automatically
generates the value and does not allow manual inserts.

------------------------------------------------------------------------

## Error 1: Attempt to insert `first_name` without adding `first_name` in it to `INSERT INTO`

**SQL attempted:**

``` sql
INSERT INTO club_members (last_name, email, major, join_date)
VALUES ('John', 'Smith', 'john.smith@university.edu', 'Physics', '2025-03-15');
```

**Exact PostgreSQL error:**

``` text
ERROR:  INSERT has more expressions than target columns
LINE 2: ... 'Smith', 'john.smith@university.edu', 'Physics', '2025-03-1...

SQL state: 42601
Character: 128
```

**Why it was rejected:** Without `first_name` in `INSERT INTO` it fails to insert automatically.
This happend while I tried to add an example to properly test the table.
------------------------------------------------------------------------