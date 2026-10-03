---
folder: "django"
generated_on: "2026-10-03T13:33:04+05:30"
num_files: 44
semantic_tags: [application-configuration, application-registry, application-setup, async-tasks, command-line, connections, cookies, database, django, event-dispatch, http, internationalization, multipart, python, requests, responses, routing, shortcuts, signals, task-backends, template-tags, templates, test-client, test-framework, testing, transactions, url-routing, urls, versioning, weak-references]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder is Django's top-level Python package, exposing package version information and setup behavior alongside command-line and general-purpose view helpers. Its files provide the `python -m django` entry point and convenience functions that connect templates, HTTP responses, URL resolution, and querysets. The helper APIs reduce repeated framework-level wiring for applications. The package delegates detailed behavior to its child packages, which have separate indexes linked below. Merged `apps/`: This package defines Django application configuration and the registry that tracks installed applications and their models. Merged `db/`: This package coordinates Django's database-facing APIs and shared connection behavior. Merged `dispatch/`: This package provides Django's signal and event-dispatch mechanism. Merged `http/`: This package models HTTP requests and responses and parses HTTP-related input. Merged `tasks/`: This package defines Django's task API, task execution behavior, and supporting integration points. Merged `templatetags/`: This package provides Django's built-in template tag libraries. Merged `test/`: This package provides Django's testing framework and its integration with Python's test runner. Merged `urls/`: This package implements Django URL configuration, route resolution, and reverse URL lookup.

## Major Responsibilities

The package initializer exposes Django's version and configures logging, URL script prefixes, and the installed-app registry through `setup()`. The module entry point passes command-line arguments to Django's management command dispatcher. Shortcut functions render templates, resolve redirect targets, and retrieve objects or lists with synchronous and asynchronous query APIs, translating missing results into `Http404`. Merged `apps/`: Define the `AppConfig` interface and create application instances from installed-app entries. Maintain the global application registry, populate it in phases, and provide lookups for applications and models. Merged `db/`: Provides top-level database initialization, transaction management, and database exception/connection utilities. Merged `dispatch/`: Expose signal primitives and implement receiver registration, disconnection, sender matching, invocation, and receiver lifecycle management. Merged `http/`: Represent incoming requests and outgoing responses, parse uploaded form data, and provide cookie and HTTP exception utilities. Merged `tasks/`: Define task metadata and invocation, provide backend selection and task lifecycle signaling, and expose checks and errors related to task configuration. Merged `tasks/backends/`: Define the task backend interface and implement basic execution strategies used for configured tasks. Merged `templatetags/`: Register and implement template tags and filters for caching, translation, localization, static assets, and timezone-aware values. Merged `test/`: Create and execute test cases, simulate HTTP requests, provide HTML-aware assertions, manage test databases and environments, and integrate with Python's unittest discovery and reporting. Merged `urls/`: Define URL patterns and converters, resolve paths into view callbacks, reverse named routes, and expose URLconf inclusion and namespace support.

## Technology Notes

