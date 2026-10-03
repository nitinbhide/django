---
folder: "django/core/management/commands"
generated_on: "2026-10-03"
num_files: 26
semantic_tags: [commands, database, django-admin, management, testing]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django's built-in management commands. Commands cover project checks, database and migration operations, data import/export, app/project scaffolding, development servers, tests, shell access, and translation catalogs. Each command is exposed through the management command framework. Read the focused command module for the behavior of a particular `django-admin` or `manage.py` operation.

## Major Responsibilities

The command classes parse options, coordinate Django subsystems, and provide command-line output. Shared command execution and option handling are provided by the parent management package.

## Technology Notes

The commands integrate with Django's ORM, migrations, test runner, translation system, templates, and server.

# Folder Navigation

## Merged Child Folders

None.

## Files
- `check.py` (Size : 2920 bytes): Implements the `check` command for running registered system checks. It supports command options that select checks and control displayed output. Results are reported through the management command framework. No markers are present.
    - Tags: [commands, system-checks]
- `compilemessages.py` (Size : 7205 bytes): Implements compilation of message catalog files for translations. It locates catalogs and invokes the available message compilation tools. The command integrates locale selection with Django's translation infrastructure. No markers are present.
    - Tags: [commands, localization, translation]
- `createcachetable.py` (Size : 4787 bytes): Creates the database table required by the database cache backend. It validates command options and delegates table creation to the cache backend. It connects management commands with database cache setup. No markers are present.
    - Tags: [cache, commands, database]
- `dbshell.py` (Size : 1811 bytes): Launches the configured database client's interactive shell. It assembles the command and connection parameters from the active database configuration. Line 33 contains a `NOTE` comment about assumptions for a missing executable error.
    - Tags: [commands, database, shell]
    - TODO/FIXME/NOTE: line 33 NOTE
- `diffsettings.py` (Size : 3656 bytes): Displays differences between project settings and Django's default settings. It formats values for readable command output and supports controlling the comparison. This helps inspect active settings overrides. No markers are present.
    - Tags: [commands, configuration, settings]
- `dumpdata.py` (Size : 11480 bytes): Implements serialization of selected model data to command output or a destination. It supports model/app selection, natural keys, ordering, and serializer options. The command delegates representation to Django's serialization framework. No markers are present.
    - Tags: [commands, database, serialization]
- `flush.py` (Size : 3714 bytes): Implements removal of data from the database while preserving the schema. It respects database selection and confirmation options, then executes the database flush operation. It is used to reset database contents. No markers are present.
    - Tags: [commands, database]
- `inspectdb.py` (Size : 18335 bytes): Generates model definitions by introspecting existing database tables. It maps database metadata and field types into Django model declarations. Options control selected tables and output formatting. No markers are present.
    - Tags: [commands, database, introspection, models]
- `listurls.py` (Size : 5772 bytes): Implements a command that enumerates URL patterns from the configured URL resolver. It formats route, name, and callback information for command-line inspection. It uses Django's URL resolver and management output facilities. No markers are present.
    - Tags: [commands, urls]
- `loaddata.py` (Size : 16441 bytes): Loads serialized fixture data into one or more configured databases. It discovers fixture files, deserializes objects, and handles transactions and constraints around loading. Options control fixture names and database routing. No markers are present.
    - Tags: [commands, database, fixtures, serialization]
- `makemessages.py` (Size : 29932 bytes): Extracts translatable strings from project files and updates message catalogs. It coordinates file traversal, message extraction, and gettext tools while honoring locale and path options. This command supports Django's localization workflow. No markers are present.
    - Tags: [commands, gettext, localization]
- `makemigrations.py` (Size : 23077 bytes): Detects model-state changes and creates migration files. It coordinates migration autodetection, conflict checks, database routers, and output writing. Options control app selection and migration generation. No markers are present.
    - Tags: [commands, database, migrations, models]
