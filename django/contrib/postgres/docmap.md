---
folder: "django/contrib/postgres"
generated_on: "2026-10-03"
num_files: 29
semantic_tags: [aggregates, array, array-field, attribute-helper, case-insensitive-text, deprecation, django, django-forms, django-orm, field-exports, form-fields, forms, full-text-search, historical-migrations, hstore, hstore-field, indexes, jinja2, json, json-field, lookups, migrations, package-exports, postgres, postgres-ranges, postgresql, range-fields, range-lookups, range-types, re-exports, serialization, serialization-support, sql-transforms, statistics, template, templates, transforms, validation, warnings, widget, widgets]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This package provides PostgreSQL-specific extensions to Django's ORM, schema migrations, and database integration. Its direct modules implement PostgreSQL query expressions, lookups, indexes, constraints, and migration operations, along with application setup and database type handling. The package's child folders provide aggregates, model fields, form fields, and widget templates for PostgreSQL-specific data types. Together these modules expose PostgreSQL capabilities through Django APIs while delegating SQL execution and connection behavior to Django's database infrastructure. Merged `aggregates/`: This folder provides PostgreSQL-specific aggregate expression classes for use with Django ORM queries. Merged `fields/`: This package exposes PostgreSQL-specific model fields through Django's `contrib.postgres` API. Merged `forms/`: This folder provides Django form fields and widgets for PostgreSQL-specific data types. Merged `jinja2/`: This folder organizes PostgreSQL-specific Jinja2 widget templates for Django forms. Merged `templates/`: This folder organizes Django-template resources for PostgreSQL-specific widgets.

## Major Responsibilities

The package configures PostgreSQL-specific application behavior and registers database adapters, serializers, lookups, and index expression wrappers. Its ORM modules implement full-text and trigram search, array subqueries, PostgreSQL index types, exclusion constraints, and database functions. Migration operations create extensions and collations and support concurrent index and staged constraint operations. Child folders supply related aggregate, field, form, and template APIs. Merged `aggregates/`: It exposes aggregate classes to Django applications and validates the required arguments for two-variable statistical aggregates. Merged `fields/`: `ArrayField`, `HStoreField`, and the range-field family adapt values and query operations to PostgreSQL-specific column types. The modules also register field-specific lookups and transforms, and provide compatibility classes retained for historical migrations. `__init__.py` re-exports the field APIs, while `utils.py` supplies an attribute-setting helper used during value serialization. Merged `forms/`: The array module provides comma-delimited and split-widget form fields, including per-item validation and array length checks. The HStore module parses JSON dictionary input and converts non-null values to strings. The ranges module adapts PostgreSQL range objects to paired form fields and widgets, validating bounds and ordering. The initializer gathers these APIs for package-level imports. Merged `jinja2/`: Group PostgreSQL Jinja2 template resources and direct agents to the widget folder index. Merged `jinja2/postgres/`: Provide a navigation point for PostgreSQL Jinja2 widget template resources. Merged `jinja2/postgres/widgets/`: Provide the split-array widget template entry by including the shared multiwidget renderer. Merged `templates/`: Group PostgreSQL widget templates and direct agents to the relevant folder index. Merged `templates/postgres/`: Provide a navigation point for PostgreSQL widget template resources. Merged `templates/postgres/widgets/`: Expose the shared multiwidget rendering template for this PostgreSQL widget.

## Technology Notes

