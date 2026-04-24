# DEMO PURPOSE ONLY
### Secure Application Development <br>
Assignment 4 Node Secrets  <br>
April 24, 2026   <br>

### This Demo Uses Fake Secrets




# Scenario 3 — Non-Shared Secrets

This repository demonstrates the **correct** way to handle secrets:
the application code is shared, but the secrets are **not**. A `.env`
file is required to run the app, but it is excluded from the repository
via `.gitignore`. Each developer creates their own `.env` locally.

## Required secrets

If you clone this repo and try to run it without a `.env` file, the app
will exit with an error. To run it, create a `.env` file in the project
root with the following variables:


- `NODE_ENV=development`
- `API_KEY=<your-api-key-here>`


- `NODE_ENV` — the runtime environment (e.g., `development`, `production`).
  When set to `development`, the app response includes a listing of files
  in the project directory.
- `API_KEY` — any string value. Used by the app and echoed back in the
  response to prove the secret was loaded.

## How to run

- Install 

        npm install


- Run the simple server

        node app.js


- TEST In the browser
    1.  http://127.0.0.1:3000   - The Host

    2.  http://localhost:3000/ - The Port


* If .env is missing, you will see:

```
ERROR: Missing required secrets (NODE_ENV, API_KEY). App cannot start.

```

## Why the `.` in front of the filename?

On Unix-like systems, any filename that begins with a `.` is treated as
a **hidden file** — it does not appear in default directory listings
(`ls`) or file managers. <br> 

This convention is used for configuration and
credential files (.env, `.gitignore`, `.ssh/`, `.bashrc`) so they
don't clutter the working directory and are less likely to be noticed
or shared by accident. <br> 

The dot itself provides no security — it is
purely a display convention — but it signals to the user that the file
is configuration rather than application content.

## Why this approach is correct

- Secrets never enter the repository or git history.
- Each environment (dev, staging, prod) can have its own values.
- Rotating a secret does not require a code change.
- The repo can be made public without leaking credentials.
```

