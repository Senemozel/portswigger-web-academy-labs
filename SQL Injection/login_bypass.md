# Lab: SQL injection vulnerability allowing login bypass

## Explanation
First, I tested the login form for SQL injection by entering `administrator'--` in the username field and leaving the password field empty. The application accepted the login and granted access to the administrator account.

## Solution
The backend query looks like this:
```sql
SELECT * FROM users WHERE username='administrator'--' AND password=''
```

The `--` comment syntax causes the password check to be ignored, allowing authentication bypass.
