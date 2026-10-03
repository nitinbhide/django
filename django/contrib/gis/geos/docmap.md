---
folder: "django/contrib/gis/geos"
generated_on: "2026-10-03"
num_files: 15
semantic_tags: [binding, collections, coordinate-sequences, ctypes, django, exceptions, factory, gdal, geometry, geometry-collections, geometry-operations, geos, io, license, linear-referencing, list-interface, list-mixin, parsing, prepared-geometries, python, serialization, spatial-reference, topology, wkb, wkt]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package provides Django's Python interface to GEOS geometries and geometric operations. It exposes geometry constructors and type-specific objects alongside readers, writers, coordinate handling, and library initialization. Its wrappers manage GEOS pointers through ctypes and delegate spatial computations to GEOS, with GDAL used for selected conversions and transformations. The package also supplies list-like access and mutation for coordinate sequences and geometry collections.

## Major Responsibilities

The modules define geometry types, parsing and serialization, coordinate and collection management, spatial predicates and topology operations, prepared geometries, GEOS library loading, and the exception type used by this API.

## Technology Notes

The package calls the GEOS C API through Python `ctypes`. It integrates with Django's GDAL wrappers for geometry conversion and coordinate transformations, and optionally uses NumPy for coordinate arrays.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `__init__.py` (Size : 679 bytes): This module defines the public import surface for GeoDjango's GEOS API. It re-exports the geometry classes, readers and writers, factory helpers, exception, and GEOS version function from neighboring modules. These exports let callers import the common types from `django.contrib.gis.geos`. The module itself contains no geometry implementation.
    - Tags: [api, exports, geos, python]

- `base.py` (Size : 187 bytes): This module defines `GEOSBase` as a thin specialization of Django's `CPointerBase`. It associates GEOS pointer failures with the package's `GEOSException`. The class provides the shared base for pointer-backed GEOS objects. It contains no geometry operations.
    - Tags: [ctypes, exceptions, geos, pointers, python]

- `collections.py` (Size : 4142 bytes): This module implements `GeometryCollection` and the MultiPoint, MultiLineString, and MultiPolygon types. Collections validate allowed member types, clone geometry pointers, and expose iteration, indexing, and rebuilding behavior. It also provides tuple and KML representations. The implementations reuse the base geometry and type-specific classes.
    - Tags: [collections, geometry, geos, list-interface, python]

- `coordseq.py` (Size : 9084 bytes): This module wraps GEOS coordinate sequences used by points, lines, and rings. It provides indexing, iteration, coordinate ordinate access, cloning, and tuple or KML output. The wrapper handles 2D, Z, M, and combined coordinate dimensions through the GEOS C API. Its `hasm` support is gated on GEOS 3.14 or newer.
    - Tags: [coordinate-sequences, ctypes, geos, python, z-dimensions]
    - TODO/FIXME/NOTE:
        - TODO (line 23): `# TODO when dropping support for GEOS 3.13 the z argument can be`

- `error.py` (Size : 109 bytes): This module defines `GEOSException`, the base exception for errors related to GEOS. The class derives directly from Python's `Exception`. Its docstring identifies its use for GEOS-related failures. No other behavior is implemented here.
    - Tags: [exceptions, geos, python]

- `factory.py` (Size : 994 bytes): This module provides `fromfile()` and `fromstr()` helpers for creating `GEOSGeometry` instances. `fromfile()` accepts a filename or open file-like object and interprets readable text as WKT or hexadecimal geometry where possible. Other byte input is passed to geometry construction as a memory view. `fromstr()` forwards a string and keyword arguments to `GEOSGeometry`.
    - Tags: [factory, geos, parsing, python, wkb, wkt]

- `geometry.py` (Size : 28380 bytes): This module implements the general GEOS geometry wrapper and its shared base behavior. It constructs geometry objects from WKT, EWKT, HEXEWKB, GeoJSON, WKB memory views, or GEOS pointers, and maps GEOS type identifiers to concrete geometry classes. It exposes serialization, coordinate and SRID information, predicates, measurements, topology operations, prepared geometry, and GDAL-backed conversion and transformation. It also implements pointer-safe cloning and pickling, with a configurable limit on nested geometry collections during parsing.
    - Tags: [ctypes, gdal, geometry, geometry-operations, geos, parsing, prepared-geometries, python, serialization, spatial-reference, topology, wkb, wkt]
    - TODO/FIXME/NOTE:
        - NOTE (line 414): `        Return the WKB of this Geometry in hexadecimal form. Please note`

