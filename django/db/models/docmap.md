---
folder: "django/db/models"
generated_on: "2026-10-03"
num_files: 33
semantic_tags: [database, expressions, functions, models, orm, queries, sql]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package implements Django's object-relational model layer. It defines model construction and metadata, query and manager APIs, field-independent expressions, aggregates, constraints, indexes, and supporting utilities. Field types, database functions, and SQL query construction live in the linked child folders. Read this folder for model behavior and ORM APIs above the SQL compiler layer. Merged `functions/`: This package exposes database function and transform expressions for use in Django ORM queries. Merged `sql/`: This package translates ORM query state into database SQL.

## Major Responsibilities

Provides model base classes, model metadata and options, querysets, managers, expressions, and ORM-level model operations. Merged `functions/`: Provides composable ORM expressions that compile to database functions and transforms across supported backends. Merged `sql/`: Implements query structures, predicate trees, SQL compilation, and operation-specific database query subclasses.

## Technology Notes

Implements Django's Python ORM and database expression interfaces. Merged `functions/`: Uses Django's database expression and SQL compilation APIs. Merged `sql/`: Uses Django's database connection operations and expression APIs.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `functions` : This package exposes database function and transform expressions for use in Django ORM queries. Its modules group functions by comparison, date/time, JSON, mathematics, text, UUID, and window operations. Shared mixins normalize input and output field behavior across function classes. Read these modules when adding or changing built-in SQL expression functions. Provides composable ORM expressions that compile to database functions and transforms across supported backends.
- `sql` : This package translates ORM query state into database SQL. It represents query tables and joins, conditions, and specialized insert, update, delete, and aggregate queries. The compiler classes generate statements and coordinate execution against database cursors. Read this folder when changing SQL generation or the internal representation of ORM queries. Implements query structures, predicate trees, SQL compilation, and operation-specific database query subclasses.

## Files
- `aggregates.py` (Size : 15895 bytes): Defines aggregate expressions such as counts and numeric/statistical aggregates for use in ORM queries. Aggregate classes provide SQL expression behavior and output-field handling.
    - Tags: [aggregates, expressions, orm]

- `base.py` (Size : 102620 bytes): Implements Django's model base class and model construction lifecycle, including class preparation, instance initialization, save/delete behavior, and model validation. It coordinates model metadata and field descriptors with database operations.
    - Tags: [model-construction, models, orm]
    - TODO/FIXME/NOTE: line 1563: TODO; line 1590: Note; line 2074: Note

- `constants.py` (Size : 223 bytes): Defines constants used by the ORM's query conflict handling.
    - Tags: [constants, orm, queries]

- `constraints.py` (Size : 29549 bytes): Defines model constraints including check, unique, and deferrable constraint representations, with validation and database SQL integration.
    - Tags: [constraints, database, models, schema]

- `deletion.py` (Size : 22684 bytes): Implements deletion collection and cascading behavior for model instances and related objects before database deletion.
    - Tags: [cascade, deletion, models, orm]

- `enums.py` (Size : 2446 bytes): Defines model-related enumerations, including choices support and enumeration helpers used to represent field values.
    - Tags: [choices, enums, models]

- `expressions.py` (Size : 80129 bytes): Defines composable ORM expressions and expression-resolution behavior used to represent calculations and references in database queries. Expressions support SQL compilation and operations such as conditional, combined, and subquery expressions.
    - Tags: [expressions, orm, queries, sql]
    - TODO/FIXME/NOTE: line 54: note; line 970: FIXME

- `fetch_modes.py` (Size : 1332 bytes): Defines data structures for configuring how related objects are fetched by ORM queries.
    - Tags: [fetching, models, orm]

- `functions/comparison.py` (Size : 7021 bytes): Defines comparison-oriented SQL functions including casting, coalescing, collation, greatest/least selection, and null handling.
    - Tags: [comparison, expressions, functions, sql]

- `functions/datetime.py` (Size : 14457 bytes): Defines date/time extraction and truncation expressions with timezone-aware SQL behavior, alongside the current-time expression.
    - Tags: [datetime, expressions, functions, sql, timezones]

- `functions/json.py` (Size : 4288 bytes): Defines JSON array and object construction expressions for database queries.
    - Tags: [expressions, functions, json, sql]

- `functions/math.py` (Size : 6354 bytes): Defines mathematical database functions and transforms for trigonometric, exponential, rounding, logarithmic, and related operations.
    - Tags: [expressions, functions, math, sql]

- `functions/mixins.py` (Size : 2444 bytes): Provides input and output field mixins for numeric and duration database functions.
    - Tags: [expressions, functions, mixins, orm]

- `functions/text.py` (Size : 11915 bytes): Defines text and string functions and transforms, including concatenation, case conversion, padding, trimming, substring, and hash functions.
    - Tags: [expressions, functions, strings, text]

- `functions/uuid.py` (Size : 3678 bytes): Defines database expressions for generating UUID values.
    - Tags: [expressions, functions, sql, uuid]