The implementation uses Django's ORM expressions, schema-editor and migration APIs, PostgreSQL SQL operators and extension types, and psycopg 2/3 adapter interfaces. PostgreSQL range, hstore, citext, full-text-search, and trigram capabilities are represented through these APIs. Merged `aggregates/`: The code uses Django's ORM `Aggregate` expressions, PostgreSQL aggregate functions, and Django's deprecation-warning framework. Merged `fields/`: The folder uses Python, Django model-field and query-expression APIs, and PostgreSQL database types and operators. Range handling uses the range classes exposed through Django's PostgreSQL psycopg compatibility module. Merged `forms/`: The files extend Django forms and widgets, and integrate with PostgreSQL range types and array validators. JSON serialization and parsing are used for HStore form values. Merged `jinja2/`: Jinja2 templates are used for Django form widget rendering. Merged `jinja2/postgres/`: Jinja2 templates are used for Django form widget rendering. Merged `jinja2/postgres/widgets/`: Jinja2 template include and Django form widget rendering. Merged `templates/`: Django template includes are used for PostgreSQL form widgets. Merged `templates/postgres/`: Django template includes are used for PostgreSQL form widgets. Merged `templates/postgres/widgets/`: Django template include and PostgreSQL form widget template.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `aggregates` : This folder provides PostgreSQL-specific aggregate expression classes for use with Django ORM queries. Its modules cover array, JSON, boolean, string, bitwise, statistical, and regression aggregates. The package initializer re-exports the general and statistical APIs. Implementations define SQL function names, output fields, and aggregate options such as distinct values and ordering. Compatibility wrappers emit Django deprecation warnings for APIs being moved or retired. It exposes aggregate classes to Django applications and validates the required arguments for two-variable statistical aggregates.
- `fields` : This package exposes PostgreSQL-specific model fields through Django's `contrib.postgres` API. It implements array, hstore, and range fields, alongside compatibility definitions for legacy case-insensitive text and JSON fields. The field implementations connect Django's ORM to PostgreSQL types, lookups, transforms, validation, forms, and serialization. Their behavior is supported by Django's PostgreSQL utilities and backend range types. `ArrayField`, `HStoreField`, and the range-field family adapt values and query operations to PostgreSQL-specific column types. The modules also register field-specific lookups and transforms, and provide compatibility classes retained for historical migrations. `__init__.py` re-exports the field APIs, while `utils.py` supplies an attribute-setting helper used during value serialization.
- `forms` : This folder provides Django form fields and widgets for PostgreSQL-specific data types. Its modules handle array values, HStore dictionaries, and range values. The package initializer re-exports the public form APIs from those modules. The implementation builds on Django's standard form validation and widget interfaces. The array module provides comma-delimited and split-widget form fields, including per-item validation and array length checks. The HStore module parses JSON dictionary input and converts non-null values to strings. The ranges module adapts PostgreSQL range objects to paired form fields and widgets, validating bounds and ordering. The initializer gathers these APIs for package-level imports.
- `jinja2/postgres/widgets` : This folder contains one retained Jinja2 widget template. The template delegates its content to Django's shared multiwidget template. No other folder contents are represented here. Its observed content does not establish additional split-array-specific behavior. Provide the split-array widget template entry by including the shared multiwidget renderer.
- `jinja2/postgres` : This folder organizes PostgreSQL-specific Jinja2 widget templates. Its `widgets` child contains the split-array template entry, which includes Django's shared multiwidget renderer. No eligible files are listed directly in this folder. Merged `widgets/`: This folder contains one retained Jinja2 widget template. Provide a navigation point for PostgreSQL Jinja2 widget template resources. Merged `widgets/`: Provide the split-array widget template entry by including the shared multiwidget renderer.
- `jinja2` : This folder organizes PostgreSQL-specific Jinja2 widget templates for Django forms. Its `postgres` child contains a widget index for the split-array template, which includes the shared multiwidget renderer. No eligible files are listed directly in this folder. Merged `postgres/`: This folder organizes PostgreSQL-specific Jinja2 widget templates. Group PostgreSQL Jinja2 template resources and direct agents to the widget folder index. Merged `postgres/`: Provide a navigation point for PostgreSQL Jinja2 widget template resources. Merged `postgres/widgets/`: Provide the split-array widget template entry by including the shared multiwidget renderer.
- `templates/postgres/widgets` : This folder contains one retained PostgreSQL widget template entry. The file is named `split_array.html`. Its content includes Django's shared `multiwidget.html` template. The file delegates rendering rather than defining standalone markup. Expose the shared multiwidget rendering template for this PostgreSQL widget.
- `templates/postgres` : This folder organizes Django-template resources for PostgreSQL-specific widgets. Its `widgets` child contains the split-array widget template, which includes the shared `multiwidget.html` template rather than defining standalone markup. No eligible files are listed directly in this folder. Merged `widgets/`: This folder contains one retained PostgreSQL widget template entry. Provide a navigation point for PostgreSQL widget template resources. Merged `widgets/`: Expose the shared multiwidget rendering template for this PostgreSQL widget.
- `templates` : This folder organizes Django-template resources for PostgreSQL-specific widgets. Its `postgres` child contains the split-array widget template index; that template includes Django's shared `multiwidget.html` renderer rather than defining standalone markup. No eligible files are listed directly in this folder. Merged `postgres/`: This folder organizes Django-template resources for PostgreSQL-specific widgets. Group PostgreSQL widget templates and direct agents to the relevant folder index. Merged `postgres/`: Provide a navigation point for PostgreSQL widget template resources. Merged `postgres/widgets/`: Expose the shared multiwidget rendering template for this PostgreSQL widget.

