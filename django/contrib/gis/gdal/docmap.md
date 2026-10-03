---
folder: "django/contrib/gis/gdal"
generated_on: "2026-10-03"
num_files: 24
semantic_tags: [ctypes, datasource, django-gis, gdal, geometry, geospatial, ogr, osr, prototypes, raster, spatial-reference, vector-data]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder provides GeoDjango's Python interfaces to the GDAL, OGR, and OSR libraries. Its modules wrap C API objects for vector data sources, drivers, layers, features, fields, geometries, and spatial references. It also includes pure-Python helpers for geometry types and bounding envelopes, alongside runtime library loading and error handling. The package initializer exposes these APIs together with the raster interface. Merged `prototypes/`: This folder defines low-level Python `ctypes` prototypes for GDAL, OGR, and OSR C APIs. Merged `raster/`: This folder implements GeoDjango's GDAL raster dataset and band interfaces.

## Major Responsibilities

The modules manage GDAL-backed object pointers and expose Python operations for reading vector data, inspecting and transforming geometries, working with coordinate systems, and accessing the native library. They define shared exceptions, OGR type conversions, and adapters for GDAL's C data structures. Merged `prototypes/`: Declares GDAL-family function signatures and adapts their inputs, outputs, errors, and memory handling for Python callers. Merged `raster/`: Provides raster dataset and band abstractions, metadata management, pixel access, and geospatial transformation operations.

## Technology Notes

The implementation uses Python `ctypes` wrappers around GDAL, OGR, and OSR C APIs. It integrates with GeoDjango's geometry and raster packages and can load a configured or platform-discovered GDAL shared library. Merged `prototypes/`: The modules use Python `ctypes` to wrap GDAL, OGR, and OSR functions and error-checking conventions. Merged `raster/`: The modules use Python wrappers around the GDAL C API, including `ctypes`, and support NumPy-based pixel data operations.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `prototypes` : This folder defines low-level Python `ctypes` prototypes for GDAL, OGR, and OSR C APIs. Its modules cover data sources, drivers, features, geometry, rasters, spatial reference systems, and coordinate transformations. Shared factories configure argument types, return types, and error callbacks, while helper routines validate pointers and convert outputs. These wrappers provide the C API surface used by higher-level GeoDjango GDAL code. Declares GDAL-family function signatures and adapts their inputs, outputs, errors, and memory handling for Python callers.
- `raster` : This folder implements GeoDjango's GDAL raster dataset and band interfaces. Its modules manage raster sources, geotransforms, spatial references, pixel bands, metadata, and raster-related constants. The implementation wraps GDAL's C API through `ctypes` and supports array-based pixel I/O. Together, the files provide raster data access and transformation operations to higher-level GIS code. Provides raster dataset and band abstractions, metadata management, pixel access, and geospatial transformation operations.

## Files
- `base.py` (Size : 187 bytes): This module defines `GDALBase`, a common base class for wrappers around GDAL pointers. It inherits pointer behavior from GeoDjango's `CPointerBase`. Its null-pointer exception class is set to `GDALException`, connecting pointer validation to the GDAL-specific error type.
    - Tags: [ctypes, exception-handling, gdal, pointer-management]

- `datasource.py` (Size : 4731 bytes): This module wraps OGR data sources and provides access to their drivers, names, and layers. It opens named or path-based sources in read-only or update mode and accepts existing pointers when paired with a driver pointer. Layer lookup supports integer indices and names, with invalid lookups reported as errors. The wrapper also handles data-source encoding and destroys the native data-source pointer.
    - Tags: [datasource, encoding, gdal, ogr, vector-data]

- `driver.py` (Size : 3255 bytes): This module wraps OGR/GDAL data-source drivers and supports lookup by name, numeric index, or existing pointer. It normalizes selected case-insensitive aliases for common vector and raster driver names. Driver registration occurs on demand, and the wrapper exposes registered-driver counts and driver names. Alias availability for TIGER drivers is conditional on the GDAL version.
    - Tags: [driver, gdal, ogr, registration]

