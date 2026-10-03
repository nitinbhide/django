---
folder: "django/template"
generated_on: "2026-10-03"
num_files: 25
semantic_tags: [django, filesystem, jinja2, loaders, python, template-backends, template-engine, template-language, template-loaders]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package implements Django's template language and its integration points. Core modules parse and render templates, manage contexts, filters, tags, libraries, and template responses. Separate child packages adapt Django and Jinja2 engines and provide template-loading strategies. Together these components power template rendering through Django's configured backends. Merged `backends/`: This package adapts engine implementations to Django's common template backend interface. Merged `loaders/`: This package implements template discovery strategies for Django's template engine.

## Major Responsibilities

Tokenize, parse, compile, and render template source; supply built-in tags and filters; manage context and template discovery; and expose engine backends and response integration. Merged `backends/`: Define the backend contract and expose implementations that normalize engine loading, template rendering, and exception translation. Merged `loaders/`: Locate templates by name, return source and origin metadata, and cache loader results when configured.

## Technology Notes

Python template engine with Django's own template syntax and optional Jinja2 backend integration. Merged `backends/`: Python adapter layer for Django templates and Jinja2. Merged `loaders/`: Python pluggable loader classes with filesystem and in-memory sources.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `backends` : This package adapts engine implementations to Django's common template backend interface. It includes the base wrapper, Django Template Language backend, optional Jinja2 backend, and a dummy backend. Shared utilities resolve template names and handle backend-specific exceptions. The adapters let applications use configured engines through a consistent API. Define the backend contract and expose implementations that normalize engine loading, template rendering, and exception translation.
- `loaders` : This package implements template discovery strategies for Django's template engine. Loaders can search configured directories, app template directories, in-memory mappings, and caches. A shared base defines loader results and template origins, while the cached loader wraps another loader. These strategies allow engine configuration to select how template sources are found. Locate templates by name, return source and origin metadata, and cache loader results when configured.

## Files
- `autoreload.py` (Size : 2124 bytes): Connects template sources and engine loaders to Django's autoreloader so template changes can trigger reloads.
    - Tags: [autoreload, django, python, templates]

- `backends/base.py` (Size : 2884 bytes): Defines the common backend wrapper, including configuration handling and template retrieval through backend-specific implementations.
    - Tags: [backend-api, python, template-backends]

- `backends/django.py` (Size : 6145 bytes): Implements the backend for Django's template engine, translating configured options into an `Engine` and adapting rendered templates.
    - Tags: [django-template-language, python, template-backends]

- `backends/dummy.py` (Size : 1802 bytes): Implements a backend that deliberately fails template retrieval, useful when a configured backend must not render templates.
    - Tags: [dummy-backend, python, template-backends]

- `backends/jinja2.py` (Size : 4161 bytes): Adapts Jinja2 environments to Django's template backend API, including template rendering and exception translation.
    - Tags: [jinja2, python, template-backends]

- `backends/utils.py` (Size : 439 bytes): Provides small shared template-backend utility behavior.
    - Tags: [python, template-backends, utilities]

- `base.py` (Size : 45899 bytes): Implements the template token, parser, node, compiled-template, and rendering foundations, including parsing and compiling source into a node tree.
    - Tags: [compiler, parser, python, template-engine]
    - TODO/FIXME/NOTE: line 487 NOTE

- `context.py` (Size : 9788 bytes): Implements template context stacks and rendering contexts, including variable lookup, context processors, and context scoping.
    - Tags: [context, python, template-engine]

- `context_processors.py` (Size : 2805 bytes): Provides standard context processors for settings, request, authentication, messages, and related template context values.
    - Tags: [context-processors, python, templates]

- `defaultfilters.py` (Size : 29414 bytes): Registers built-in template filters for formatting, string manipulation, escaping, dates, numbers, and collection operations.
    - Tags: [filters, python, template-language]

- `defaulttags.py` (Size : 56775 bytes): Registers built-in template tags and node implementations for control flow, URL generation, includes, blocks, cycles, and other template statements.
    - Tags: [control-flow, python, template-language]

- `engine.py` (Size : 8635 bytes): Implements the configured Django template `Engine`, combining loaders, built-in libraries, context processors, and template compilation settings.
    - Tags: [configuration, engine, python, template-engine]

- `exceptions.py` (Size : 1386 bytes): Defines template-specific exceptions for syntax, lookup, and rendering failures.
    - Tags: [exceptions, python, template-engine]

- `library.py` (Size : 17748 bytes): Implements registration libraries and decorators for custom template tags and filters, including metadata for argument parsing and safety.
    - Tags: [filters, libraries, python, template-tags]

- `loader.py` (Size : 2120 bytes): Exposes convenience functions for locating, compiling, and rendering templates through configured engines.
    - Tags: [loaders, python, template-engine]

- `loaders/app_directories.py` (Size : 325 bytes): Exposes the loader that searches installed applications' template directories.
    - Tags: [applications, python, template-loaders]

- `loaders/base.py` (Size : 1687 bytes): Defines the base loader interface and template origin/source records used by loader implementations.
    - Tags: [loader-api, python, template-loaders]

- `loaders/cached.py` (Size : 3816 bytes): Wraps a configured loader with template caching and invalidation behavior.
    - Tags: [caching, python, template-loaders]

- `loaders/filesystem.py` (Size : 1551 bytes): Searches configured filesystem template directories and returns matching source and origin information.
    - Tags: [filesystem, python, template-loaders]

- `loaders/locmem.py` (Size : 698 bytes): Loads templates from an in-memory name-to-source mapping.
    - Tags: [in-memory, python, template-loaders]

- `loader_tags.py` (Size : 13896 bytes): Implements parsing and rendering nodes for template inheritance, inclusion, and related loader-level tags.
    - Tags: [inheritance, loaders, python, template-tags]

- `response.py` (Size : 5748 bytes): Implements `TemplateResponse` and rendering response behavior that defers template rendering until needed in the response lifecycle.
    - Tags: [http, python, template-response]

- `smartif.py` (Size : 6698 bytes): Provides the expression parser used by conditional template tags to evaluate boolean expressions.
    - Tags: [expressions, parser, python, template-language]

- `utils.py` (Size : 3681 bytes): Contains shared template utilities for engine lookup, template origin metadata, and template string handling.
    - Tags: [python, template-engine, utilities]

- `__init__.py` (Size : 1940 bytes): Exposes the public template engine, context, loader, and template exception APIs.
    - Tags: [django, python, template-engine]

---

## Links Child Folder docmaps

None.

# Related Features

Django template parsing and rendering, built-in tags and filters, engine configuration, template loading, and rendered HTTP responses. Merged `backends/`: Configurable template engines and Django/Jinja2 backend integration. Merged `loaders/`: Template source discovery from files, installed apps, memory, and cached loader results.

# Agent Guidance

## Read When

Tracing template compilation, rendering, contexts, built-ins, backend selection, or template discovery. Merged `backends/`: Investigating configured template backend behavior or engine adapters. Merged `loaders/`: Investigating template lookup order, origin tracking, caching, or loader configuration.

## Modify When

Changing Django template syntax, core rendering semantics, built-ins, or backend/loader integration. Merged `backends/`: Changing the common backend API or engine-specific adaptation. Merged `loaders/`: Changing loader implementations or introducing a template source strategy.

## Avoid Modifying When

Changing an application's template markup or an unrelated response middleware. Merged `backends/`: Changing Django Template Language parsing internals. Merged `loaders/`: Changing template parsing or engine backend configuration.