## Files
- `aggregates/general.py` (Size : 3317 bytes): Defines PostgreSQL general-purpose aggregates, including array, boolean, JSONB, bitwise, and string aggregation. The classes configure their SQL function names, output fields, and support for distinct values or ordering where applicable. The PostgreSQL-specific bitwise and string wrappers issue `RemovedInDjango2028Warning` deprecation warnings and delegate to corresponding Django ORM aggregates. `StringAgg` also wraps a string delimiter in `Value` to preserve its current literal behavior.
    - Tags: [aggregates, deprecation, django, jsonb, postgresql, warnings]
    - TODO/FIXME/NOTE: none

- `aggregates/mixins.py` (Size : 575 bytes): Defines `OrderableAggMixin`, a compatibility mixin that enables ordering for aggregate subclasses. Its subclass initialization emits a `RemovedInDjango2028Warning` directing users to configure `Aggregate.allow_order_by` instead. It then delegates subclass initialization to the parent implementation. The module contains no other aggregate behavior.
    - Tags: [aggregates, deprecation, django, mixin, postgresql, warnings]
    - TODO/FIXME/NOTE: none

- `aggregates/statistics.py` (Size : 1586 bytes): Implements PostgreSQL statistical and regression aggregate expressions, including correlation, covariance, averages, counts, and regression measures. These classes share `StatAggregate`, which configures a floating-point output by default and rejects missing `y` or `x` expressions. `CovarPop` selects sample or population covariance SQL, while `RegrCount` uses an integer output and returns zero for an empty result set. The remaining classes map to their corresponding PostgreSQL statistical SQL functions.
    - Tags: [aggregates, django, postgresql, regression, statistics]
    - TODO/FIXME/NOTE: none

- `aggregates/__init__.py` (Size : 67 bytes): Re-exports the general and statistical aggregate modules as the package-level public API. The wildcard imports make those modules' exported names available to callers importing this package. `NOQA` comments mark the imports as intentional despite lint rules. This file contains no aggregate implementation of its own.
    - Tags: [django, package-api, python]
    - TODO/FIXME/NOTE: none

- `apps.py` (Size : 4151 bytes): Configures the PostgreSQL contrib application and its setup and teardown behavior. On application readiness it updates PostgreSQL type introspection, registers connection type handlers, registers PostgreSQL lookups on character and text fields, and adds range serialization and index-expression wrappers. Its setting-change receiver reverses these registrations when the application is removed from `INSTALLED_APPS`.
    - Tags: [application-config, django-apps, postgresql, registration]
    - TODO/FIXME/NOTE: None.

- `constraints.py` (Size : 10497 bytes): Implements `ExclusionConstraint` for PostgreSQL exclusion constraints using GiST, Hash, or SP-GiST indexes. It validates configuration, resolves field expressions and conditions, constructs constraint SQL, deconstructs constraints for migrations, and checks candidate values against existing rows. Optional features include deferrability, included columns, and custom violation errors.
    - Tags: [constraints, django-orm, postgresql, sql, validation]
    - TODO/FIXME/NOTE: None.

- `expressions.py` (Size : 419 bytes): Defines `ArraySubquery`, a `Subquery` expression whose SQL template wraps a subquery in PostgreSQL's `ARRAY(...)` constructor. Its output field is an `ArrayField` based on the selected query's output field. This lets query results be represented as a PostgreSQL array expression.
    - Tags: [array, django-orm, expressions, postgresql, subquery]
    - TODO/FIXME/NOTE: None.

- `fields/array.py` (Size : 13588 bytes): Implements `ArrayField`, a Django model field that adapts a base field to PostgreSQL array storage, database preparation, forms, and serialization. It validates array elements and nested-array lengths, delegates value handling to the base field, and includes PostgreSQL type and collation information. Index and slice transforms map ORM expressions to PostgreSQL array subscripting. Registered lookups support containment, contained-by, exact, overlap, membership, and array length operations.
    - Tags: [array-field, django-orm, field-validation, postgresql, serialization, sql-transforms]

- `fields/citext.py` (Size : 1408 bytes): Defines the legacy `CICharField`, `CIEmailField`, and `CITextField` classes as Django field subclasses. Each class supplies removed-field system-check details, including its check identifier and a replacement suggestion using a non-deterministic case-insensitive collation. The module states that these definitions remain for historical migrations. It does not implement separate database storage or lookup behavior.
    - Tags: [case-insensitive-text, django-orm, historical-migrations, postgresql]