- `envelope.py` (Size : 7514 bytes): This module defines the ctypes `OGREnvelope` structure and the Python `Envelope` bounding-box interface. Envelopes can be initialized from a structure, a four-value sequence, or four coordinates, and reject inverted bounds. The API exposes coordinate bounds, tuple and corner forms, and WKT output. It can expand the bounds to include points, extents, or other envelopes.
    - Tags: [bounding-box, ctypes, geometry, gdal, ogr]
    - TODO/FIXME/NOTE: line 193: `        # TODO: Fix significant figures.`

- `error.py` (Size : 1636 bytes): This module declares `GDALException` and `SRSException` and maps OGR and CPL error codes to exception classes and messages. The `check_err()` helper returns for success and raises the mapped exception for recognized failures. Unknown codes raise `GDALException`. The mappings connect native GDAL/OGR failures to the Python wrapper APIs.
    - Tags: [error-handling, exceptions, gdal, ogr, osr]

- `feature.py` (Size : 4134 bytes): This module wraps an OGR feature owned by a layer and exposes its identifier, layer name, geometry, and field metadata. Integer and name-based indexing return `Field` wrappers, while `get()` retrieves a field's value. Field-name lookup raises an index error when the requested name is absent. Its documentation also notes that the returned `Field` is not itself the field value.
    - Tags: [feature, fields, gdal, ogr, vector-data]
    - TODO/FIXME/NOTE: line 34: `        an integer or the Field's string label. Note that the Field object`

- `field.py` (Size : 7566 bytes): This module wraps OGR feature fields and selects a specialized Python subclass based on the field's OGR type. It converts integer, real, string, date, time, and date-time values, while exposing field names, widths, precision, type information, and set status. List and binary types use dedicated subclasses, and integer fields support 64-bit retrieval. The date-time conversion currently does not adapt the timezone value, as documented in a TODO.
    - Tags: [date-time, field, gdal, ogr, type-conversion]
    - TODO/FIXME/NOTE: line 190: `        # TODO: Adapt timezone information. See:`

- `geometries.py` (Size : 29725 bytes): This module implements `OGRGeometry` and geometry-specific subclasses backed by OGR pointers. It accepts WKT, EWKT, JSON, hexadecimal WKB, memory views, geometry types, or existing pointers, and provides geometry serialization, coordinate access, topology operations, and generated geometries. Spatial-reference assignment and coordinate transformation are integrated with `SpatialReference` and `CoordTransform`. A type mapping selects point, line, polygon, collection, and curve classes, with selected curve types declaring that GEOS conversion is unsupported.
    - Tags: [geometry, geojson, gdal, ogr, topology, transformation, wkb, wkt]
    - TODO/FIXME/NOTE: line 261: `        # TODO: Fix Envelope() for Point geometries.`

- `geomtype.py` (Size : 4728 bytes): This module represents OGR geometry types and maps numeric type codes to names, including Z, M, and combined dimensional forms. Construction accepts another wrapper, a supported name, or a numeric code and rejects invalid values. The class provides name-based equality, Django geometry field names, and conversion of supported single geometry types to their multi counterparts. Its mapping is used by the geometry wrappers to identify concrete types.
    - Tags: [geometry, gdal, ogr, type-mapping]

- `layer.py` (Size : 9054 bytes): This module wraps an OGR layer owned by a data source and exposes feature iteration, indexed access, and slices. It retrieves layer metadata such as fields, field types, geometry type, extent, and spatial reference. Spatial filters accept geometries or rectangular bounds, while helpers retrieve field values and geometries across features. Random feature lookup uses the native capability when available and otherwise iterates features by identifier.
    - Tags: [feature, filtering, gdal, ogr, spatial-reference, vector-data]

- `libgdal.py` (Size : 3720 bytes): This module locates and loads the GDAL shared library, honoring `GDAL_LIBRARY_PATH` when configured and otherwise trying platform-specific library names. It uses `ctypes` loaders and selects the Windows calling convention for OSR functions where required. The module defines helpers to bind function signatures and expose GDAL version information. It also installs a GDAL error callback that logs native library errors.
    - Tags: [ctypes, gdal, library-loading, version-detection]

