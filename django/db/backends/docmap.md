---
folder: "django/db/backends"
generated_on: "2026-10-03"
num_files: 39
semantic_tags: [connections, database, drivers, dummy-backend, introspection, mysql, postgresql, psycopg, schema, sql, sqlite]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder defines shared support for database backend implementations. It contains the common cursor wrappers, backend signals, DDL reference structures, and the base backend contract. Vendor-specific adapters are split into separate child folders. Start here for cross-backend behavior; use the dialect indexes for SQL or driver-specific behavior. Merged `base/`: This folder defines the reusable database backend contract inherited by database engines. Merged `dummy/`: This package provides the fallback backend used when no functional database engine is configured. Merged `sqlite3/`: This folder implements Django's SQLite backend. Merged `mysql/`: This folder implements Django's MySQL database backend. The connection wrapper configures the MySQL driver and backend components, while the remaining modules specialize client commands, compilation, creation, feature reporting, introspection, SQL operations, schema editing, and validation. These modules inherit shared behavior from the base backend and adapt it to MySQL. Use this folder for MySQL-specific behavior. Merged `postgresql/`: This folder implements Django's PostgreSQL backend. It configures the PostgreSQL connection and driver compatibility, and supplies specialized SQL compilation, database creation, capability reporting, introspection, operations, and schema editing. The `psycopg_any` module provides the driver compatibility layer shared across supported psycopg variants. Use this folder for PostgreSQL-specific behavior.

## Major Responsibilities

Supplies common database backend primitives and links the base, dummy, MySQL, Oracle, PostgreSQL, and SQLite implementations. Merged `base/`: Implements the base connection and the common hooks used for database creation, schema editing, SQL operations, introspection, and backend capability reporting. Merged `dummy/`: Represents database access that is unavailable because a usable backend has not been selected. Merged `sqlite3/`: Adapts Django's backend contract to SQLite connections, functions, schema behavior, and database operations. Merged `mysql/`: Provides the MySQL backend implementation and its database-specific SQL and schema behavior. Merged `postgresql/`: Adapts shared backend APIs to PostgreSQL connections, SQL, database metadata, schema changes, and driver variants.

## Technology Notes

Implements Django's database backend abstraction and SQL execution support. Merged `base/`: Uses Django's database wrapper and SQL compiler abstractions. Merged `dummy/`: Uses the shared database backend base classes. Merged `sqlite3/`: Targets SQLite through Python's SQLite database interface.

Merged `mysql/`: Targets MySQL through Django's database backend contract. Merged `postgresql/`: Targets PostgreSQL and the supported psycopg driver interfaces.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `base` : This folder defines the reusable database backend contract inherited by database engines. Its modules cover connection state, client commands, creation, feature flags, schema operations, introspection, SQL operations, and validation. Backend implementations override these shared behaviors where engine differences require it. Read these files for changes that should affect multiple database engines. Implements the base connection and the common hooks used for database creation, schema editing, SQL operations, introspection, and backend capability reporting.
- `dummy` : This package provides the fallback backend used when no functional database engine is configured. Its connection wrapper raises Django's database configuration error for unsupported database use. Its feature module gives Django a backend feature object without providing actual database operations. Read it when changing behavior for unconfigured database connections. Represents database access that is unavailable because a usable backend has not been selected.
- `mysql` : This folder implements Django's MySQL database backend. The connection wrapper configures the MySQL driver and backend components, while the remaining modules specialize client commands, compilation, creation, feature reporting, introspection, SQL operations, schema editing, and validation. These modules inherit shared behavior from the base backend and adapt it to MySQL. Use this folder for MySQL-specific behavior. Provides the MySQL backend implementation and its database-specific SQL and schema behavior. Targets MySQL through Django's database backend contract. # Folder Navigation
- `postgresql` : This folder implements Django's PostgreSQL backend. It configures the PostgreSQL connection and driver compatibility, and supplies specialized SQL compilation, database creation, capability reporting, introspection, operations, and schema editing. The `psycopg_any` module provides the driver compatibility layer shared across supported psycopg variants. Use this folder for PostgreSQL-specific behavior. Adapts shared backend APIs to PostgreSQL connections, SQL, database metadata, schema changes, and driver variants. Targets PostgreSQL and the supported psycopg driver interfaces. # Folder Navigation
- `sqlite3` : This folder implements Django's SQLite backend. It configures the SQLite connection and registers SQL functions, while its other modules adapt database creation, capabilities, introspection, SQL operations, and schema editing to SQLite. SQLite's built-in client integration is also defined here. Use this folder for behavior specific to SQLite databases. Adapts Django's backend contract to SQLite connections, functions, schema behavior, and database operations.