The direct files are Python modules in the Django framework package. They integrate with Django settings, application loading, management commands, templates, HTTP responses, URL resolution, and ORM querysets. Merged `apps/`: Python package using Django application-loading APIs. Merged `db/`: The package implements Django's Python database abstraction and transaction APIs. Merged `dispatch/`: Python weak references and locking support the signal dispatcher. Merged `http/`: Python HTTP abstractions with WSGI/ASGI request support and multipart MIME parsing. Merged `tasks/`: Python task abstractions with pluggable backends and asynchronous execution support. Merged `tasks/backends/`: Python pluggable backend classes. Merged `templatetags/`: Python tag libraries integrated with Django's template parser and filter registration APIs. Merged `test/`: Python `unittest` integration with Django-specific test clients and database test utilities. Merged `urls/`: Python routing and regular-expression-based URL matching.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `apps` : This package defines Django application configuration and the registry that tracks installed applications and their models. It provides the application metadata API used during project setup and app loading. The registry exposes application and model lookup while coordinating readiness states. Its implementation is Python code built around Django's app-loading lifecycle. Define the `AppConfig` interface and create application instances from installed-app entries. Maintain the global application registry, populate it in phases, and provide lookups for applications and models.
- `db` : This package coordinates Django's database-facing APIs and shared connection behavior. It exposes transaction helpers and connection management to the rest of the framework. The backend implementations, model ORM, and migration system are organized in child folders. Read this folder for database-wide behavior rather than backend-specific SQL or ORM internals. Provides top-level database initialization, transaction management, and database exception/connection utilities.
- `dispatch` : This package provides Django's signal and event-dispatch mechanism. The dispatcher connects receivers to senders and invokes matching receivers when a signal is sent. It supports weak references, receiver identity, and optional receiver-result caching. The package also includes the bundled license text for its dispatch implementation. Expose signal primitives and implement receiver registration, disconnection, sender matching, invocation, and receiver lifecycle management.
- `http` : This package models HTTP requests and responses and parses HTTP-related input. It provides request data access, response classes and headers, cookie handling, and multipart form/file upload parsing. The package-level module re-exports commonly used HTTP types. These primitives are used throughout Django's request/response processing. Represent incoming requests and outgoing responses, parse uploaded form data, and provide cookie and HTTP exception utilities.
- `tasks/backends` : This package contains Django task backend implementations and their common contract. The base backend defines how task work is submitted and executed. Dummy and immediate backends provide non-queued and synchronous execution strategies. These implementations support backend configuration without coupling the task API to a single queue system. Define the task backend interface and implement basic execution strategies used for configured tasks.
- `tasks` : This package defines Django's task API, task execution behavior, and supporting integration points. It provides task declaration and invocation primitives, backend interfaces, checks, exceptions, and signals. Backend implementations are organized in a child folder and provide execution strategies. The package is the framework layer for defining and dispatching application tasks. Merged `backends/`: This package contains Django task backend implementations and their common contract. Define task metadata and invocation, provide backend selection and task lifecycle signaling, and expose checks and errors related to task configuration. Merged `backends/`: Define the task backend interface and implement basic execution strategies used for configured tasks.
- `templatetags` : This package provides Django's built-in template tag libraries. Separate modules expose cache, internationalization, localization, static-file, and timezone tags and filters. The implementations register their syntax with the template library API and delegate specialized behavior to the relevant framework utilities. Applications load these libraries from templates by their registered names. Register and implement template tags and filters for caching, translation, localization, static assets, and timezone-aware values.
- `test` : This package provides Django's testing framework and its integration with Python's test runner. It includes test cases and assertion helpers, an HTTP test client, HTML comparison utilities, runner orchestration, and signals for test lifecycle events. Utilities support database isolation, temporary settings, environment changes, and other test setup concerns. These APIs are used by Django's own tests and by application test suites. Create and execute test cases, simulate HTTP requests, provide HTML-aware assertions, manage test databases and environments, and integrate with Python's unittest discovery and reporting.
- `urls` : This package implements Django URL configuration, route resolution, and reverse URL lookup. It exposes the public `path()` and `re_path()` constructors and provides route converters, resolver exceptions, and utility functions. Resolver objects match incoming paths against URL patterns and produce view matches; reverse resolution constructs paths from names and arguments. The package is central to mapping requests to views. Define URL patterns and converters, resolve paths into view callbacks, reverse named routes, and expose URLconf inclusion and namespace support.

## Files
- `apps/config.py` (Size : 11756 bytes): Implements `AppConfig`, which stores application metadata, locates app modules and models, and supports application readiness hooks. It includes helpers for deriving configuration from installed-app declarations.
    - Tags: [application-configuration, app-loading, django, python]

- `apps/registry.py` (Size : 18145 bytes): Implements the central `Apps` registry and its global instance. It tracks app configurations and models, populates installed apps in phases, and provides lookup and readiness operations.
    - Tags: [application-registry, model-registry, django, python]

- `apps/__init__.py` (Size : 94 bytes): Exposes the application configuration and registry APIs from this package.
    - Tags: [application-registry, django, python]

- `db/transaction.py` (Size : 13429 bytes): Implements atomic transaction blocks, commit/rollback controls, and transaction-state helpers around database connections. The APIs coordinate nested blocks and connection savepoints. Read it when changing transaction boundaries or callback behavior.
    - Tags: [atomicity, database, savepoints, transactions]
    - TODO/FIXME/NOTE: line 214: note

- `db/utils.py` (Size : 9632 bytes): Defines database exception classes and the connection handler/configuration utilities used to construct and access database connections. It also handles backend loading and connection setup. Read it when changing connection configuration or database error handling.
    - Tags: [connections, database, exceptions]
    - TODO/FIXME/NOTE: line 97: Note

