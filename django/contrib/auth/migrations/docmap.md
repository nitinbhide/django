---
folder: "django/contrib/auth/migrations"
generated_on: "2026-10-03"
num_files: 12
semantic_tags: [authentication, contenttypes, database, django, migrations, permissions, schema, users]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder records the schema and data migration history for Django's authentication app. Its ordered migrations establish the Permission, Group, and User models, then evolve selected fields and their validation behavior. The history also coordinates authentication migrations with the contenttypes app. One reversible data migration moves permissions for proxy models to their proxy content types.

## Major Responsibilities

The migration modules create and alter authentication tables and fields, including permission names, group names, username validation and length, and user profile fields. They declare migration ordering requirements, including a contenttypes prerequisite. A RunPython operation updates proxy-model permission content types and provides a reverse operation.

## Technology Notes

Python migration modules use Django's migration operations and serialized model fields. The data migration uses the historical app registry, database alias routing, transactions, and ORM query expressions; content types are supplied by Django's contenttypes app.

# Folder Navigation

## Merged Child Folders

None.

## Files
- `0001_initial.py` (Size : 7485 bytes): Defines the initial authentication schema for Permission, Group, and User, including their fields, relationships, options, and model managers. The User model is swappable through `AUTH_USER_MODEL`, and username validation uses Django's Unicode username validator. Permission and group relationships connect users to assigned permissions and group-derived permissions. This migration depends on the initial contenttypes migration.
    - Tags: [authentication, database, migrations, permissions, schema, users]

- `0002_alter_permission_name_max_length.py` (Size : 361 bytes): Alters the Permission `name` field to allow up to 255 characters. It depends on the initial auth migration and expresses the change with an `AlterField` operation. No other model fields or data operations are defined. The migration is part of the auth schema history.
    - Tags: [database, migrations, permissions, schema]

- `0003_alter_user_email_max_length.py` (Size : 435 bytes): Alters the User `email` field to use a maximum length of 254 characters. The field remains an optional email field with the “email address” label. It depends on the preceding permission-name migration. The change is represented as a Django `AlterField` operation.
    - Tags: [database, migrations, schema, users]

- `0004_alter_user_username_opts.py` (Size : 907 bytes): Alters the User `username` field with Django's Unicode username validator and an explicit uniqueness error message. It retains the 30-character maximum and updates the field help text. The source comment explicitly notes that the migration makes no database changes and changes validators and error messages. It depends on the initial auth migration.
    - Tags: [authentication, migrations, schema, users, validation]

- `0005_alter_user_last_login_null.py` (Size : 427 bytes): Alters the User `last_login` field to allow null values and marks it blank in forms. The change is encoded as an `AlterField` operation. It depends on the username-options migration. No data migration or other field alteration is included.
    - Tags: [database, migrations, schema, users]

- `0006_require_contenttypes_0002.py` (Size : 382 bytes): Adds an explicit dependency on contenttypes migration `0002_remove_content_type_name`, following the prior auth migration. Its operations list is empty, so it performs no schema or data operation itself. The source comments explain that the ordering ensures contenttypes is migrated before `post_migrate` signals create ContentType records. This migration therefore coordinates app migration ordering.
    - Tags: [contenttypes, migrations, signals]

- `0007_alter_validators_add_error_messages.py` (Size : 828 bytes): Alters the User `username` field to specify Django's Unicode username validator, its uniqueness error message, and the corresponding help text. The field remains unique and limited to 30 characters. The migration follows the contenttypes prerequisite migration. It uses an `AlterField` operation and contains no data operation.
    - Tags: [authentication, migrations, schema, users, validation]

- `0008_alter_user_username_max_length.py` (Size : 840 bytes): Alters the User `username` field's maximum length to 150 characters and updates its help text to match. It preserves uniqueness, the Unicode username validator, and the configured uniqueness error message. It depends on the validator/error-message migration. The field change is represented by an `AlterField` operation.
    - Tags: [authentication, migrations, schema, users, validation]

- `0009_alter_user_last_name_max_length.py` (Size : 432 bytes): Alters the User `last_name` field to allow 150 characters while keeping it optional. It depends on the username-length migration. The change is represented by a single `AlterField` operation. No data migration is defined.
    - Tags: [database, migrations, schema, users]

- `0010_alter_group_name_max_length.py` (Size : 393 bytes): Alters the Group `name` field to allow 150 characters while retaining its uniqueness constraint. It depends on the preceding User last-name migration. The schema update is expressed as a single `AlterField` operation. No data operation is defined.
    - Tags: [database, groups, migrations, schema]

- `0011_update_proxy_permissions.py` (Size : 2936 bytes): Defines a data migration that changes proxy-model permissions to use the proxy model's ContentType rather than the concrete model's ContentType. It selects default and custom permission codenames, routes queries through the migration database alias, and updates permissions atomically. The reverse operation restores the concrete-model ContentType association. An integrity conflict is reported with a warning that asks operators to audit permissions for both content types.
    - Tags: [contenttypes, data-migration, django, permissions, proxy-models]

- `0012_alter_user_first_name_max_length.py` (Size : 428 bytes): Alters the User `first_name` field to allow 150 characters while retaining its optional status. It depends on the proxy-permission data migration. The change is encoded as a single `AlterField` operation. No data operation is defined.
    - Tags: [database, migrations, schema, users]

---

## Links Child Folder docmaps

None.

# Related Features

Django authentication model schema evolution, permission and group definitions, username validation, migration ordering with contenttypes, and proxy-model permission migration.

# Agent Guidance

## Read When

Read this folder when tracing authentication model schema changes, migration dependencies, permission content-type behavior, or migration reversibility.

## Modify When

Modify these files when adding or changing the authentication app's migration history. New migrations should preserve Django's migration ordering and historical-model conventions.

## Avoid Modifying When

Avoid editing historical migrations to implement current model behavior; use the current model definitions and add a migration for schema changes instead.

## Dependency Graph

Not generated. Dependency metadata is intentionally empty.
