---
folder: "django/contrib/gis/db/backends"
generated_on: "2026-10-02"
num_files: 34
semantic_tags: [backend, binary-format, database, database-backend, database-backends, database-features, database-introspection, database-operations, database-schema, django, django-models, gdal, geography, geometry, gis, mariadb, mysql, oracle, postgis, postgresql, psycopg, python, raster, schema-metadata, serialization, spatial, spatial-database, spatial-index, spatial-lookups, spatial-operations, spatial-reference-system, spatialite, sql, sqlite, table-metadata, type-adaptation]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder contains shared GIS backend support and database-specific GIS adapters. Its direct files provide package initialization and spatial lookup SQL representation, while child folders implement base, MySQL, Oracle, PostGIS, and SpatiaLite backends. The backend indexes cover database capabilities, geometry handling, introspection, and spatial operations. The folder groups these implementations under Django's GIS database backend package. Merged `base/`: This folder contains shared primitives for GIS database backends. Merged `mysql/`: This folder adapts Django's MySQL backend for GIS operations. Merged `oracle/`: This folder implements Django's Oracle GIS backend as an extension of the core Oracle backend. Merged `spatialite/`: This directory implements Django's GIS database backend for SpatiaLite, layered over the SQLite backend and shared spatial-backend abstractions. Merged `postgis/`: This package implements Django's PostGIS database backend on top of PostgreSQL. It provides backend-specific connection and data adaptation, feature flags, introspection, models, SQL operations, and schema editing. Geometry and raster support includes PostGIS value conversion and raster serialization. This standalone docmap covers the ten direct inventory entries; dependencies are not inferred.

## Major Responsibilities

Provides shared GIS SQL lookup behavior and navigation to the database-specific GIS backend implementations. Merged `base/`: Provide reusable geometry adaptation, capability reporting, spatial-reference access, and database operation hooks. Merged `mysql/`: Provide GIS-specific database wrapper, capability, introspection, operation, and schema behavior for MySQL and MariaDB. Merged `oracle/`: Provide Oracle-specific GIS backend wiring, geometry adaptation, metadata access, spatial operations, and schema editing. Merged `spatialite/`: Connect SQLite database operations to SpatiaLite geometry functions, metadata, and schema behavior. Merged `postgis/`: Provide PostGIS connection wiring, spatial feature declarations, geometry and raster adapters, database introspection, SQL operations, metadata models, and spatial schema editing.

## Technology Notes

The direct implementation uses Python and SQL-template rendering for spatial lookup operations. Child indexes document the database-specific backend technologies. Merged `base/`: Python, Django database backends, GEOS/GDAL spatial data, and WKT. Merged `mysql/`: Python, Django database backends, MySQL, MariaDB, and spatial SQL. Merged `oracle/`: Python, Django database backends, Oracle Spatial, and spatial SQL. Merged `spatialite/`: Python, Django database backends, SQLite, and SpatiaLite.

Merged `postgis/`: Python backend code integrates PostgreSQL/PostGIS with Psycopg, GDAL, and Django's GIS abstractions.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `base` : This folder contains shared primitives for GIS database backends. `adapter.py` provides a WKT-backed geometry adapter, while `features.py` declares common spatial capability defaults and support checks. `models.py` exposes spatial-reference details, and `operations.py` defines hooks for spatial SQL, conversions, lookups, aggregates, and function naming. Backend-specific behavior is represented through overridable methods and capability values. Provide reusable geometry adaptation, capability reporting, spatial-reference access, and database operation hooks.
- `mysql` : This folder adapts Django's MySQL backend for GIS operations. It supplies backend wiring, spatial feature flags, geometry introspection, spatial SQL operations, and spatial-index schema handling. Several capabilities vary between MySQL and MariaDB or by MariaDB version. The retained inventory lists six direct entries. Provide GIS-specific database wrapper, capability, introspection, operation, and schema behavior for MySQL and MariaDB.
- `oracle` : This folder implements Django's Oracle GIS backend as an extension of the core Oracle backend. It adapts geometry values and provides Oracle-specific spatial capabilities, SQL operations, and metadata models. Introspection and schema management connect GIS fields to Oracle geometry metadata and spatial indexes. The source records Oracle-specific limitations and version-dependent test skips. Provide Oracle-specific GIS backend wiring, geometry adaptation, metadata access, spatial operations, and schema editing.
- `postgis` : This package implements Django's PostGIS database backend on top of PostgreSQL. It provides backend-specific connection and data adaptation, feature flags, introspection, models, SQL operations, and schema editing. Geometry and raster support includes PostGIS value conversion and raster serialization. This standalone docmap covers the ten direct inventory entries; dependencies are not inferred. Provide PostGIS connection wiring, spatial feature declarations, geometry and raster adapters, database introspection, SQL operations, metadata models, and spatial schema editing. Python backend code integrates PostgreSQL/PostGIS with Psycopg, GDAL, and Django's GIS abstractions.
- `spatialite` : This directory implements Django's GIS database backend for SpatiaLite, layered over the SQLite backend and shared spatial-backend abstractions. `base.py` assembles the backend and loads the SpatiaLite extension. `operations.py` and `schema.py` handle spatial SQL and geometry-aware schema changes, while `features.py`, `introspection.py`, and `models.py` cover capabilities and spatial metadata. The retained inventory lists nine Python files, including an empty `__init__.py`. Connect SQLite database operations to SpatiaLite geometry functions, metadata, and schema behavior.

