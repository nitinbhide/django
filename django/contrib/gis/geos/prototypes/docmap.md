---
folder: "django/contrib/gis/geos/prototypes"
generated_on: "2026-10-02"
num_files: 10
semantic_tags: [ctypes, geometry, geos, prototypes, spatial-operations]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder provides `ctypes` prototypes for GEOS geometry and spatial operations. It covers geometry construction and destruction, coordinate sequences, I/O formats, predicates, measurements, and topology. Shared factories and error checks convert C API results and statuses into Python-facing behavior. Thread-local context and I/O helpers support safe GEOS calls and reader/writer reuse.

## Major Responsibilities

Defines the low-level GEOS C API bindings used by higher-level geometry classes, including result validation, memory management, and thread-safe call adaptation.

## Technology Notes

The modules wrap GEOS C functions with Python `ctypes` and use GEOS context-aware function variants for thread safety.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `__init__.py` (Size : 1560 bytes): This module re-exports GEOS ctypes prototypes from coordinate-sequence, geometry, predicate, topology, and miscellaneous operation modules. It provides a unified import surface for these related bindings. Explicit import lists keep the package namespace controlled. The file organizes exports rather than implementing the wrapped operations.
    - Tags: [aggregate, api, exports, geos, imports, prototypes, reexport]

- `coordseq.py` (Size : 3594 bytes): This module defines ctypes prototypes for GEOS coordinate-sequence operations. It covers construction, cloning, coordinate ordinates, and dimension or orientation predicates. Factory classes standardize creation of the wrapped functions and their error checking. By-reference outputs are extracted for coordinate values.
    - Tags: [construction, coordinate-sequences, ctypes, error-checking, factories, geos, ordinate, predicates]

- `errcheck.py` (Size : 2900 bytes): This module centralizes error checking for GEOS ctypes calls. It converts status codes and invalid results into exceptions and extracts by-reference values. It handles geometry, numeric, predicate, and string outputs, including freeing GEOS-allocated strings. The helpers mediate between C return values and higher-level Python code.
    - Tags: [ctypes, error-checking, exceptions, geos, memory-management, status-codes, validation]

- `geom.py` (Size : 3494 bytes): This module defines ctypes prototypes for GEOS geometry construction and manipulation. It covers points, lines, rings, polygons, collections, cloning, destruction, ring access, coordinates, and SRID handling. Factory classes configure platform-sensitive argument and return types. Specialized error checks support memory management and exception propagation.
    - Tags: [construction, ctypes, destruction, factories, geometry-operations, geos, memory-management, srid]

- `io.py` (Size : 17467 bytes): This module wraps GEOS WKT and WKB readers and writers. It accepts string, byte, and memoryview inputs and manages reusable reader/writer objects per thread. Geometry-collection parsing applies a recursion limit to constrain deeply nested input, and handling accounts for GEOS version differences. Reader and writer settings include precision and byte order.
    - Tags: [collections, ctypes, formats, geos, io, memory-management, parsing, readers, security, thread-local, validation, wkb, wkt, writers]

- `misc.py` (Size : 1202 bytes): This module defines ctypes prototypes for miscellaneous GEOS measurements and validity information. It provides area, distance, and length operations with by-reference numeric result handling. It also retrieves validity-reason strings and frees the associated GEOS memory. A factory class standardizes error handling for measurement calls.
    - Tags: [area, ctypes, distance, geometry-operations, geos, length, measurement, reason, validation]

- `predicates.py` (Size : 1753 bytes): This module defines factories for unary and binary GEOS spatial predicates. Unary predicates test individual geometry properties such as emptiness, validity, closure, and simplicity. Binary predicates evaluate spatial relationships between geometries. The factories standardize boolean conversion and error handling, including specialized equality and relationship tests.
    - Tags: [binary-predicates, ctypes, geos, predicates, relationships, spatial-analysis, unary-predicates]

- `prepared.py` (Size : 1201 bytes): This module wraps prepared-geometry operations for repeated spatial predicate checks. It provides constructors and destructors for prepared geometry resources. The prototypes include binary predicates such as contains, covers, crosses, and intersects. Prepared forms allow the same source geometry to be reused across multiple predicate calls.
    - Tags: [ctypes, geos, optimization, predicates, prepared-geometries, spatial-analysis]

- `threadsafe.py` (Size : 2388 bytes): This module adapts standard GEOS ctypes functions to their context-aware thread-safe variants. `GEOSFunc` injects a per-thread context handle as the first function argument. It keeps context initialization lazy and proxies function argument, return, and error-check properties. This wrapper lets callers use the thread-safe APIs through a common function interface.
    - Tags: [ctypes, geos, initialization, property-proxying, thread-local, thread-safe, wrapper]

- `topology.py` (Size : 2401 bytes): This module defines ctypes prototypes for unary and binary GEOS topology operations. Unary operations include boundary, convex hull, centroid, and simplification; binary operations include union, intersection, difference, and symmetric difference. It also wraps project and interpolate linear-reference operations and normalized variants. Return values use geometry or string types with standardized error checks.
    - Tags: [boundary, buffer, ctypes, difference, geos, intersection, linear-referencing, simplification, topology, union]

## Links Child Folder docmaps

None.

# Related Features

Low-level GEOS bindings for geometry construction, serialization, spatial predicates, measurement, topology, and thread-safe operation.

# Agent Guidance

## Read When

Changing GEOS C API bindings or how GEOS results, errors, and contexts are handled.

## Modify When

The requested change concerns prototype signatures, error conversion, geometry I/O, or thread-safe GEOS wrappers.

## Avoid Modifying When

Changing high-level GEOS geometry behavior without a prototype or binding-level requirement.