- `functions/window.py` (Size : 2961 bytes): Defines window expressions for ranking, distribution, offsets, and value selection over query partitions.
    - Tags: [expressions, functions, sql, window-functions]

- `functions/__init__.py` (Size : 2979 bytes): Exposes the public database function classes from the specialized function modules.
    - Tags: [functions, orm, package-api]

- `indexes.py` (Size : 15969 bytes): Defines model index classes and their validation, deconstruction, and schema-editing behavior.
    - Tags: [database, indexes, models, schema]

- `lookups.py` (Size : 29677 bytes): Implements lookup classes that translate ORM field comparisons and lookup expressions into database query behavior.
    - Tags: [lookups, orm, queries]

- `manager.py` (Size : 7079 bytes): Defines the manager API that provides model-level access to querysets and query construction.
    - Tags: [managers, models, orm, queries]

- `options.py` (Size : 40727 bytes): Implements model metadata options, collecting and exposing field, constraint, index, relationship, and table configuration for each model.
    - Tags: [metadata, models, orm]
    - TODO/FIXME/NOTE: line 151: Note; line 205: NOTE

- `query.py` (Size : 125083 bytes): Implements the public QuerySet API for constructing, refining, combining, and evaluating model queries. It coordinates query expressions, model managers, and lower-level SQL query construction.
    - Tags: [models, orm, queries]

- `query_utils.py` (Size : 20927 bytes): Provides shared utilities and helper classes used by ORM query construction, filtering, and model metadata behavior.
    - Tags: [orm, queries, utilities]

- `signals.py` (Size : 1676 bytes): Declares model lifecycle signals emitted around class preparation and model save/delete events.
    - Tags: [models, orm, signals]

- `sql/compiler.py` (Size : 99804 bytes): Compiles ORM query objects into SQL and executes select, insert, delete, update, and aggregate statements through database cursors.
    - Tags: [compiler, database, orm, sql]
    - TODO/FIXME/NOTE: line 60: Note; line 156: Note

- `sql/constants.py` (Size : 625 bytes): Defines constants used by ORM SQL query construction and compilation.
    - Tags: [constants, orm, sql]

- `sql/datastructures.py` (Size : 7501 bytes): Defines SQL query structures for joins, base tables, and related table-alias data.
    - Tags: [joins, orm, sql]
    - TODO/FIXME/NOTE: line 59: Note

- `sql/query.py` (Size : 127332 bytes): Implements the internal ORM Query representation, including filter paths, joins, annotations, ordering, grouping, subquery handling, and query combination. It tracks the state that the SQL compiler consumes.
    - Tags: [database, orm, queries, sql]
    - TODO/FIXME/NOTE: line 256: Note; line 742: Note; line 1527: Note; line 1918: Note; line 1988: Note; line 2166: Note; line 2186: Note; line 2291: Note; line 2905: Note

- `sql/subqueries.py` (Size : 6170 bytes): Defines query subclasses for insert, update, delete, and aggregate statements.
    - Tags: [database, orm, queries, sql]

- `sql/where.py` (Size : 12662 bytes): Implements predicate-tree nodes and SQL rendering for where clauses and related condition structures.
    - Tags: [conditions, orm, queries, sql]

- `sql/__init__.py` (Size : 247 bytes): Initializes the SQL query package.
    - Tags: [orm, package, sql]

- `utils.py` (Size : 2641 bytes): Provides utility functions for model metadata and ORM operations.
    - Tags: [models, orm, utilities]

- `__init__.py` (Size : 3496 bytes): Exposes the public model API, including model classes, fields, managers, query expressions, constraints, and indexes. It gathers these objects from the model package's implementation modules.
    - Tags: [models, orm, package-api]

---

## Links Child Folder docmaps
- `fields/docmap.md` — Model field classes, relationship descriptors, field lookups, and field-specific behavior.

# Related Features

Model definition, ORM queries, expressions, model constraints and indexes, relation handling, and object deletion. Merged `functions/`: ORM expressions for database-native mathematical, textual, temporal, JSON, UUID, comparison, and window functions. Merged `sql/`: ORM query compilation and execution, joins, filtering conditions, and database write queries.

# Agent Guidance

## Read When

Changing model APIs, querysets, metadata, expressions, constraints, or model lifecycle behavior. Merged `functions/`: Changing a built-in ORM database function or adding a function expression. Merged `sql/`: Changing how ORM queries are represented or compiled to SQL.

## Modify When

The change is part of ORM behavior above field implementation or SQL query compilation. Merged `functions/`: The operation should be represented as a database function or transform. Merged `sql/`: The change concerns joins, predicates, SQL generation, or operation-specific query objects.

## Avoid Modifying When

The change is specifically about a field type, SQL compiler, or migration operation; use the corresponding child index. Merged `functions/`: The change is generic expression resolution or vendor backend SQL behavior; inspect the model or backend indexes. Merged `sql/`: The change is a public QuerySet API or database vendor-specific behavior; use the parent models or backend index.
