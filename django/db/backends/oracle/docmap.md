---
folder: "django/db/backends/oracle"
generated_on: "2026-10-03"
num_files: 10
semantic_tags: [database, oracle, sql]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django's Oracle database backend and its Oracle-specific SQL and schema behavior. It provides the driver-facing connection wrapper alongside database creation, introspection, capability flags, operations, schema editing, and validation. Supporting modules handle the command-line client, SQL functions, and Oracle compatibility utilities. Use it for behavior that is specific to Oracle databases.

## Major Responsibilities

Adapts Django's common database backend interfaces to Oracle connections, metadata, SQL, and schema operations.

## Technology Notes

Targets Oracle through Django's database backend contract.

# Folder Navigation

## Merged Child Folders
No child folders are merged; small-folder merges were not run.

## Files
- `base.py` (Size : 26615 bytes): Implements Oracle database connection setup and composes the backend's Oracle-specific database components.
    - Tags: [connections, database, oracle]
    - TODO/FIXME/NOTE: line 214: Note; line 492: note

- `client.py` (Size : 811 bytes): Implements the command-line client integration for an Oracle database shell.
    - Tags: [cli, database, oracle]

- `creation.py` (Size : 21552 bytes): Implements Oracle database and test-database lifecycle behavior, including Oracle-specific database creation operations.
    - Tags: [database, oracle, test-databases]

- `features.py` (Size : 10517 bytes): Declares Oracle-specific backend capabilities used to select database-dependent ORM behavior.
    - Tags: [capabilities, database, oracle]

- `functions.py` (Size : 838 bytes): Provides Oracle-specific SQL function and expression support used by database operations.
    - Tags: [database, functions, oracle, sql]

- `introspection.py` (Size : 16346 bytes): Reads Oracle database metadata through the backend introspection interface, including schema objects and their properties.
    - Tags: [database, introspection, oracle, schema]

- `operations.py` (Size : 29392 bytes): Implements Oracle-specific SQL generation and database value conversion behavior for the ORM.
    - Tags: [database, oracle, sql]
    - TODO/FIXME/NOTE: line 36: TODO

- `schema.py` (Size : 11105 bytes): Adapts schema editor SQL and database structure changes to Oracle's schema rules.
    - Tags: [database, ddl, oracle, schema]

- `utils.py` (Size : 2851 bytes): Contains Oracle support helpers for database connection and value compatibility.
    - Tags: [database, oracle, utilities]

- `validation.py` (Size : 882 bytes): Implements Oracle-specific database option validation.
    - Tags: [configuration, database, oracle, validation]

---

## Links Child Folder docmaps
No child folder docmaps.

# Related Features

Oracle database connections, SQL operations, metadata inspection, and schema management.

# Agent Guidance

## Read When

Changing Django's Oracle driver integration or dialect-specific SQL behavior.

## Modify When

The behavior is specific to Oracle's connection, schema, capabilities, or SQL syntax.

## Avoid Modifying When

The behavior is shared across all database engines; check the merged `base/` section in `../docmap.md`.