## Files
- `base/adapter.py` (Size: 618 bytes): Defines `WKTAdapter` for adapting geometries to WKT. Initialization stores the geometry's WKT and SRID. Equality and hashing use those two values, while string conversion returns the WKT. `_fix_polygon()` returns its input unchanged as an Oracle hook.
  - Tags: [geometry, wkt]

- `base/features.py` (Size: 3,857 bytes): Defines `BaseSpatialFeatures` with default GIS capability flags for storage, functions, lookups, and aggregates. Properties derive selected capabilities from the connection's operators, functions, and disallowed aggregates. Dynamic `has_<function>_function` access checks the unsupported-function set and rejects unregistered names. The class provides shared capability behavior for spatial database backends.
  - Tags: [database-capabilities, gis, spatial-backend]

- `base/models.py` (Size: 3,826 bytes): Defines `SpatialRefSysMixin` for exposing spatial-reference information from WKT or PROJ.4 text. Its cached `srs` property tries both representations and reports both errors if neither can be parsed. Properties expose ellipsoid, spheroid, datum, projection, and unit details. Class methods retrieve units and spheroid parameters, and string conversion returns the spatial reference representation.
  - Tags: [coordinate-systems, gdal, spatial-reference]

- `base/operations.py` (Size: 7,351 bytes): Defines `BaseSpatialOperations` with backend flags, function mappings, unsupported-function names, and aggregate defaults. It builds geometry placeholders, applying SRID transformations when required, and selects placeholder forms based on backend features. It provides hooks for spatial types, distance handling, aggregate naming, geometry conversion, and column discovery. Database converters and area/distance unit attributes are handled in the base implementation.
  - Tags: [database-operations, geometry, gis, spatial-sql]

- `mysql/base.py` (Size: 512 bytes): Subclasses Django's MySQL `DatabaseWrapper`. It connects the wrapper to the GIS-specific features, introspection, operations, and schema editor classes. Those classes are imported from sibling modules. The file provides the backend wrapper wiring for this package.
  - Tags: [database, gis, mysql, spatial]

- `mysql/features.py` (Size: 1,400 bytes): Combines the base spatial and MySQL feature classes. It declares unsupported spatial capabilities and GeoJSON options for this backend. It checks MariaDB status when determining geometry-field unique-index support. It also adds a MariaDB-specific skipped test for nested geometry collections.
  - Tags: [capabilities, gis, mariadb, mysql, spatial]

- `mysql/introspection.py` (Size: 1,635 bytes): Extends MySQL database introspection for GIS fields. It maps MySQL's geometry field type to Django's `GeometryField`. Its geometry-type lookup describes the table and converts the matching column type through `OGRGeomType`. It reports spatial-index support for MyISAM, Aria, and InnoDB storage engines.
  - Tags: [geometry, gis, introspection, mysql, spatial-index]

- `mysql/operations.py` (Size: 5,393 bytes): Combines Django's spatial and MySQL database operations. It defines geometry serialization, spatial operator mappings, aggregate availability, and unsupported spatial functions. Several mappings and restrictions depend on whether the connection is MariaDB and, in some cases, its version. It also converts database geometry values to GEOS objects and handles distance lookup parameters.
  - Tags: [aggregation, gis, mysql, spatial-functions, spatial-lookups]

- `mysql/schema.py` (Size: 3,709 bytes): Extends MySQL's schema editor for GIS fields. It creates spatial indexes only for eligible non-null geometry fields and supported storage engines, logging when an index cannot be created. It also handles spatial-index removal during field deletion and updates during field alterations. Spatial-index SQL and names are built using the connection's identifier-quoting operation.
  - Tags: [database, gis, mysql, schema-editor, spatial-index]