- `LICENSE` (Size : 1554 bytes): This file contains the BSD-style redistribution and use terms for the OGRGeometry-related code. It specifies conditions for source and binary redistribution, endorsement restrictions, and warranty and liability disclaimers. It is legal text rather than implementation code.
    - Tags: [license, redistribution]

- `prototypes/ds.py` (Size : 5046 bytes): This module defines `ctypes` prototypes for OGR data sources, drivers, layers, features, and fields. It includes constants for GDAL file-access modes and wraps datasource and feature access routines. The declarations cover retrieval of layers, features, field definitions, and field values. Function outputs use wrappers from `generation.py` for conversion and error checking.
    - Tags: [constant, ctypes, datasource, driver, feature, field, gdal, layer, ogr, prototype, wrapper]

- `prototypes/errcheck.py` (Size : 4311 bytes): This module provides error-checking and pointer-validation helpers for GDAL ctypes calls. It extracts by-reference values and validates string, geometry, spatial-reference, and envelope results. It also manages memory for dynamically allocated GDAL pointers, including VSI frees. Invalid pointers or GDAL error codes raise GIS exceptions.
    - Tags: [ctypes, envelope, error-check, gdal, geometry, memory-management, pointer, srs, validation, vsi]

- `prototypes/generation.py` (Size : 5066 bytes): This module provides factories that configure GDAL C function wrappers with argument types, return types, and error callbacks. Its output wrappers cover boolean, numeric, geometry, spatial-reference, string, pointer, and void results. Each wrapper sets the relevant `ctypes` function properties and associates error handling. The module also defines `gdal_char_p` for GDAL-specific string memory handling.
    - Tags: [bool, callback, ctypes, error-check, factory, gdal, generation, pointer, prototype, wrapper]

- `prototypes/geom.py` (Size : 6088 bytes): This module wraps OGR geometry functions for creation, manipulation, analysis, and serialization. It includes GeoJSON, WKB, WKT, and GML operations, geometric set operations, topology predicates, and coordinate or envelope access. It supports measured and three-dimensional geometry checks, curve linearization, and spatial-reference assignment. Helper functions adapt envelope, point, and topology results.
    - Tags: [ctypes, envelope, export, gdal, geometry, ogr, prototype, srs, topology, transformation, wkb, wkt]

- `prototypes/raster.py` (Size : 5740 bytes): This module defines ctypes prototypes for GDAL raster datasets and bands. It wraps raster creation, opening, projection, geotransform, metadata, band I/O, statistics, color interpretation, and no-data operations. It also exposes raster reprojection, warped virtual datasets, and VSI operations for in-memory buffers. GDAL error codes are incorporated into raster-specific error reporting.
    - Tags: [band, buffer, ctypes, datasource, geotransform, gdal, metadata, projection, raster, reprojection, statistics, vsi, warping]

- `prototypes/srs.py` (Size : 3784 bytes): This module wraps OSR spatial-reference and coordinate-transformation functions. It provides creation, validation, cloning, destruction, and import or export across WKT, PROJ, EPSG, and XML representations. It handles ESRI/OGR WKT morphing, EPSG identification, ellipsoid data, units, and coordinate-system classification. The prototypes also establish coordinate transformations between spatial reference systems.
    - Tags: [coordinate-transform, ctypes, ellipsoid, epsg, esri, gdal, import-export, osr, projection, prototype, srs, units, validation, wkt, xml]

- `raster/band.py` (Size : 8616 bytes): This module defines `GDALBand` as a wrapper for GDAL raster bands and exposes dimensions, pixel values, data types, and statistics. It supports statistics caching and refresh. `BandList` provides lazy creation of band wrappers. Pixel data can be read or written using supported Python and NumPy representations through ctypes-based GDAL calls.
    - Tags: [array-io, band-management, ctypes-binding, datatype, gdal-wrapper, lazy-loading, metadata, nodata, numpy-integration, pixel-data, statistics]

