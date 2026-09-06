# PostgreSQL Data Type Selection

| # | Column | PostgreSQL Data Type | Justification |
|---|--------|----------------------|---------------|
| 1 | student_id | `INTEGER` | This stores whole-number identifiers and supports auto-incrementing sequences effectively. |
| 2 | first_name | `VARCHAR(50)` | This limits storage to the typical maximum name length while efficiently handling variable-length text. |
| 3 | email_address | `VARCHAR(255)` | This accommodates standard email address lengths without wasting space on arbitrarily large text. |
| 4 | date_of_birth | `DATE` | This stores only the calendar date, ignoring time-of-day details which are unnecessary for a birthday. |
| 5 | account_balance | `NUMERIC(10,2)` | This precisely stores monetary values with two decimal places, avoiding floating-point rounding errors. |
| 6 | is_active | `BOOLEAN` | This represents a clear true/false state using the most efficient and logical data type for binary options. |
| 7 | event_start | `TIMESTAMPTZ` | This captures the exact date and time while automatically handling timezone conversions for participants in different regions. |
| 8 | event_description | `TEXT` | This handles unlimited variable-length text, making it perfect for paragraphs of arbitrary length. |
| 9 | maximum_attendees | `INTEGER` | This stores whole-number capacity limits using a standard, space-efficient numeric type. |
| 10 | student_attended | `BOOLEAN` | This directly maps the Yes/No requirement to PostgreSQL's native true/false type. |
| 11 | phone_number | `VARCHAR(20)` | This preserves formatting characters like '+', '-', and parentheses while accommodating various international lengths. |
| 12 | postal_code | `VARCHAR(10)` | This stores the code as text to preserve leading zeros (e.g., '33101') and handle ZIP+4 extensions cleanly. |
| 13 | event_status | `VARCHAR(20)` | This stores short string statuses and easily accommodates new future statuses without requiring schema changes. |
| 14 | student_number | `VARCHAR(10)` | This stores the value as text to preserve leading zeros and accommodate any future changes in the numbering format. |