- `db/__init__.py` (Size : 1596 bytes): Initializes database package APIs and defines connection lifecycle helpers used to reset query logs and close stale connections. It connects database lifecycle signals to those helpers. Read it when changing package-level database setup or connection cleanup behavior.
    - Tags: [connections, database, initialization]

- `dispatch/dispatcher.py` (Size : 20121 bytes): Implements `Signal` and the `receiver` decorator. Receivers are matched by sender and dispatch UID, stored with optional weak references, and called synchronously or asynchronously; optional caching avoids repeated receiver lookups.
    - Tags: [async, event-dispatch, python, signals, weak-references]

- `dispatch/license.txt` (Size : 1779 bytes): Contains the license notice distributed with the signal dispatcher code.
    - Tags: [license, signals]

- `dispatch/__init__.py` (Size : 296 bytes): Exposes the signal dispatcher types and the `receiver` decorator as the package-level API.
    - Tags: [django, event-dispatch, python, signals]

- `http/cookie.py` (Size : 702 bytes): Defines the HTTP cookie naming and parsing helpers used by Django's request and response code.
    - Tags: [cookies, http, python]

- `http/multipartparser.py` (Size : 28853 bytes): Parses multipart request bodies into form fields and uploaded files. It coordinates upload handlers, manages input streams and boundaries, and applies request upload limits.
    - Tags: [file-uploads, http, multipart, python]
    - TODO/FIXME/NOTE: line 722 FIXME

- `http/request.py` (Size : 31459 bytes): Implements `HttpRequest` and its upload-related variants. It exposes headers, query/form data, cookies, host and URL information, and supports request construction from WSGI and ASGI environments.
    - Tags: [asgi, django, http, python, requests, wsgi]

- `http/response.py` (Size : 27986 bytes): Implements base, standard, streaming, and file HTTP responses, including status, headers, cookies, and content handling. It also defines response-related exceptions and header validation.
    - Tags: [cookies, http, python, responses, streaming]
    - TODO/FIXME/NOTE: line 674 NOTE

- `http/__init__.py` (Size : 1252 bytes): Re-exports request, response, cookie, and HTTP exception types to provide the public `django.http` API.
    - Tags: [django, http, python]

- `shortcuts.py` (Size : 7177 bytes): Provides convenience APIs for rendering templates, redirecting to model URLs, named routes, or URLs, and retrieving one or more queryset results. Synchronous and asynchronous lookup helpers raise `Http404` for missing results, while `resolve_url()` handles model methods, lazy strings, relative paths, reverse resolution, and URL fallbacks.
    - Tags: [asynchronous-orm, django, http-responses, redirects, templates, url-resolution]

- `tasks/backends/base.py` (Size : 3908 bytes): Defines the abstract/base task backend contract and shared submission and execution behavior.
    - Tags: [async-tasks, backend-api, python]

- `tasks/backends/dummy.py` (Size : 2021 bytes): Implements a backend that accepts task submissions without performing task work, for disabled or non-executing configurations.
    - Tags: [dummy-backend, python, task-backends]

- `tasks/backends/immediate.py` (Size : 3436 bytes): Implements a backend that runs submitted tasks immediately rather than queuing them for later execution.
    - Tags: [immediate-execution, python, task-backends]

- `tasks/base.py` (Size : 8798 bytes): Implements task definitions and invocation, including task options, enqueueing behavior, and execution context used by task backends.
    - Tags: [async-tasks, execution, python, task-api]

- `tasks/checks.py` (Size : 262 bytes): Registers system-check integration for task configuration.
    - Tags: [configuration, django, system-checks, tasks]

- `tasks/exceptions.py` (Size : 546 bytes): Defines exceptions specific to Django task declaration and execution.
    - Tags: [exceptions, python, tasks]

- `tasks/signals.py` (Size : 1755 bytes): Declares signals associated with task lifecycle events.
    - Tags: [django, signals, tasks]

- `tasks/__init__.py` (Size : 1223 bytes): Exposes the task declaration and execution API for application code.
    - Tags: [async-tasks, django, python]

- `templatetags/cache.py` (Size : 3650 bytes): Defines cache-related template tags that cache rendered blocks and configure cache keys and timeouts.
    - Tags: [caching, python, template-tags]

- `templatetags/i18n.py` (Size : 20577 bytes): Implements translation and language-selection template tags and filters, including message translation and block-based translation.
    - Tags: [internationalization, python, template-tags, translation]