- `oracle/adapter.py` (Size: 2,085 bytes): Defines `OracleSpatialAdapter` as the Oracle implementation of Django's WKT adapter. It specifies Oracle's CLOB input size and captures each geometry's WKT and SRID. Before serialization, it checks polygons and geometry collections for Oracle's required ring orientation. When necessary, it clones the geometry and reverses incorrectly oriented rings.
  - Tags: [adapter, django, geometry, oracle, spatial, wkt]

- `oracle/base.py` (Size: 521 bytes): Defines the GIS `DatabaseWrapper` by extending Django's Oracle wrapper. It selects the Oracle GIS schema editor for schema changes. It registers the backend's GIS-specific features, introspection, and operations classes. This file connects the general Oracle backend with the GIS implementations in this directory.
  - Tags: [backend, database, django, oracle, spatial]

- `oracle/features.py` (Size: 2,019 bytes): Defines Oracle's GIS feature flags by combining the GIS base features with the Oracle database features. It declares supported and unsupported spatial capabilities, including SRS entries, geometry introspection, geodetic perimeter, and GeoJSON options. Its `django_test_skips` property adds skips for unsupported spatial constraints and nested geometry collections. It conditionally adds further skips for Oracle 23.9 and later.
  - Tags: [capabilities, django, oracle, spatial, testing]

- `oracle/introspection.py` (Size: 1,958 bytes): Extends Oracle database introspection to map Oracle object values to Django `GeometryField`. `get_geometry_type()` queries `USER_SDO_GEOM_METADATA` for a column's dimension and SRID. It returns generic geometry-field parameters, omitting the default SRID 4326 and default two-dimensional setting. A comment records an unimplemented investigation into finding a more specific geometry field type.
  - Tags: [database, django, introspection, oracle, spatial]
  - TODO: `TODO` at line 35

- `oracle/models.py` (Size: 2,147 bytes): Defines unmanaged Django models for Oracle's spatial metadata tables. `OracleGeometryColumns` maps geometry-column metadata to `USER_SDO_GEOM_METADATA`, while `OracleSpatialRefSys` maps spatial reference data to `CS_SRS`. The model fields expose table, column, SRID, WKT, and coordinate-system details used by the backend. A TODO records missing support for the metadata table's `diminfo` column.
  - Tags: [django, metadata, models, oracle, spatial, spatial-reference]
  - TODO/FIXME/NOTE: `note` at line 5; `TODO` at line 21

- `oracle/operations.py` (Size: 9,476 bytes): Defines Oracle spatial operators, lookup SQL, function mappings, and GIS database operations. It handles geometry conversion, distance parameters, aggregate names, quoting, and geometry metadata model access. A module comment notes that WKT support is broken on Oracle XE and a TODO requests verification of the `intersects` mapping against `ST_Intersects()`. It also declares spatial functions unsupported by this backend, with a version-dependent exception for `GeometryType`.
  - Tags: [aggregates, django, geometry, oracle, spatial, sql]
  - TODO/FIXME/NOTE: `note` at line 5; `TODO` at line 109

- `oracle/schema.py` (Size: 5,581 bytes): Extends Oracle's schema editor with GIS-specific metadata and spatial-index SQL. It queues geometry metadata insertion when geometry columns are created, then executes the queued SQL after model or field creation. It removes table or column metadata and updates spatial indexes as fields change. Spatial index names are truncated to Oracle's 30-character limit for backwards compatibility.
  - Tags: [database, django, geometry, oracle, schema, spatial]

- `postgis/adapter.py` (Size: 2,043 bytes): Defines `PostGISAdapter` to prepare GEOS geometries and GDAL rasters for PostgreSQL/PostGIS. Geometry values are serialized as EWKB, while rasters are converted with `to_pgraster()`. The adapter provides Psycopg quoting behavior and emits geometry, geography, or raster SQL representations. It also defines equality and hashing using the serialized value.
  - Tags: [geometry, postgis, postgresql, python, raster, sql]

- `postgis/base.py` (Size: 5,954 bytes): Defines the PostGIS `DatabaseWrapper` by extending Django's PostgreSQL wrapper. It selects PostGIS-specific operations, features, introspection, and schema-editor classes, while using PostgreSQL classes for the no-database alias. It checks for the PostGIS extension and initializes it when missing. For Psycopg 3, it fetches PostGIS type information and registers geometry, geography, and raster adapters and loaders.
  - Tags: [database-backend, postgis, postgresql, psycopg, python, type-adaptation]

- `postgis/const.py` (Size: 2,071 bytes): Defines lookup tables for converting pixel types between GDAL and PostGIS. It provides the struct format for PostGIS raster headers and band values, plus their byte sizes. The constants also define the raster pixel-type mask and the no-data flag used when packing or unpacking band data. These definitions are consumed by the raster conversion code.
  - Tags: [binary-format, gdal, postgis, python, raster, serialization]

