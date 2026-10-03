---
folder: "django/db/migrations"
generated_on: "2026-10-03"
num_files: 19
semantic_tags: [autodetection, database, migrations, project-state, schema]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package discovers, represents, plans, and executes Django database migrations. Its modules compare model state to migration state, construct and traverse migration graphs, serialize migration values, and persist applied migrations. It also contains the migration executor and state transitions used by migration operations. Read this folder for changes to migration lifecycle and planning. Merged `operations/`: This package defines the migration operations that describe changes to database schemas and model state.

## Major Responsibilities

Coordinates migration detection, loading, graph ordering, serialization, project state, execution, and recording of applied migrations. Merged `operations/`: Provides operation classes consumed by migrations, the autodetector, optimizer, and executor.

## Technology Notes

Uses Django's model state and database schema editor abstractions. Merged `operations/`: Implements Django's migration operation and schema-editor interfaces.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `operations` : This package defines the migration operations that describe changes to database schemas and model state. The base operation module supplies shared execution and state-transition behavior. The fields and models modules group operations by the schema objects they manipulate, while special operations cover data and other migration actions. Read these modules when implementing or changing a migration operation. Provides operation classes consumed by migrations, the autodetector, optimizer, and executor.

## Files
- `autodetector.py` (Size : 91138 bytes): Compares project model states with migration state and builds ordered migration operations for detected changes. It groups related changes and tracks operation dependencies while producing migrations.
    - Tags: [autodetection, migrations, model-state]
    - TODO/FIXME/NOTE: line 48: Note; line 2015: Note

- `exceptions.py` (Size : 1264 bytes): Declares exception types for migration loading and graph ambiguity or invalid migration conditions.
    - Tags: [exceptions, migrations]

- `executor.py` (Size : 19442 bytes): Applies and unapplies migration plans, coordinating migration state transitions with database schema operations.
    - Tags: [database, execution, migrations]

- `graph.py` (Size : 13485 bytes): Defines migration graph nodes and graph traversal/planning utilities for migration dependencies and replacement nodes.
    - Tags: [dependency-graph, migrations, planning]
    - TODO/FIXME/NOTE: line 195: NOTE

- `loader.py` (Size : 19177 bytes): Finds migration modules, loads their migration objects, builds the dependency graph, and resolves migration targets and replacements.
    - Tags: [discovery, migrations, planning]
    - TODO/FIXME/NOTE: line 290: note

- `migration.py` (Size : 10004 bytes): Defines the Migration object that groups operations and dependency declarations, and provides migration-level state and execution behavior.
    - Tags: [migrations, operations, state]
    - TODO/FIXME/NOTE: line 23: Note

- `operations/base.py` (Size : 6104 bytes): Defines the base migration operation contract, including database execution, project-state updates, reduction, and migration serialization hooks. Concrete operations inherit this common lifecycle.
    - Tags: [migrations, operations, state]
    - TODO/FIXME/NOTE: line 24: Note

- `operations/fields.py` (Size : 13144 bytes): Implements migration operations for adding, altering, removing, and renaming model fields and related field state.
    - Tags: [fields, migrations, schema]

- `operations/models.py` (Size : 47189 bytes): Implements migration operations that create, delete, rename, alter, and manage models and their database structures. It also covers model options, indexes, and constraints through project-state and schema-editor operations.
    - Tags: [migrations, models, schema]

- `operations/special.py` (Size : 8364 bytes): Implements migration operations for data migrations, raw SQL, and other operations that do not fit ordinary model or field changes.
    - Tags: [data-migrations, migrations, sql]

- `operations/__init__.py` (Size : 1054 bytes): Re-exports migration operation classes as the package-level operation API.
    - Tags: [migrations, operations, package-api]

- `optimizer.py` (Size : 3324 bytes): Reduces migration operation sequences by combining compatible operations while preserving their resulting project state.
    - Tags: [migrations, operations, optimization]

- `questioner.py` (Size : 13915 bytes): Defines interactive and non-interactive responses used by migration generation for choices that cannot be inferred automatically.
    - Tags: [autodetection, migrations, prompts]

- `recorder.py` (Size : 3937 bytes): Stores and queries applied migration records through the database migration table.
    - Tags: [database, migrations, persistence]

- `serializer.py` (Size : 15202 bytes): Serializes Python values referenced by migration operations into importable migration source representations.
    - Tags: [migrations, serialization]

- `state.py` (Size : 43140 bytes): Represents historical project model state and applies migration operations to construct or render model state at a selected migration point.
    - Tags: [migrations, model-state, project-state]
    - TODO/FIXME/NOTE: line 77: Note; line 298: TODO; line 743: Note

- `utils.py` (Size : 4530 bytes): Provides shared helpers for migration module and migration-name handling.
    - Tags: [migrations, utilities]

- `writer.py` (Size : 12256 bytes): Writes migration objects and operations as Python source files, including imports and formatted operation declarations.
    - Tags: [code-generation, migrations, serialization]

- `__init__.py` (Size : 99 bytes): Marks the migration package and exposes its package-level module interface.
    - Tags: [migrations, package]

---

## Links Child Folder docmaps

None.

# Related Features

Migration generation, dependency planning, serialization, project-state evolution, and database migration execution. Merged `operations/`: Schema and data changes represented and applied through Django migrations.

# Agent Guidance

## Read When

Changing migration generation, discovery, graph planning, state history, or execution. Merged `operations/`: Adding a migration operation or changing how an operation alters database or project state.

## Modify When

The migration lifecycle or migration representation is affected. Merged `operations/`: The work concerns migration operation semantics or serialization.

## Avoid Modifying When

The change belongs to a concrete schema/data operation; inspect `operations/docmap.md`. Merged `operations/`: The change is about migration discovery, dependency graph construction, or execution orchestration.