- `templatetags/l10n.py` (Size : 1623 bytes): Provides localization template filters and configuration behavior for localized value rendering.
    - Tags: [localization, python, template-filters]

- `templatetags/static.py` (Size : 4909 bytes): Defines the `{% static %}` and related tags for resolving static asset URLs, including configured storage behavior.
    - Tags: [python, static-files, template-tags]

- `templatetags/tz.py` (Size : 5472 bytes): Defines template tags and filters for local-time conversion and timezone selection.
    - Tags: [python, template-tags, timezones]

- `test/client.py` (Size : 58373 bytes): Implements Django's test client, request factory, and response wrappers for exercising views through WSGI or ASGI request paths. It handles sessions, cookies, redirects, form data, and exception propagation.
    - Tags: [asgi, http, python, test-client, testing, wsgi]

- `test/html.py` (Size : 9142 bytes): Provides HTML parsing and normalization helpers used by test assertions for comparing markup and checking HTML structures.
    - Tags: [html, python, testing]

- `test/runner.py` (Size : 48436 bytes): Implements Django's test runner, suite construction, database setup/teardown, test labels, result reporting, and parallel execution support.
    - Tags: [database-testing, python, test-runner, testing]

- `test/signals.py` (Size : 7913 bytes): Defines signals emitted around test setup and teardown and provides support for test lifecycle listeners.
    - Tags: [python, signals, testing]

- `test/testcases.py` (Size : 70855 bytes): Implements Django's `SimpleTestCase`, `TransactionTestCase`, and `TestCase`, including assertions, request helpers, fixture handling, and database isolation.
    - Tags: [database-testing, python, test-cases, testing]
    - TODO/FIXME/NOTE: line 1014 TODO

- `test/utils.py` (Size : 35072 bytes): Provides reusable test utilities for temporary settings, modified environments, captured output, database setup, and test support helpers.
    - Tags: [python, testing, test-utilities]
    - TODO/FIXME/NOTE: line 100 NOTE; line 101 NOTE

- `test/__init__.py` (Size : 872 bytes): Exposes common test-case classes, test client types, and assertion helpers as the `django.test` API.
    - Tags: [django, python, test-framework, testing]

- `urls/base.py` (Size : 6399 bytes): Implements URL resolution and reverse lookup entry points, including URLconf selection, script prefixes, and namespaced route handling.
    - Tags: [python, reverse-resolution, routing, urls]

- `urls/conf.py` (Size : 3574 bytes): Defines `include()`, `path()`, and `re_path()` helpers and constructs URL patterns from routes, views, and URLconf modules.
    - Tags: [python, routing, urlconf, urls]

- `urls/converters.py` (Size : 1426 bytes): Defines built-in route converters for string, path, integer, and UUID URL parameters.
    - Tags: [converters, python, routing, urls]

- `urls/exceptions.py` (Size : 124 bytes): Defines URL resolution exceptions exposed by the routing package.
    - Tags: [exceptions, python, urls]

- `urls/resolvers.py` (Size : 32914 bytes): Implements URL pattern and resolver classes, route matching, callback lookup, namespaces, and reverse construction for URLconf trees.
    - Tags: [python, routing, urlconf, urls]

- `urls/utils.py` (Size : 7593 bytes): Provides utilities for URL pattern iteration, script prefixes, and route-related formatting.
    - Tags: [python, routing, urls, utilities]

- `urls/__init__.py` (Size : 1132 bytes): Exposes the public URL pattern constructors, resolvers, reverse/resolve helpers, and URL exceptions.
    - Tags: [django, python, routing, urls]

- `__init__.py` (Size : 849 bytes): Defines the package version and exposes `setup()` to configure logging, optionally set the URL script prefix, and populate the installed-app registry using project settings.
    - Tags: [application-setup, django, logging, settings, versioning]

- `__main__.py` (Size : 222 bytes): Makes `python -m django` invoke Django's management command dispatcher, forwarding command-line arguments to `execute_from_command_line()`.
    - Tags: [command-line, django, management, module-entry-point]

---