- `fields/hstore.py` (Size : 3500 bytes): Implements `HStoreField` for PostgreSQL maps whose values are strings or nulls. It validates map values, prepares keys and values for storage, and converts values to and from JSON for Python and serialized forms. The field integrates with Django's hstore form field and registers containment and key-related lookups. Dynamic key transforms and `keys`/`values` transforms expose hstore content through ORM expressions.
    - Tags: [django-orm, hstore-field, lookups, postgresql, serialization, transforms, validation]

- `fields/jsonb.py` (Size : 420 bytes): Defines the legacy PostgreSQL `JSONField` as a subclass of Django's built-in model `JSONField`. Its system-check metadata marks the PostgreSQL field as removed except for historical migration support and recommends the built-in field. The module adds no separate JSON storage or query implementation. Its responsibility is compatibility for existing migration references.
    - Tags: [django-orm, historical-migrations, json-field, postgresql]

- `fields/ranges.py` (Size : 12070 bytes): Implements Django model fields for PostgreSQL integer, big-integer, decimal, date-time, and date ranges, with range-boundary expressions and operator constants. The fields prepare Python inputs, convert serialized and database values, integrate with range form fields, and select PostgreSQL database types. Registered lookups and transforms expose containment, overlap, ordering, adjacency, endpoints, bounds, and emptiness through ORM expressions. It uses Django's PostgreSQL range types and a shared attribute helper when serializing endpoint values.
    - Tags: [django-orm, postgresql, range-fields, range-lookups, serialization, sql-transforms, validation]

- `fields/utils.py` (Size : 98 bytes): Defines `AttributeSetter`, a small helper that assigns a supplied name and value as an object's attribute. Array and range field serialization use it to present individual values through the attribute interface expected by base-field serializers. The helper contains no database or field-specific behavior. Its role is limited to supporting those serialization paths.
    - Tags: [attribute-helper, python, serialization-support]

- `fields/__init__.py` (Size : 153 bytes): Re-exports field APIs from the adjacent array, citext, hstore, JSON, and range modules. This makes their symbols available from the package namespace without adding field implementation of its own. The imports use each module's public exports. The file contains no additional runtime logic.
    - Tags: [field-exports, package-exports, python]

- `forms/array.py` (Size : 8672 bytes): Implements `SimpleArrayField` for delimiter-separated values and `SplitArrayField` with `SplitArrayWidget` for separate inputs. The fields delegate conversion and validation to a base field, prefix item errors with their positions, and support array length constraints and optional removal of trailing empty values.
    - Tags: [array, django-forms, form-fields, validation, widgets]
    - TODO/FIXME/NOTE: None.

- `forms/hstore.py` (Size : 1846 bytes): Implements `HStoreField`, a character form field that accepts JSON dictionary input and prepares dictionary values as JSON text. It reports invalid JSON or non-dictionary input through form validation errors, casts non-null values to strings, and compares changes after normalizing the initial value.
    - Tags: [django-forms, form-fields, hstore, json, validation]
    - TODO/FIXME/NOTE: None.

- `forms/ranges.py` (Size : 3771 bytes): Implements paired range widgets and a base multi-value field that converts two validated bounds into PostgreSQL range values. Specialized integer, decimal, date-time, and date fields select their corresponding base field and range type; the base class also applies optional default bounds and rejects reversed endpoints.
    - Tags: [django-forms, form-fields, postgres-ranges, validation, widgets]
    - TODO/FIXME/NOTE: None.

- `forms/__init__.py` (Size : 92 bytes): Re-exports the form APIs from the array, HStore, and range modules, with `NOQA` markers on the wildcard imports. It contains no independent field or widget implementation.
    - Tags: [django-forms, postgres, re-exports]
    - TODO/FIXME/NOTE: None.

- `functions.py` (Size : 263 bytes): Provides two Django ORM `Func` expressions for PostgreSQL SQL functions. `RandomUUID` emits `GEN_RANDOM_UUID()` and declares a UUID output field, while `TransactionNow` emits `CURRENT_TIMESTAMP` and declares a date-time output field. The module contains no additional query or connection setup.
    - Tags: [django-orm, functions, postgresql, sql]
    - TODO/FIXME/NOTE: None.

