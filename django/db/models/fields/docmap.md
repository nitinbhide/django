---
folder: "django/db/models/fields"
generated_on: "2026-10-03"
num_files: 12
semantic_tags: [database, fields, models, orm, relationships]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django model fields and the descriptors and lookups that give fields their model-instance and query behavior. It includes the base field API, concrete field variants, file and JSON support, generated and composite fields, and relationship fields. Reverse relationships and related-object access are represented in separate modules. Read this folder when changing field values, schema definitions, or model relationship behavior.

## Major Responsibilities

Defines model field metadata, validation and database conversion, relationship behavior, and descriptors used to access field values.

## Technology Notes

Implements Django's ORM field and database schema interfaces.

# Folder Navigation

## Merged Child Folders
No child folders are merged; small-folder merges were not run.

## Files
- `__init__.py` (Size : 105929 bytes): Implements the base Field API and the concrete scalar field classes used to define model attributes. It covers field configuration, validation, serialization, database preparation and conversion, and schema metadata.
    - Tags: [database, fields, models, orm, validation]
    - TODO/FIXME/NOTE: line 618: Note; line 1348: TODO

- `composite.py` (Size : 5908 bytes): Implements composite model fields that map multiple component fields to a single model attribute and coordinate their database representation.
    - Tags: [composite-fields, database, fields, orm]

- `files.py` (Size : 20783 bytes): Defines file and image field behavior, including file-backed model attributes and storage-aware handling of uploaded files.
    - Tags: [fields, files, models, storage]

- `generated.py` (Size : 8220 bytes): Implements generated fields whose values are computed by the database from an expression and whose schema behavior is backend-aware.
    - Tags: [database, expressions, fields, generated-columns]

- `json.py` (Size : 28700 bytes): Defines JSONField behavior for JSON values, database preparation and conversion, and JSON key/path lookups and transforms.
    - Tags: [database, fields, json, lookups]

- `mixins.py` (Size : 2012 bytes): Provides reusable field mixins for field value caching and checking defaults.
    - Tags: [fields, mixins, models]

- `proxy.py` (Size : 533 bytes): Defines the proxy field used for ordering model instances by their model order.
    - Tags: [fields, models, ordering]

- `related.py` (Size : 88030 bytes): Implements relationship fields, including foreign keys, one-to-one and many-to-many relations, and their metadata and validation behavior.
    - Tags: [fields, models, relationships]
    - TODO/FIXME/NOTE: line 883: Note

- `related_descriptors.py` (Size : 71567 bytes): Implements descriptors that provide forward and reverse access to related model objects and collections. These descriptors coordinate assignment, retrieval, caching, and relation-aware query behavior.
    - Tags: [descriptors, models, relationships]

- `related_lookups.py` (Size : 6292 bytes): Defines lookup behavior for queries involving related fields and relationship traversal.
    - Tags: [fields, lookups, relationships]

- `reverse_related.py` (Size : 13031 bytes): Defines metadata objects describing reverse relationships and their field-path behavior.
    - Tags: [metadata, relationships, reverse-relations]
    - TODO/FIXME/NOTE: line 258: Note

- `tuple_lookups.py` (Size : 15989 bytes): Implements tuple and composite-value lookup expressions used in database queries.
    - Tags: [fields, lookups, tuples]

---

## Links Child Folder docmaps
No child folder docmaps.

# Related Features

Model field definitions, database value conversion, validation, schema representation, JSON handling, file storage, and object relationships.

# Agent Guidance

## Read When

Changing model field APIs, field values, relation access, or field-related query behavior.

## Modify When

The implementation belongs to a field, relationship descriptor, or field lookup.

## Avoid Modifying When

The change concerns model-wide query APIs or low-level SQL compilation; use the model or SQL index.