## Links Child Folder docmaps
- `conf/docmap.md` — Settings interfaces, defaults, project templates, and configuration-related URL helpers.
- `contrib/docmap.md` — Optional Django applications and their supporting features.
- `core/docmap.md` — Framework-wide services, including request handling, caching, management commands, and validation.
- `db/backends/docmap.md` — Shared database backend interfaces and vendor-specific implementations.
- `db/migrations/docmap.md` — Migration discovery, graph planning, state transitions, and execution operations.
- `db/models/docmap.md` — ORM model metadata, query APIs, fields, expressions, and SQL compilation.
- `forms/docmap.md` — Form fields, validation, model forms, widgets, and rendering templates.
- `middleware/docmap.md` — Request/response middleware for caching, security, CSRF, localization, and related concerns.
- `template/docmap.md` — Template parsing and rendering, contexts, libraries, and backend integrations.
- `utils/docmap.md` — Shared utilities for dates, data structures, encoding, HTTP, cryptography, logging, and compatibility.
- `views/docmap.md` — Reusable views, generic class-based view foundations, error pages, and related templates.

# Related Features

Package setup and application loading; command-line management dispatch; template rendering; URL resolution and redirects; synchronous and asynchronous object retrieval with HTTP 404 handling. Merged `apps/`: Django application discovery, startup population, and model registration. Merged `db/`: Database connection management, transaction handling, ORM operations, and schema migrations. Merged `dispatch/`: Django's in-process signal API and event receiver registration. Merged `http/`: HTTP request handling, response generation, cookie management, and multipart uploads. Merged `tasks/`: Task declaration, task dispatch, pluggable execution backends, and task lifecycle signals. Merged `tasks/backends/`: Task submission and basic backend execution modes. Merged `templatetags/`: Built-in template tags and filters for translation, localization, caching, static assets, and timezones. Merged `test/`: Django unit and integration testing, HTTP request simulation, database isolation, and test execution. Merged `urls/`: Request routing, URLconf inclusion, path converters, and named URL reversal.

# Agent Guidance

## Read When

Working on package initialization, Django version exposure, the `python -m django` entry point, or framework shortcut functions. Merged `apps/`: Investigating app startup, installed-app configuration, app/model lookup, or registry readiness. Merged `db/`: Changing database connection lifecycle, transaction management, or package-level database APIs. Merged `dispatch/`: Investigating signal connection, receiver lifetime, sender filtering, or dispatch behavior. Merged `http/`: Tracing request parsing, request metadata, uploads, response headers, streaming responses, or cookies. Merged `tasks/`: Investigating task definitions, dispatch behavior, configuration checks, or lifecycle signals. Merged `tasks/backends/`: Investigating backend selection, task submission semantics, or synchronous/dummy execution. Merged `templatetags/`: Investigating built-in template library syntax or rendered locale/timezone behavior. Merged `test/`: Writing or debugging Django tests, understanding test client behavior, or diagnosing test database setup and runner behavior. Merged `urls/`: Investigating route matching, URL pattern construction, namespaces, or reverse URL lookup.

## Modify When

Changing package-level setup behavior, command-line module dispatch, or shared view helper APIs. Merged `apps/`: Changing application metadata handling or registry population and lookup behavior. Merged `db/`: The behavior is shared across database backends or is part of the database package's public utilities. Merged `dispatch/`: Changing receiver registration, signal sending, weak-reference handling, or dispatch caching. Merged `http/`: Changing the framework's core request/response representations or multipart parsing behavior. Merged `tasks/`: Changing Django's task API or backend integration contract. Merged `tasks/backends/`: Changing the shared backend contract or built-in task execution strategies. Merged `templatetags/`: Changing a built-in template tag or filter implementation. Merged `test/`: Changing shared test APIs, test-case assertions, client simulation, or test orchestration. Merged `urls/`: Changing URLconf APIs, resolver semantics, built-in converters, or route generation.

## Avoid Modifying When

The change is confined to an individual child package; use that package's linked `docmap.md` and source files instead. Merged `apps/`: Changing an individual app's business logic or model implementation. Merged `db/`: The change is specific to a backend dialect, ORM field, model query, or migration operation; use the corresponding child folder instead. Merged `dispatch/`: Changing how individual framework components emit their own signals. Merged `http/`: Changing middleware policy or URL routing behavior. Merged `tasks/`: Changing an application's task implementation or an external queue service. Merged `tasks/backends/`: Changing external queue infrastructure not implemented here. Merged `templatetags/`: Changing the template parser or app-specific custom tag libraries. Merged `test/`: Changing production request handling or app-specific test assertions. Merged `urls/`: Changing view behavior or middleware that runs after resolution.