## Files
- `base/base.py` (Size : 29335 bytes): Implements the base database connection wrapper, coordinating connection setup, cursor access, transaction state, and backend component instances. Vendor backends extend this shared behavior to integrate their own drivers and SQL rules.
    - Tags: [connections, database, transactions]

- `base/client.py` (Size : 1020 bytes): Defines the base command-line client interface used to invoke database shell tools.
    - Tags: [cli, database]

- `base/creation.py` (Size : 17083 bytes): Implements common database creation, test-database setup, and teardown behavior for backend engines.
    - Tags: [database, test-databases]

- `base/features.py` (Size : 19032 bytes): Declares backend capability flags and feature-dependent behavior that ORM and schema code can query. Engine implementations specialize these defaults.
    - Tags: [capabilities, database]
    - TODO/FIXME/NOTE: line 204: Note

- `base/introspection.py` (Size : 8545 bytes): Defines the shared interface and common helpers for inspecting database tables, columns, constraints, and relationships.
    - Tags: [database, introspection, schema]

- `base/operations.py` (Size : 35288 bytes): Provides common SQL generation and database value-conversion operations used by the ORM. Backend-specific operation classes override dialect-sensitive behavior.
    - Tags: [database, sql, sql-generation]

- `base/schema.py` (Size : 88182 bytes): Implements schema editor behavior for creating, altering, and deleting database structures, including fields, indexes, and constraints. Backend subclasses adapt its generated DDL to vendor-specific syntax.
    - Tags: [database, ddl, schema]

- `base/validation.py` (Size : 1151 bytes): Defines base validation hooks for database configuration and backend options.
    - Tags: [configuration, database, validation]

- `ddl_references.py` (Size : 8882 bytes): Defines reference objects used to construct and quote schema-definition SQL while tracking table, column, and constraint references. These objects support database schema editing across backend implementations.
    - Tags: [database, ddl, schema, sql]

- `dummy/base.py` (Size : 2293 bytes): Defines the dummy connection wrapper and its failure behavior for database operations when no usable engine is configured.
    - Tags: [connections, database, dummy-backend]

- `dummy/features.py` (Size : 187 bytes): Defines the feature class for the dummy backend, inheriting the shared database feature interface.
    - Tags: [capabilities, database, dummy-backend]

- `mysql/base.py` (Size : 16756 bytes): Implements the MySQL database connection wrapper and wires up the backend's client, creation, features, introspection, operations, schema, and validation components.
    - Tags: [connections, database, mysql]
    - TODO/FIXME/NOTE: line 182: Note

- `mysql/client.py` (Size : 3060 bytes): Implements the MySQL command-line client integration used to launch a database shell.
    - Tags: [cli, database, mysql]

- `mysql/compiler.py` (Size : 3116 bytes): Specializes ORM SQL compilation for MySQL-specific query syntax and expression handling.
    - Tags: [compiler, database, mysql, sql]

- `mysql/creation.py` (Size : 4152 bytes): Implements MySQL database and test-database creation behavior.
    - Tags: [database, mysql, test-databases]

- `mysql/features.py` (Size : 8766 bytes): Declares MySQL-specific database capabilities and feature-dependent ORM behavior.
    - Tags: [capabilities, database, mysql]

- `mysql/introspection.py` (Size : 15351 bytes): Inspects MySQL schema metadata, including tables, columns, indexes, and constraints, through the backend introspection API.
    - Tags: [database, introspection, mysql, schema]

- `mysql/operations.py` (Size : 17185 bytes): Implements MySQL SQL generation, database value conversions, and backend-specific ORM operations.
    - Tags: [database, mysql, sql]

- `mysql/schema.py` (Size : 10189 bytes): Adapts schema editor DDL generation and schema changes to MySQL syntax and behavior.
    - Tags: [database, ddl, mysql, schema]

- `mysql/validation.py` (Size : 3170 bytes): Adds MySQL-specific database configuration and connection option validation.
    - Tags: [configuration, database, mysql, validation]

---

- `postgresql/base.py` (Size : 24453 bytes): Implements PostgreSQL database connection setup and backend component configuration, including the use of the driver compatibility layer.
    - Tags: [connections, database, postgresql]
    - TODO/FIXME/NOTE: line 167: Note; line 461: Note

- `postgresql/client.py` (Size : 2108 bytes): Implements the PostgreSQL command-line client integration for database shell access.
    - Tags: [cli, database, postgresql]

- `postgresql/compiler.py` (Size : 2539 bytes): Specializes ORM SQL compilation for PostgreSQL-specific query syntax and features.
    - Tags: [compiler, database, postgresql, sql]