- `postgis/features.py` (Size: 468 bytes): Defines PostGIS database feature flags by combining Django's spatial and PostgreSQL feature classes. It declares support for geography, 3D storage and functions, rasters, and empty geometries. It also sets the behavior for empty spatial intersections. The module contains feature declarations rather than query or conversion logic.
  - Tags: [database-features, geography, postgis, python, raster, spatial-database]

- `postgis/introspection.py` (Size: 3,258 bytes): Defines PostGIS-specific database introspection on top of PostgreSQL introspection. It lazily queries PostgreSQL type OIDs for geometry and geography and adds those types to Django's reverse field mapping. It excludes PostGIS metadata tables and views from ordinary table introspection. For geometry columns, it queries PostGIS metadata to determine the Django field type and non-default geography, SRID, and dimension parameters.
  - Tags: [database-introspection, geography, geometry, postgis, python, schema-metadata]

- `postgis/models.py` (Size: 2,075 bytes): Defines unmanaged Django models for PostGIS's `geometry_columns` view and `spatial_ref_sys` table. The geometry-columns model exposes table, column, coordinate-dimension, SRID, and geometry-type metadata. It provides methods naming the metadata columns used for feature-table and geometry-column identification. The spatial-reference model uses `SpatialRefSysMixin` and exposes its stored spatial reference text as `wkt`.
  - Tags: [django-models, postgis, python, spatial-reference-system, table-metadata]

- `postgis/operations.py` (Size: 17,596 bytes): Defines PostGIS spatial database operations, including lookup operators for geometry, geography, and raster values. It constructs SQL behavior for raster-to-polygon conversion, geography casts, spatial field types, distance lookups, and SRID transformations. It also provides PostGIS version queries, geometry and extent result conversion, raster parsing, and spatial aggregate naming. The operations class links query behavior to the backend's adapter and metadata models.
  - Tags: [database-operations, geography, geometry, postgis, python, raster, spatial-lookups, sql]
  - TODO/FIXME/NOTE: `TODO` at line 255: `Support 'M' extension.`

- `postgis/pgraster.py` (Size: 4,740 bytes): Implements conversion between PostGIS raster hex data and dictionaries consumable by `GDALRaster`. It packs and unpacks raster headers and band data using the format definitions in `const.py`. Parsing preserves dimensions, SRID, scale, origin, skew, band data, and optional no-data values. It raises `ValidationError` when bands in one raster do not share a pixel type.
  - Tags: [binary-format, gdal, postgis, python, raster, serialization]

- `postgis/schema.py` (Size: 4,859 bytes): Defines a PostgreSQL schema editor with PostGIS-specific spatial index and column-alteration behavior. Spatial indexes use GiST; raster indexes wrap the raster expression with `ST_ConvexHull`, and multidimensional geometry indexes can use the ND operator class. The editor handles spatial-index creation and deletion when fields change and uses `ST_Force3D` or `ST_Force2D` for dimensionality changes. It delegates general schema work to Django's PostgreSQL schema editor.
  - Tags: [database-schema, geometry, postgis, python, raster, spatial-index]
  - TODO/FIXME/NOTE: `Note` at line 105: `hull of the raster. Note that expressions is None here since`

- `spatialite/adapter.py` (Size: 328 bytes): Adapts GIS geometry values for SQLite's database protocol. `SpatiaLiteAdapter` subclasses the shared `WKTAdapter`. Its `__conform__` method returns the adapter's string representation for SQLite's `PrepareProtocol`. No other adaptation behavior is defined here.
  - Tags: [django, geometry, sqlite, wkt]

- `spatialite/base.py` (Size: 3,297 bytes): Defines the SpatiaLite `DatabaseWrapper` on top of Django's SQLite wrapper. It configures the backend's client, features, introspection, operations, and schema editor classes. It searches configured and system library names, then loads the SpatiaLite extension when opening a connection. During database preparation, it initializes spatial metadata when the `geometry_columns` table is empty, choosing the initialization function by SpatiaLite version.
  - Tags: [database-connection, django, extension-loading, spatialite, sqlite]

- `spatialite/client.py` (Size: 143 bytes): Provides the command-line client configuration for the SpatiaLite backend. `SpatiaLiteClient` subclasses SQLite's `DatabaseClient`. It sets the executable name to `spatialite`. No additional client behavior is implemented here.
  - Tags: [database-client, django, spatialite, sqlite]