- `migrate.py` (Size : 22016 bytes): Applies or unapplies database migrations for selected apps and databases. It uses the migration loader, executor, and plan display to coordinate schema changes. Command options govern targets and execution behavior. No markers are present.
    - Tags: [commands, database, migrations]
- `optimizemigration.py` (Size : 5373 bytes): Rewrites a migration to simplify or optimize its operations. It loads migration state, runs optimization, and writes the resulting migration when beneficial. It is part of the migration authoring workflow. No markers are present.
    - Tags: [commands, migrations, optimization]
- `runserver.py` (Size : 7762 bytes): Starts Django's development HTTP server. It configures the server, address/port, autoreload, and request handling based on command options. Production deployments use different server infrastructure. No markers are present.
    - Tags: [commands, development-server, http]
- `sendtestemail.py` (Size : 1911 bytes): Sends a test message through Django's configured email backend. The command accepts recipient addresses and uses the mail API. It verifies that the project's email configuration can deliver a message. No markers are present.
    - Tags: [commands, email]
- `shell.py` (Size : 10009 bytes): Provides an interactive shell initialized with Django's application context. It supports selecting a shell implementation and importing project models or configured objects. Command options control startup and environment behavior. No markers are present.
    - Tags: [commands, interactive-shell]
- `showmigrations.py` (Size : 7024 bytes): Displays migration status for configured apps and databases. It reads migration graph and recorder state to distinguish applied and unapplied migrations. Output options control list or plan presentation. No markers are present.
    - Tags: [commands, database, migrations]
- `sqlflush.py` (Size : 1061 bytes): Prints SQL statements that would flush database contents. It delegates SQL generation to the database backend without executing the statements. This supports inspection of database reset operations. No markers are present.
    - Tags: [commands, database, sql]
- `sqlmigrate.py` (Size : 3393 bytes): Prints SQL generated for a named migration. It loads the migration plan and asks the selected backend to render migration operations. The command is intended for inspecting, not applying, migration SQL. No markers are present.
    - Tags: [commands, database, migrations, sql]
- `sqlsequencereset.py` (Size : 1133 bytes): Prints SQL to reset sequences for selected models. It delegates sequence SQL generation to the configured database backend. The output can be reviewed or run separately. No markers are present.
    - Tags: [commands, database, sql]
- `squashmigrations.py` (Size : 10384 bytes): Combines a sequence of migrations into a replacement migration. It validates the selected range and coordinates migration optimizer and writer behavior. The command supports reducing migration history while preserving represented operations. No markers are present.
    - Tags: [commands, migrations]
- `startapp.py` (Size : 548 bytes): Creates a new Django application from the app template. It delegates file rendering and destination handling to the management template utilities. Options choose the project directory and target name. No markers are present.
    - Tags: [commands, project-scaffolding]
- `startproject.py` (Size : 860 bytes): Creates a new Django project from the project template. It uses management template rendering to populate project files and substitute the chosen project name. Options select the destination directory. No markers are present.
    - Tags: [commands, project-scaffolding]
- `test.py` (Size : 2433 bytes): Implements the test management command and its command-line options. It selects and configures Django's test runner, then returns the resulting test status. The command supports test labels and runner-specific settings. No markers are present.
    - Tags: [commands, testing]
- `testserver.py` (Size : 2286 bytes): Loads fixture data and runs a development server against it for testing. It coordinates fixture loading with server startup and accepts fixture and address options. This command supports manual testing with populated test data. No markers are present.
    - Tags: [commands, fixtures, testing]

---

## Links Child Folder docmaps

None.

# Related Features

Built-in project administration, database migration and data commands, localization, and test execution.

# Agent Guidance

## Read When

Changing a specific Django management command or its command-line behavior.

## Modify When

Updating a command's options, subsystem integration, or user-visible output.

## Avoid Modifying When

Changing shared management command infrastructure that belongs in the parent folder.