- `postgresql/creation.py` (Size : 3977 bytes): Implements PostgreSQL database and test-database creation behavior.
    - Tags: [database, postgresql, test-databases]

- `postgresql/features.py` (Size : 7200 bytes): Declares PostgreSQL backend capability flags used by ORM and schema behavior.
    - Tags: [capabilities, database, postgresql]

- `postgresql/introspection.py` (Size : 13042 bytes): Inspects PostgreSQL database objects and metadata through Django's backend introspection interface.
    - Tags: [database, introspection, postgresql, schema]

- `postgresql/operations.py` (Size : 15926 bytes): Implements PostgreSQL-specific SQL generation and value conversion for ORM database operations.
    - Tags: [database, postgresql, sql]

- `postgresql/psycopg_any.py` (Size : 4190 bytes): Provides compatibility imports and helpers for the supported psycopg driver variants.
    - Tags: [database, drivers, postgresql, psycopg]

- `postgresql/schema.py` (Size : 15152 bytes): Adapts schema editor DDL generation and database structure changes to PostgreSQL.
    - Tags: [database, ddl, postgresql, schema]

---

- `signals.py` (Size : 69 bytes): Declares the signal emitted when a database connection is created.
    - Tags: [connections, database, signals]

- `sqlite3/_functions.py` (Size : 16296 bytes): Registers SQLite SQL functions and aggregates used by Django's ORM, including function behavior that aligns SQLite with Django database expressions.
    - Tags: [database, functions, sql, sqlite]

- `sqlite3/base.py` (Size : 15783 bytes): Implements SQLite connection setup, backend component configuration, and SQLite-specific connection behavior.
    - Tags: [connections, database, sqlite]
    - TODO/FIXME/NOTE: line 132: Note

- `sqlite3/client.py` (Size : 331 bytes): Defines the SQLite command-line client used for database shell access.
    - Tags: [cli, database, sqlite]

- `sqlite3/creation.py` (Size : 6981 bytes): Implements SQLite database and test-database creation and lifecycle behavior.
    - Tags: [database, sqlite, test-databases]

- `sqlite3/features.py` (Size : 7375 bytes): Declares SQLite-specific database capabilities used by Django's ORM and schema code.
    - Tags: [capabilities, database, sqlite]

- `sqlite3/introspection.py` (Size : 18502 bytes): Inspects SQLite tables and schema metadata through the backend introspection interface.
    - Tags: [database, introspection, schema, sqlite]

- `sqlite3/operations.py` (Size : 16397 bytes): Implements SQLite-specific SQL generation and value conversions for ORM database operations.
    - Tags: [database, sql, sqlite]

- `sqlite3/schema.py` (Size : 20860 bytes): Implements SQLite schema editing, including the backend-specific SQL required for schema changes.
    - Tags: [database, ddl, schema, sqlite]

- `utils.py` (Size : 11479 bytes): Implements database cursor wrappers, debug query capture, transaction debug helpers, and database value type-casting utilities. It provides shared cursor behavior consumed by backend connection classes.
    - Tags: [cursors, database, debugging, sql]

## Links Child Folder docmaps
- `oracle/docmap.md` — Oracle connection, schema, SQL behavior, and compatibility utilities.

# Related Features

Shared database backend contracts, cursor handling, and backend-specific database access. Merged `base/`: Shared database connections, SQL operation generation, schema changes, database creation, and introspection. Merged `dummy/`: Fallback behavior for database connections without a configured backend. Merged `sqlite3/`: SQLite connections, SQL functions, schema inspection, and schema changes.

# Agent Guidance

## Read When

Changing behavior that applies to multiple database engines or choosing the correct backend implementation area. Merged `base/`: Changing behavior shared by multiple database backends or investigating the base backend contract. Merged `dummy/`: Changing errors or feature reporting for unconfigured databases. Merged `sqlite3/`: Changing the SQLite backend, its registered database functions, or its schema behavior.

## Modify When

The behavior belongs to common cursor handling, schema references, or connection signals. Merged `base/`: A common backend default or behavior should change consistently across engines. Merged `dummy/`: The dummy backend's connection behavior or declared capabilities must change. Merged `sqlite3/`: The change is specific to SQLite.

## Avoid Modifying When

The change concerns one database engine only; prefer that engine's child folder. Merged `base/`: Only one engine needs a dialect-specific change; update its backend implementation instead. Merged `dummy/`: Adding functionality for a supported database engine; use that backend's folder. Merged `sqlite3/`: The behavior applies to every database backend; check this map's merged `base/` section.
