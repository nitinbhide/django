---
folder: "django/core"
generated_on: "2026-10-03"
num_files: 25
semantic_tags: [asgi, cache, checks, command-line, commands, cryptography, deserialization, email, exceptions, file-handling, http, json, management, pagination, project-scaffolding, request-handling, serialization, server, signals, signing, system-checks, uploads, validation, validators, wsgi, xml, yaml]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

`django/core` provides framework-wide services used by Django applications, including request handling, caching, file processing, mail, management commands, serialization, validation, and signing. It also contains startup checks, pagination, and WSGI/ASGI entry points. Subsystem maps provide detail for the folders with cohesive implementations. Begin here to locate the core service, then follow the corresponding child map. Merged `handlers/`: This folder implements Django's request/response handling pipeline for WSGI and ASGI. Merged `management/`: This folder provides Django's management command framework and shared utilities. Merged `serializers/`: This folder implements Django's object serialization and deserialization formats. Merged `servers/`: This folder contains Django's low-level HTTP server support used by the development server.

## Major Responsibilities

The modules expose shared framework APIs and coordinate application-level services. Child folders contain implementations for cache backends, checks, file storage, HTTP handling, mail delivery, management commands, serializers, and development-server support. Merged `handlers/`: The handlers build request objects, run middleware and views, translate exceptions into responses, and support synchronous and asynchronous request paths. WSGI and ASGI adapters provide protocol-specific server integration. Merged `management/`: The modules parse command-line input, locate command classes, invoke command execution, and provide reusable utilities for command output and generated project files. The `commands` child contains the concrete built-in operations. Merged `serializers/`: The modules convert model instances to serialized streams and reconstruct model objects from streams. They define format-specific encoders, decoders, and options around a shared serialization contract. Merged `servers/`: The code adapts WSGI server and handler classes to Django's HTTP request and response objects. It also supplies internal WSGI application loading and connection error handling.

## Technology Notes

The code is Python and integrates with WSGI, ASGI, database, filesystem, email, and serialization interfaces. Merged `handlers/`: The code implements both WSGI and ASGI request interfaces and integrates Django middleware. Merged `management/`: The framework integrates Django settings, application loading, terminal output, and template rendering. Merged `serializers/`: JSON and XML are handled with Python standard-library support; YAML depends on the optional PyYAML package. Merged `servers/`: The implementation uses Python's `wsgiref` and socket server primitives.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `handlers` : This folder implements Django's request/response handling pipeline for WSGI and ASGI. Shared base and exception modules coordinate middleware, URL resolution, and error conversion, while protocol-specific handlers adapt incoming requests. The ASGI handler contains a documented FIXME for an override capability. Read the relevant protocol entry point when changing request execution. The handlers build request objects, run middleware and views, translate exceptions into responses, and support synchronous and asynchronous request paths. WSGI and ASGI adapters provide protocol-specific server integration.
- `management` : This folder provides Django's management command framework and shared utilities. It discovers and executes built-in or project commands, defines command interfaces and output styling, and renders project/app templates. Individual built-in commands are indexed in the child `commands` map. Start with `base.py` for command lifecycle changes and `__init__.py` for dispatch behavior. The modules parse command-line input, locate command classes, invoke command execution, and provide reusable utilities for command output and generated project files. The `commands` child contains the concrete built-in operations.
- `serializers` : This folder implements Django's object serialization and deserialization formats. A shared serializer framework coordinates format lookup and object handling, with modules for Python-native, JSON, JSON Lines, YAML, and XML representations. Formats are used by fixture and data-management commands. Start with the package entry point and base classes when changing serializer behavior. The modules convert model instances to serialized streams and reconstruct model objects from streams. They define format-specific encoders, decoders, and options around a shared serialization contract.
- `servers` : This folder contains Django's low-level HTTP server support used by the development server. Its implementation builds on Python's WSGI server classes and provides Django request handling and response writing. The management `runserver` command uses this server machinery. Read this area when changing development-server request transport behavior. The code adapts WSGI server and handler classes to Django's HTTP request and response objects. It also supplies internal WSGI application loading and connection error handling.

## Files
- `asgi.py` (Size : 399 bytes): Exposes Django's ASGI application factory. The function initializes Django's ASGI handler after application setup. It is the conventional ASGI entry point for a project. No markers are present.
    - Tags: [asgi, application-entry-point]