- `indexes.py` (Size : 8545 bytes): Implements PostgreSQL-specific Bloom, BRIN, B-tree, GIN, GiST, Hash, and SP-GiST model indexes on a shared `PostgresIndex` base. The base builds index SQL with its access method and optional `WITH` parameters, while subclasses validate and serialize their own options. `OpClass` adds a PostgreSQL operator class to a query expression.
    - Tags: [django-orm, indexes, migrations, postgresql, sql]
    - TODO/FIXME/NOTE: None.

- `jinja2/postgres/widgets/split_array.html` (Size: 54 bytes): Includes `django/forms/widgets/multiwidget.html`. Its content is therefore the shared multiwidget template rather than standalone markup. The file provides the widget template entry for this folder. Its observed content does not establish additional split-array-specific behavior.
  - Tags: [django, forms, jinja2, template, widgets]

- `lookups.py` (Size : 2069 bytes): Defines PostgreSQL operator lookups for containment, overlap, and key membership, plus unaccent and full-text-search transforms and trigram similarity lookups. The overlap lookup converts a right-hand-side ORM query to `ArraySubquery`; key-list lookups prepare their values for PostgreSQL operators. `SearchLookup` adapts ordinary expressions to `SearchVector` when needed.
    - Tags: [django-orm, lookups, postgresql, search, transforms]
    - TODO/FIXME/NOTE: None.

- `operations.py` (Size : 13020 bytes): Provides reversible migration operations for creating PostgreSQL extensions and collations, including named extension subclasses. It also implements concurrent index addition/removal and operations for adding unvalidated constraints and validating them later. Database operations honor backend and migration-router checks where applicable, and concurrent index operations reject execution inside a transaction.
    - Tags: [database-operations, django-migrations, extensions, indexes, postgresql]
    - TODO/FIXME/NOTE: None.

- `search.py` (Size : 16605 bytes): Implements PostgreSQL full-text-search expressions for vectors, queries, ranking, highlighted headlines, and lexeme composition, together with trigram similarity and distance functions. Search vectors and queries support configuration and expression combination, while query construction supports plain, phrase, raw, and web-search modes. The module also normalizes and quotes lexemes using the active psycopg adapter.
    - Tags: [django-orm, full-text-search, postgresql, trigram-search]
    - TODO/FIXME/NOTE: None.

- `serializers.py` (Size : 445 bytes): Defines a migration serializer for PostgreSQL range objects. It emits an import and representation for the object's class module, translating the legacy `psycopg2._range` implementation module to its public `psycopg2.extras` import path. This allows range values to be represented in migration code.
    - Tags: [django-migrations, postgresql, range-types, serialization]
    - TODO/FIXME/NOTE: None.

- `signals.py` (Size : 2961 bytes): Provides cached lookups for PostgreSQL hstore and citext type OIDs and registers database adapters when PostgreSQL connections are created. Separate implementations handle psycopg 3 and psycopg2, including hstore values and citext arrays. Registration skips non-PostgreSQL and dummy connections, and the psycopg2 path avoids registering handlers when the extension types are unavailable.
    - Tags: [database-connections, postgresql, psycopg, type-adapters]
    - TODO/FIXME/NOTE: None.

- `templates/postgres/widgets/split_array.html` (Size: 54 bytes): Includes `django/forms/widgets/multiwidget.html` for rendering. The file is exactly 54 bytes in the retained inventory. Its content is an include directive rather than standalone markup. No TODO, FIXME, or NOTE markers were found.
  - Tags: [array, postgres, template, widget]

- `utils.py` (Size : 2074 bytes): Defines `prefix_validation_error`, which adds a formatted prefix while preserving the underlying validation error data and nested error structure. `CheckPostgresInstalledMixin` adds a system-check error when PostgreSQL-specific indexes or constraints are used without the contrib application installed. These helpers are shared by package-level constraint and index implementations.
    - Tags: [django-checks, postgresql, utilities, validation]
    - TODO/FIXME/NOTE: None.

- `validators.py` (Size : 2892 bytes): Defines validators for PostgreSQL array lengths, required or restricted HStore keys, and numeric range bounds. The range validators compare values against range endpoints, and `KeysValidator` supports optional strict rejection of extra keys. Array length messages use lazy pluralization, and the key validator supports customized messages.
    - Tags: [array, hstore, postgresql, range-types, validation, validators]
    - TODO/FIXME/NOTE: None.

---

## Links Child Folder docmaps

None.

# Related Features