- `spatialite/features.py` (Size: 902 bytes): Defines database capability flags and test-skip behavior for SpatiaLite. `DatabaseFeatures` combines shared spatial features with SQLite features. It declares 3D storage support and marks geometry-column alteration as unimplemented. Cached properties determine geodetic-area support from the geometry library and skip a distance-lookup test unsupported by SpatiaLite.
  - Tags: [database-features, django, gis, spatialite, sqlite]

- `spatialite/introspection.py` (Size: 3,215 bytes): Extends SQLite database introspection for spatial columns and indexes. Its flexible field lookup maps supported geometry type names to Django's `GeometryField`. `get_geometry_type()` reads geometry type, coordinate dimension, and SRID from `geometry_columns`, then returns the field type and non-default parameters. `get_constraints()` adds enabled spatial indexes from the same metadata table to SQLite's constraint results.
  - Tags: [database-introspection, geometry, gis, spatial-metadata, spatialite]

- `spatialite/models.py` (Size: 2,001 bytes): Models SpatiaLite's `geometry_columns` and `spatial_ref_sys` metadata tables. Both models are unmanaged and assigned to Django's `gis` app. `SpatialiteGeometryColumns` exposes geometry-column metadata and helpers for its table-name and geometry-column fields. `SpatialiteSpatialRefSys` uses `SpatialRefSysMixin` and exposes `srtext` through its `wkt` property.
  - Tags: [django-models, gis, spatial-metadata, spatial-reference, spatialite]

- `spatialite/operations.py` (Size: 8,922 bytes): Implements SpatiaLite-specific GIS database operations on top of shared spatial operations and SQLite operations. It defines spatial lookup operators, SQL function-name mappings, aggregate names, and unsupported functions based on library versions. Its methods provide version and library queries, geometry type handling, distance parameters, and conversion of returned geometry data. It also supplies the backend's geometry metadata model classes.
  - Tags: [gis, geometry, spatial-operators, spatialite, sql-functions]

- `spatialite/schema.py` (Size: 7,545 bytes): Implements geometry-aware schema editing on top of SQLite's schema editor. It creates geometry columns and spatial indexes through SpatiaLite functions, and tracks those statements while creating models. It handles geometry metadata and spatial indexes during field removal, model deletion, and table renaming. `remove_field()` rebuilds the table for geometry fields because they have no database type and are managed through stored procedures.
  - Tags: [database-schema, geometry-columns, migrations, spatial-index, spatialite]
  - TODO/FIXME/NOTE: `NOTE` at line 128

- `utils.py` (Size : 818 bytes): This module defines `SpatialOperator`, which stores an operation name and function for GIS lookups. Its SQL rendering uses a template that can represent either a function call or an operator expression. The `as_sql()` method combines the stored values with the lookup template and parameters. The module provides shared SQL-generation support for GIS backend lookups.
    - Tags: [database-operations, gis, spatial-lookups, sql]

## Links Child Folder docmaps
No child folder docmaps.

# Related Features

Shared GIS database lookup SQL and database-specific GIS backend implementations for MySQL, Oracle, PostGIS, and SpatiaLite. Merged `base/`: Shared GIS backend capabilities and operations. Merged `mysql/`: GIS support for MySQL and MariaDB. Merged `oracle/`: Oracle GIS backend, metadata tables, and spatial indexes. Merged `spatialite/`: SpatiaLite GIS backend, geometry metadata, and spatial indexes.

# Agent Guidance

## Read When

Changing shared GIS backend lookup SQL or deciding which database-specific backend folder owns a change. Merged `base/`: Changing common spatial backend behavior or a backend-specific subclass hook. Merged `mysql/`: Changing MySQL GIS capabilities, geometry handling, or spatial indexes. Merged `oracle/`: Changing Oracle-specific spatial database behavior or its metadata handling. Merged `spatialite/`: Changing SpatiaLite backend connections, spatial SQL, schema, or metadata.

## Modify When

The requested change concerns `SpatialOperator` or shared backend behavior in the direct files; use a child index for database-specific behavior. Merged `base/`: The requested GIS database behavior belongs in a shared backend primitive. Merged `mysql/`: The requested database behavior is specific to this backend. Merged `oracle/`: The behavior is specific to the Oracle GIS backend. Merged `spatialite/`: The behavior is specific to the SpatiaLite backend.

## Avoid Modifying When

Changing one database backend's implementation without a shared behavior requirement. Merged `base/`: The change is specific to one database backend. Merged `mysql/`: Changing shared GIS backend behavior or another database backend. Merged `oracle/`: Changing shared spatial operations or other database backends. Merged `spatialite/`: Changing shared GIS database behavior or a different database backend.