- `exceptions.py` (Size : 7038 bytes): Defines framework-level exceptions and helpers used across Django. It includes common model, app-registry, and request-related exception types. Other subsystems raise these types to report framework conditions. No markers are present.
    - Tags: [exceptions, framework]

- `handlers/asgi.py` (Size : 14206 bytes): Implements Django's ASGI application handler and asynchronous request lifecycle. It receives ASGI events, constructs requests, invokes middleware and views, and sends response messages. Line 166 includes a `FIXME` about allowing an override.
    - Tags: [asgi, async, request-handling]
    - TODO/FIXME/NOTE: line 166 FIXME

- `handlers/base.py` (Size : 15215 bytes): Defines shared request-handler behavior for middleware loading, URL resolution, response processing, and exception handling. It provides the common base used by protocol-specific handlers. The implementation coordinates Django's request and response APIs. No markers are present.
    - Tags: [middleware, request-handling]

- `handlers/exception.py` (Size : 6166 bytes): Converts exceptions raised during request processing into HTTP responses. It handles exception middleware and maps known Django and HTTP errors to response objects. Both WSGI and ASGI handling use this shared conversion layer. No markers are present.
    - Tags: [exceptions, http, request-handling]

- `handlers/wsgi.py` (Size : 7521 bytes): Implements Django's WSGI request handler. It adapts WSGI environment data into Django requests and returns WSGI responses from the shared handler pipeline. Synchronous request execution is handled by the common base. No markers are present.
    - Tags: [http, request-handling, wsgi]

- `management/base.py` (Size : 25939 bytes): Defines the base command class, argument parsing, output wrappers, and common execution behavior. It handles system checks, transactions, exception conversion, and styled command output. Built-in and project commands subclass this API. No markers are present.
    - Tags: [command-api, command-line, output]

- `management/color.py` (Size : 3288 bytes): Provides terminal output styling and colorization for management commands. It selects styles based on terminal support and command options. The command base uses this module for readable output. No markers are present.
    - Tags: [command-line, output, terminal]

- `management/sql.py` (Size : 1910 bytes): Provides helpers for SQL emitted around model and migration operations. It formats or coordinates SQL statements used by management commands. The database command modules use it for SQL-related output. No markers are present.
    - Tags: [commands, database, sql]

- `management/templates.py` (Size : 15899 bytes): Implements app and project template rendering for scaffolding commands. It locates template sources, substitutes project values, and creates the resulting files and directories. `startapp` and `startproject` use these utilities. No markers are present.
    - Tags: [project-scaffolding, templates]

- `management/utils.py` (Size : 5817 bytes): Defines shared utilities used by Django management commands. The functions support command execution and command-specific file or option handling. This module keeps reusable behavior outside individual commands. No markers are present.
    - Tags: [commands, utilities]

- `management/__init__.py` (Size : 17781 bytes): Implements command discovery, loading, dispatch, and the command-line entry point. It also provides `call_command()` for programmatic execution. Lines 235 and 295 contain `NOTE` text in a comment and function documentation.
    - Tags: [command-line, commands, dispatch]
    - TODO/FIXME/NOTE: line 235 NOTE; line 295 NOTE

- `paginator.py` (Size : 15699 bytes): Implements `Paginator` and `Page` for splitting iterable data into pages. It handles count lookup, page validation, empty results, and orphan items. The API is used by applications and framework components that display paginated results. No markers are present.
    - Tags: [pagination]

- `serializers/base.py` (Size : 13989 bytes): Defines common serializer and deserializer abstractions and shared object handling. It manages model metadata, fields, and natural keys independently of a specific output format. Format modules specialize the base behavior. No markers are present.
    - Tags: [deserialization, interface, serialization]

- `serializers/json.py` (Size : 3917 bytes): Implements JSON serialization and deserialization using the shared serializer framework. It configures JSON encoding of model data and streams decoded objects through the common deserializer. No markers are present.
    - Tags: [deserialization, json, serialization]

- `serializers/jsonl.py` (Size : 2318 bytes): Implements JSON Lines serialization and deserialization. It handles one JSON representation per line while using the shared model-object encoding and reconstruction logic. No markers are present.
    - Tags: [deserialization, json-lines, serialization]

- `serializers/python.py` (Size : 9138 bytes): Implements Python-native serialization structures and deserialization. It converts model instances to basic Python data and reconstructs objects from those structures. The format is also used as a foundation for other serializers. No markers are present.
    - Tags: [deserialization, python, serialization]