PostgreSQL-specific ORM query expressions and lookups, full-text and trigram search, model indexes and exclusion constraints, migration operations for extensions and collations, and database type adaptation. The child indexes cover PostgreSQL aggregates, fields, forms, and widget templates. Merged `aggregates/`: PostgreSQL aggregation through Django ORM queries, including general-purpose, statistical, and regression aggregate expressions. Merged `fields/`: This folder provides Django model-field support for PostgreSQL arrays, hstore maps, and range types, including associated ORM lookups and transforms. The legacy citext and PostgreSQL JSON field classes support historical migration references. Merged `forms/`: PostgreSQL-specific form handling for array, HStore, and range data. Merged `jinja2/`: PostgreSQL form widget rendering with Jinja2 templates. Merged `jinja2/postgres/`: PostgreSQL-specific form widget template rendering. Merged `jinja2/postgres/widgets/`: PostgreSQL split-array widget template rendering. Merged `templates/`: PostgreSQL array form widget templates. Merged `templates/postgres/`: PostgreSQL array form widget templates. Merged `templates/postgres/widgets/`: PostgreSQL array form widgets.

# Agent Guidance

## Read When

Working on PostgreSQL-specific Django ORM features, database setup and adapters, migration operations, indexes, constraints, or the location of related PostgreSQL fields and forms. Merged `aggregates/`: Working with PostgreSQL aggregate functions, aggregate expression options, output field inference, or aggregate deprecations. Merged `fields/`: Read this index when changing or tracing PostgreSQL-specific Django model fields, their ORM lookups and transforms, or historical migration compatibility. Merged `forms/`: Working on Django forms, input validation, or widgets for PostgreSQL-specific field types. Merged `jinja2/`: Locating or changing PostgreSQL Jinja2 widget templates. Merged `jinja2/postgres/`: Locating or changing a PostgreSQL Jinja2 widget template. Merged `jinja2/postgres/widgets/`: Changing the Jinja2 split-array widget template. Merged `templates/`: Locating or changing PostgreSQL widget templates. Merged `templates/postgres/`: Locating or changing a PostgreSQL widget template. Merged `templates/postgres/widgets/`: Changing PostgreSQL array widget template rendering.

## Modify When

The change concerns the direct implementations of PostgreSQL database integration, query expressions and lookups, index or constraint behavior, migration operations, validation helpers, or PostgreSQL type serialization. Merged `aggregates/`: Adding or changing PostgreSQL aggregate classes, their SQL function mappings, or package-level exports. Merged `fields/`: Modify `array.py`, `hstore.py`, or `ranges.py` when the corresponding field's value handling, validation, database representation, or query behavior changes. Update `citext.py` or `jsonb.py` for legacy field compatibility, and `__init__.py` when changing package-level exports. Merged `forms/`: Changing how these form fields parse, prepare, validate, or render PostgreSQL-specific values. Merged `jinja2/`: The requested change concerns organization of this template area. Merged `jinja2/postgres/`: The requested change concerns the PostgreSQL Jinja2 template folder structure. Merged `jinja2/postgres/widgets/`: The requested change concerns this include wrapper. Merged `templates/`: The requested change concerns organization of this template area. Merged `templates/postgres/`: The requested change concerns the PostgreSQL template folder structure. Merged `templates/postgres/widgets/`: The requested change concerns this shared multiwidget include.

## Avoid Modifying When

The requested behavior belongs specifically to aggregate classes, model fields, form fields, or widget templates; use the corresponding child folder index to locate those implementations. Merged `aggregates/`: Changing generic Django ORM aggregate behavior that is implemented outside this PostgreSQL-specific package. Merged `fields/`: Do not change these field modules for behavior owned by PostgreSQL backend connection setup, database adapters, or other PostgreSQL contrib features. Use the relevant backend or feature implementation instead. Merged `forms/`: The change concerns database storage or query behavior without affecting form input, validation, or rendering. Merged `jinja2/`: Changing shared widget rendering or PostgreSQL field behavior outside this folder. Merged `jinja2/postgres/`: Changing shared multiwidget rendering or PostgreSQL field behavior outside this folder. Merged `jinja2/postgres/widgets/`: Changing shared multiwidget behavior or PostgreSQL field logic. Merged `templates/`: Changing shared multiwidget rendering or PostgreSQL field behavior outside this folder. Merged `templates/postgres/`: Changing shared multiwidget rendering or PostgreSQL field behavior outside this folder. Merged `templates/postgres/widgets/`: Changing array form behavior implemented outside this template.

## Dependency Graph

Not generated. `dependencies` is empty; no dependencies were inferred.