- `io.py` (Size : 827 bytes): This module exposes the Python-facing WKB and WKT reader and writer classes. The reader wrappers convert the underlying prototype results into `GEOSGeometry` objects. The low-level reader and writer implementations are imported from the prototypes package. `__all__` defines the reader and writer names exported by this module.
    - Tags: [geos, io, parsing, python, serialization, wkb, wkt]

- `libgeos.py` (Size : 5364 bytes): This module initializes access to the GEOS shared library and defines ctypes pointer structures and utility wrappers. Library discovery supports a configured path and platform-specific GEOS library names. It configures error and notice callbacks, lazily loads the C library and GEOS functions, and exposes version helpers. `GEOSFuncFactory` obtains context-aware function wrappers from the thread-safe prototypes module when called.
    - Tags: [ctypes, geos, library-loading, pointers, python, thread-safe]

- `LICENSE` (Size : 1557 bytes): This file contains a three-clause BSD license notice attributed to Justin Bronn for 2007–2009. It states redistribution conditions for source and binary forms and restricts endorsement using contributor names. The disclaimer excludes warranties and liability. It is license text rather than implementation documentation.
    - Tags: [bsd, license]

- `linestring.py` (Size : 6560 bytes): This module implements `LineString` and `LinearRing` geometries from coordinate sequences, point objects, or supported NumPy arrays. It validates coordinate counts and dimensions, initializes GEOS coordinate sequences, and supports list-style access and updates. The classes expose tuple, array, and per-axis coordinate views. Linear geometries inherit interpolation, projection, and related operations from `LinearGeometryMixin`.
    - Tags: [coordinate-sequences, geos, linear-referencing, linestring, python]

- `mutable_list.py` (Size : 10437 bytes): This module defines `ListMixin`, a reusable list-interface implementation for classes with custom storage. Subclasses provide item retrieval, rebuilding, and length behavior, with optional item assignment and type constraints. The mixin implements indexing, slicing, comparisons, arithmetic, and list mutations while rebuilding backing data as needed. It documents that generators used in rebuilding can depend on the previous internal items.
    - Tags: [list-interface, list-mixin, mutation, python, sequences]
    - TODO/FIXME/NOTE:
        - NOTE (line 28): `        Note that if _get_single_internal and _get_single_internal return`
        - NOTE (line 35): `        NOTE: items may be a generator which calls _get_single_internal.`

- `point.py` (Size : 4953 bytes): This module implements GEOS `Point` objects from coordinate tuples or individual numeric ordinates. It creates coordinate sequences through GEOS prototypes and supports empty points, indexing, coordinate mutation, and tuple access. Pickling and OGR pointer conversion account for empty points. It also exposes X, Y, and optional Z coordinate properties.
    - Tags: [coordinate-sequences, gdal, geos, point, python]

- `polygon.py` (Size : 6899 bytes): This module implements `Polygon` geometries from an exterior ring and optional interior rings. It constructs and clones GEOS ring pointers, supports iteration and list-style updates, and provides bounding-box construction. Properties expose ring counts, shell and exterior-ring aliases, coordinate tuples, and KML output. Ring inputs may be `LinearRing` instances or sequences that can initialize one.
    - Tags: [geos, linear-rings, polygon, python]

- `prepared.py` (Size : 1628 bytes): This module wraps GEOS prepared geometries for repeated spatial predicate operations. `PreparedGeometry` retains its source geometry to keep the underlying object alive and initializes a prepared GEOS pointer. It exposes prepared forms of predicates including contains, covers, intersects, and within. Destruction is delegated to the prepared-geometry prototypes.
    - Tags: [ctypes, geos, predicates, prepared-geometries, python]

---

## Links Child Folder docmaps
- `prototypes/docmap.md` — Documents the low-level ctypes prototypes for GEOS geometry construction, I/O, predicates, measurements, topology operations, and thread-safe calls.

# Related Features

GEOS-backed geometry creation and manipulation, geometry collection and coordinate handling, WKB/WKT serialization, spatial predicates and topology, and GDAL-assisted geometry conversion and transformation.

# Agent Guidance

## Read When

Changing GEOS geometry construction, geometry-type behavior, coordinate handling, collection semantics, serialization, spatial operations, or GEOS library loading.

## Modify When

The requested behavior is implemented in the Python-facing GEOS wrappers or their pointer, coordinate-sequence, collection, or I/O adapters.

## Avoid Modifying When

The change is confined to the low-level GEOS C function prototypes, error checking, or thread-safe function adaptation; inspect `prototypes/docmap.md` and its source files for those responsibilities.