- `serializers/pyyaml.py` (Size : 2700 bytes): Implements YAML serialization and deserialization using PyYAML. It adapts YAML stream operations to Django's shared serializer contract. The optional dependency is needed when this format is used. No markers are present.
    - Tags: [deserialization, serialization, yaml]

- `serializers/xml_serializer.py` (Size : 22662 bytes): Implements XML serialization and deserialization for Django model data. It writes XML elements and parses them back into shared object data, handling fields and related objects. The module contains the format-specific XML logic. No markers are present.
    - Tags: [deserialization, serialization, xml]

- `serializers/__init__.py` (Size : 9040 bytes): Provides serializer and deserializer lookup, registration, and format-level dispatch. It exposes the high-level APIs used by Django commands and callers. Concrete format implementation is delegated to sibling modules. No markers are present.
    - Tags: [api, deserialization, serialization]

- `servers/basehttp.py` (Size : 10053 bytes): Provides the HTTP server, request handler, and WSGI server-handler classes used by Django's development server. It translates incoming WSGI requests into Django handling and emits HTTP responses. It includes application resolution and broken-pipe handling. No markers are present.
    - Tags: [http, server, wsgi]

- `signals.py` (Size : 157 bytes): Declares core Django signal objects for request lifecycle events. The named signals are imported and sent by framework components. No markers are present.
    - Tags: [signals]

- `signing.py` (Size : 10692 bytes): Provides cryptographic signing and verification utilities, including timestamped signatures and JSON-oriented signing. It derives signatures from salted keys and supports expiration checks for signed values. The API is used where Django needs tamper-evident data. No markers are present.
    - Tags: [cryptography, signing]

- `validators.py` (Size : 26304 bytes): Defines reusable validators for URLs, email addresses, IP addresses, slugs, regular expressions, and related values. The validator classes and functions raise structured validation errors used throughout forms and models. The module also includes reusable length and value constraints. No markers are present.
    - Tags: [validation, validators]

- `wsgi.py` (Size : 401 bytes): Exposes Django's WSGI application factory. The function initializes and returns the WSGI handler after application setup. It is the conventional WSGI entry point for a project. No markers are present.
    - Tags: [application-entry-point, wsgi]

---

## Links Child Folder docmaps
- `cache/docmap.md` — Cache alias handling and template-fragment keys, with backend implementations in its child map.
- `checks/docmap.md` — System-check registry, message types, and built-in configuration checks.
- `files/docmap.md` — File wrappers, upload processing, temporary files, and storage.
- `mail/docmap.md` — Email API, message construction, and configured delivery backends.
- `management/commands/docmap.md` — Built-in Django management commands for administration, migrations, data, scaffolding, localization, servers, and tests.

# Related Features

Application entry points, request processing, validation, pagination, signing, caching, mail, uploads, serialization, system checks, and management commands. Merged `handlers/`: HTTP request dispatch, middleware execution, and WSGI/ASGI application handling. Merged `management/`: `django-admin` and `manage.py` command discovery, execution, output, and project scaffolding. Merged `serializers/`: Model fixture serialization and deserialization across supported data formats. Merged `servers/`: Django's development HTTP server and WSGI request/response transport.

# Agent Guidance

## Read When

Locating a Django core service or tracing behavior across its subsystem folders. Merged `handlers/`: Changing request lifecycle, middleware integration, exception-to-response behavior, or protocol adapters. Merged `management/`: Changing command parsing, dispatch, base command behavior, or scaffolding utilities. Merged `serializers/`: Changing serialized data formats, fixture loading, or object reconstruction. Merged `servers/`: Changing local development server protocol or WSGI request handling.

## Modify When

Changing a shared core API or subsystem implementation represented in this hierarchy. Merged `handlers/`: Updating shared request handling or an ASGI/WSGI implementation. Merged `management/`: Updating a shared command facility or adding a built-in management operation. Merged `serializers/`: Updating a format encoder/decoder or the common serializer API. Merged `servers/`: Changing server adapter behavior or error handling.

## Avoid Modifying When

Working on application-specific behavior outside `django/core`. Merged `handlers/`: Changing lower-level development-server transport unrelated to the handler pipeline. Merged `management/`: Changing an individual command whose behavior is isolated in the child folder. Merged `serializers/`: Changing management command behavior that does not affect serialization. Merged `servers/`: Changing deployment WSGI/ASGI entry points that do not use this server.
