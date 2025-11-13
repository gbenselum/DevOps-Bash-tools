# PostgreSQL Scripts

This directory contains scripts for managing PostgreSQL resources.

---

### `postgres.sh`

One-touch [PostgreSQL](https://www.postgresql.org/), boots docker container + drops in to `psql` shell, with `/sql` scripts mounted in container for easy sourcing eg. `\i /sql/<name>.sql`. Optionally loads sample 'chinook' database.

---

### `psql.sh`

Shortens `psql` command to connect to [PostreSQL](https://www.postgresql.org/) by auto-populating switches from environment variables.

---

### `postgres_foreach_table.sh`

Executes a SQL query against every table, replacing `{db}`, `{schema}` and `{table}` in each iteration eg. `select count(*) from {table}`.

---

### `postgres_list_databases.sh`

Various scripts using `psql.sh` for row counts, iterating each table, or outputting clean lists of databases, schemas and tables for quick scripting.

---

### `postgres_list_schemas.sh`

Various scripts using `psql.sh` for row counts, iterating each table, or outputting clean lists of databases, schemas and tables for quick scripting.

---

### `postgres_list_tables.sh`

Various scripts using `psql.sh` for row counts, iterating each table, or outputting clean lists of databases, schemas and tables for quick scripting.

---

### `postgres_tables_row_counts.sh`

Various scripts using `psql.sh` for row counts, iterating each table, or outputting clean lists of databases, schemas and tables for quick scripting.

---

### `postgres_test_scripts.sh`

Various scripts using `psql.sh` for row counts, iterating each table, or outputting clean lists of databases, schemas and tables for quick scripting.
