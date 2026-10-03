# Architecture Map

This map summarizes architectural facts explicitly recorded in the generated docmap hierarchy. It does not infer dependencies or describe unrecorded runtime relationships.

## Architecture overview

Django is organized as a modular Python framework. Its package areas separate configuration and application loading, HTTP and URL handling, middleware, forms, template rendering, database access, and reusable views. Optional `contrib` applications add capabilities while using the framework's shared APIs. Folder-level indexes carry implementation detail beneath the root overview.

## Architectural patterns

- **Package-oriented modules:** Framework capabilities are grouped into Python packages with package-level APIs and narrower implementation areas.
- **Pluggable backends:** Database, template, task, session, and storage maps describe backend interfaces or backend-specific implementations.
- **Request pipeline:** Core handler summaries describe request construction, middleware and view execution, and exception conversion for WSGI and ASGI.
- **Declarative framework APIs:** Model, form, widget, route, and management-command summaries describe registries, metadata, factories, and extension hooks.
- **Signal dispatch:** The dispatch package documents receiver registration, sender matching, invocation, and receiver lifecycle management.
- **Template rendering:** Django templates and an optional Jinja2 backend are exposed through configured rendering interfaces.

## Layer definitions

- **Application setup and configuration:** `django/docmap.md` and `django/conf/docmap.md` describe version/setup behavior, settings, app loading, and project scaffolding.
- **Request and presentation services:** `django/core/docmap.md`, `django/middleware/docmap.md`, `django/template/docmap.md`, and `django/forms/docmap.md` describe request handling, middleware, rendering, forms, and widgets.
- **Persistence:** Database behavior is summarized in the merged `db` section of `django/docmap.md`; optional PostgreSQL and GIS database features are documented in their contrib maps.
- **Optional applications:** `django/contrib/docmap.md` indexes applications such as admin, authentication, sessions, static files, GIS, and syndication.
- **Development and quality tooling:** `scripts/docmap.md` and root configuration-file entries in `DOCMAP.md` describe release, test, packaging, and lint workflows.

## Major responsibilities

- `django/core/docmap.md` covers shared services such as request handling, management commands, serialization, validation, caching, and signing.
- `django/docmap.md` covers package startup and its merged app registry, database, HTTP, task, URL, template-tag, and test-framework summaries.
- `django/forms/docmap.md` covers validation, formsets, model forms, widgets, errors, and rendering.
- `django/template/docmap.md` covers parsing, compilation, rendering, tags, filters, backends, and loaders.
- `django/contrib/docmap.md` provides navigation across optional applications.

## Architectural constraints

- `pyproject.toml`, summarized in `DOCMAP.md`, declares Python 3.12 or newer.
- The generated maps keep `dependencies: []`; a module dependency graph has not been generated.
- No additional explicit architecture constraints are available in the generated docmaps.
