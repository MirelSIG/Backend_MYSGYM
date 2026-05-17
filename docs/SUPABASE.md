Supabase setup
==============

This project can use Supabase as the managed PostgreSQL backend for deployment.

Steps
-----

1. Create a Supabase project.
2. Open Project Settings -> Database and copy the connection string.
3. Use the connection string as `DATABASE_URL`.
4. Deploy the app with the Render blueprint or run it locally with the same env var.

Recommended connection format
-----------------------------

Supabase usually provides a URI similar to:

```text
postgresql://postgres:<password>@db.<project-ref>.supabase.co:5432/postgres
```

For this repo, the backend normalizes the URI to `postgresql+psycopg://...` and adds `sslmode=require` automatically when the hostname ends with `.supabase.co`.

Example
-------

```bash
export DATABASE_URL='postgresql://postgres:<password>@db.<project-ref>.supabase.co:5432/postgres'
python app.py
```

Notes
-----

- Keep the `DATABASE_URL` out of the repository.
- If you rotate the Supabase password, update the environment variable in your host.
- Existing data migrations are still available in `scripts/migrate_mysql_to_postgres.py` if you need to move rows into Supabase.