- `raster/base.py` (Size : 2959 bytes): This module defines `GDALRasterBase`, a shared base for raster and band metadata behavior. It reads and writes metadata grouped by GDAL domain, including the default domain. The implementation traverses ctypes arrays and encodes or decodes metadata values. GDAL-allocated domain lists are freed after use.
    - Tags: [abstract-base, ctypes-marshalling, encoding, gdal-wrapper, metadata-domain, metadata-management]

- `raster/const.py` (Size : 3362 bytes): This module centralizes GDAL raster constants and mappings. It maps numeric identifiers to pixel data types, color interpretations, ctypes conversion types, and resampling algorithms. It also defines VSI filesystem constants used for in-memory raster handling. Other raster modules use these values to interpret and pass GDAL options.
    - Tags: [api-constants, color-types, ctypes-conversion, datatypes, enumerations, gdal-standards, resampling-algorithms, vsi-filesystem, vsi-in-memory]

- `raster/source.py` (Size : 20327 bytes): This module implements `GDALRaster`, the primary wrapper for raster data sources. It accepts file, byte-backed, and ctypes-pointer inputs, and manages driver detection and VSI storage. Properties expose geotransforms, spatial references, extents, and coordinate transformations. The class also supports warping, reprojection, cloning, and write-mode persistence with VSI cleanup.
    - Tags: [coordinate-systems, data-source-management, gdal-wrapper, geospatial, geotransform, raster-transformation, resampling, spatial-reference, srs-management, vsi-filesystem, warp-operations, write-mode-management]

- `srs.py` (Size : 12759 bytes): This module wraps OSR spatial-reference objects and coordinate transformations. `SpatialReference` imports coordinate systems from EPSG codes, WKT, PROJ strings, XML, and supported shorthand inputs, and exposes names, authority identifiers, units, ellipsoid data, classification, and exported representations. `AxisOrder` configures traditional or authority axis behavior. `CoordTransform` validates source and target references and creates the native transformation object.
    - Tags: [coordinate-transformation, epsg, gdal, osr, projection, spatial-reference, wkt]

- `__init__.py` (Size : 1869 bytes): This package initializer documents the GDAL objects exposed by GeoDjango and re-exports their public classes, exceptions, and version helpers. It also exposes the raster source interface from the sibling raster package. The imports define the package-level API used by callers. The module notes that the native library path can be configured with `GDAL_LIBRARY_PATH`.
    - Tags: [api, gdal, ogr, osr, package, python]

---

## Links Child Folder docmaps

None.

# Related Features

GeoDjango access to GDAL/OGR vector data, geometry operations and serialization, spatial references and coordinate transformations, and raster sources. Merged `prototypes/`: Low-level GeoDjango bindings for GDAL/OGR/OSR data sources, geometry, raster, spatial-reference, and coordinate-transformation operations. Merged `raster/`: GeoDjango raster source and band access, raster metadata and pixel I/O, and raster geospatial transformation and warping.

# Dependency Graph

Not generated.

# Agent Guidance

## Read When

Changing or investigating GeoDjango's GDAL-backed vector data, geometry, driver, field, or spatial-reference behavior, or its native-library loading and error handling. Merged `prototypes/`: Changing or investigating the low-level GDAL-family function bindings used by GeoDjango. Merged `raster/`: Changing GDAL raster source handling, band operations, metadata, or raster transformations.

## Modify When

The requested change affects the Python wrappers for GDAL/OGR/OSR objects, geometry or spatial-reference operations, data-source and layer access, or native-library integration. Merged `prototypes/`: The requested change concerns C API signatures, `ctypes` result conversion, pointer management, or GDAL error handling. Merged `raster/`: The requested change concerns raster data access, pixel I/O, geotransforms, spatial references, or GDAL raster constants.

## Avoid Modifying When

Changing raster-specific behavior without a shared GDAL binding requirement; use the `raster` child index to locate raster implementation files. Merged `prototypes/`: Changing higher-level geometry or raster behavior without a binding-level requirement. Merged `raster/`: Changing vector geometry or unrelated GDAL bindings without a raster-specific requirement.
