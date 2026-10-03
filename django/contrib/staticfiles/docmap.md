---
folder: "django/contrib/staticfiles"
generated_on: "2026-10-03"
num_files: 12
semantic_tags: [app-configuration, asgi, cache-busting, development, django, file-discovery, live-server, management-commands, manifest, settings-validation, static-files, storage, system-checks, testing, urls, views, wsgi]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

Django’s staticfiles package supports locating, storing, URL-configuring, validating, and serving static assets. Finder classes resolve assets from configured directories, installed apps, and eligible storage backends, while storage classes generate cache-busted names and manifests. Development helpers expose static serving through WSGI/ASGI handlers and URL patterns, and testing support overlays finder-provided assets in live-server tests. The `management/` child index documents collection, discovery, and development-server commands. Merged `management/`: This folder organizes Django management commands for static files.

## Major Responsibilities

The package provides finder and storage implementations, validation checks for their settings, development-only static serving, and test-server integration. Its management commands are indexed separately under `management/`. Merged `management/`: Provide navigation to static-file management commands. Merged `management/commands/`: Provides command-line workflows for collecting and locating static assets and integrating static serving with the development server.

## Technology Notes

This Python package integrates with Django’s app configuration, system checks, storage APIs, URL routing, and WSGI/ASGI request handlers. The storage implementation processes CSS and JavaScript references to support content-hashed static asset names. Merged `management/`: The child folder uses Django's management-command framework, static-file finders and storage, and development-server integration. Merged `management/commands/`: The commands use Django's management-command framework, static-file finders and storage, and the development server's WSGI handler.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `management/commands` : This folder contains Django management commands for static-file collection, discovery, and development serving. `collectstatic` gathers assets into `STATIC_ROOT`, while `findstatic` locates assets through configured finders. The custom `runserver` command can serve static files during development. The package initializer is empty. Provides command-line workflows for collecting and locating static assets and integrating static serving with the development server.
- `management` : This folder organizes Django management commands for static files. Its `commands` child indexes workflows for collecting static assets, locating files through configured finders, and serving static files during development. No eligible files are listed directly in this folder. Merged `commands/`: This folder contains Django management commands for static-file collection, discovery, and development serving. Provide navigation to static-file management commands. Merged `commands/`: Provides command-line workflows for collecting and locating static assets and integrating static serving with the development server.

## Files
- `apps.py` (Size : 518 bytes): Configures the `django.contrib.staticfiles` application and provides its translated display name. It defines patterns for ignoring CVS directories, dot-prefixed entries, and editor backup files. At startup, `ready()` registers finder and storage validation checks with Django’s staticfiles system-check tag. This is the app-setup integration point for the checks implemented in `checks.py`.
    - Tags: [app-configuration, django, static-files, system-checks]

- `checks.py` (Size : 865 bytes): Defines the `staticfiles.E005` error for a missing static-files storage alias. `check_finders()` invokes checks on configured finders and skips those that do not implement checking. `check_storages()` verifies that the static-files alias exists in `settings.STORAGES`. Both functions return Django system-check errors for registration by the application configuration.
    - Tags: [django, static-files, system-checks]

- `finders.py` (Size : 11392 bytes): Implements finder interfaces and concrete finders for configured filesystem directories, installed applications, and storage backends. Finders locate individual assets or list files, while the module-level `find()` searches the configured finder set and can return the first match or all matches. `get_finder()` imports and validates finder classes, caching constructed instances. Finder checks and the shared `searched_locations` list support configuration validation and tracking searched roots.
    - Tags: [django, file-discovery, static-files, storage]

- `handlers.py` (Size : 4157 bytes): Provides shared request handling that maps paths beneath `STATIC_URL` to filesystem paths and serves them through the staticfiles view. `StaticFilesHandler` wraps WSGI requests, while `ASGIStaticFilesHandler` wraps HTTP ASGI requests and delegates unrelated requests to the wrapped application. Both handlers return normal exception responses for missing files. The ASGI implementation adapts synchronous streaming content and registers request cleanup.
    - Tags: [asgi, django, static-files, wsgi]

- `management/commands/collectstatic.py` (Size : 16651 bytes): This module implements the `collectstatic` management command, which gathers static files into `STATIC_ROOT`. It supports copying or symlinking, dry-run operation, conflict handling, and post-processing. The command tracks modified, unmodified, skipped, and deleted files and reports according to verbosity. It also handles output and errors from the collection process.
    - Tags: [cli-command, conflict-handling, django-admin, file-operations, static-files, symlink]

- `management/commands/findstatic.py` (Size : 1691 bytes): This module implements the `findstatic` command for locating static asset paths through Django's configured finders. It can report all matches or stop after the first match. Verbose output can include the locations searched. The command reports results using Django's management-command output handling.
    - Tags: [cli-command, django-admin, file-discovery, static-files]

- `management/commands/runserver.py` (Size : 1409 bytes): This module extends Django's development server command to serve static files. It wraps the normal handler with `StaticFilesHandler` when static serving is enabled. The command adds `--nostatic` and `--insecure` options to control this behavior. Insecure serving can be enabled when `DEBUG` is false.
    - Tags: [cli-command, development-server, django-admin, static-files, wsgi-handler]

- `storage.py` (Size : 25023 bytes): Implements static-filesystem storage using `STATIC_ROOT` and `STATIC_URL`, and rejects filesystem path requests when `STATIC_ROOT` is unset. `HashedFilesMixin` derives content-hashed names and iteratively rewrites supported CSS and JavaScript asset references while avoiding comments and string literals. `ManifestFilesMixin` loads and writes the `staticfiles.json` path manifest and applies strict or fallback behavior for missing entries. `staticfiles_storage` lazily resolves the configured static-files storage alias.
    - Tags: [cache-busting, django, manifest, static-files, storage]
    - TODO/FIXME/NOTE: `storage.py:293` — `            # CSS / JS?). Note that STATIC_URL cannot be empty.`

- `testing.py` (Size : 476 bytes): Defines `StaticLiveServerTestCase` as an extension of Django’s `LiveServerTestCase`. It selects `StaticFilesHandler` as the live server’s static handler. That handler uses staticfiles finders to expose assets during test execution. The documented behavior avoids requiring `collectstatic` as part of test setup.
    - Tags: [django, live-server, static-files, testing]

- `urls.py` (Size : 517 bytes): Exposes `staticfiles_urlpatterns()`, which builds URL patterns for the configured static URL prefix or an explicitly supplied prefix using the staticfiles view. The module initializes an empty `urlpatterns` list. When `DEBUG` is enabled and the list is empty, it appends the generated static-file patterns.
    - Tags: [django, static-files, urls, views]

- `utils.py` (Size : 2350 bytes): Implements case-sensitive wildcard matching for ignore patterns and recursively yields files from a storage while applying ignores to file names, paths, and directories. `check_settings()` validates that `STATIC_URL` is configured and does not conflict with `MEDIA_URL`. It also rejects overlapping media and static roots and, in debug mode, media URLs nested beneath the static URL. These utilities are shared by the package’s finder, storage, and serving components.
    - Tags: [django, settings-validation, static-files]

- `views.py` (Size : 1302 bytes): Implements the development static-file serving view and documents that it is not intended for production. It requires `DEBUG` unless explicitly invoked with `insecure=True`, normalizes the requested path, and resolves it through the configured staticfiles finders. Missing files and directory-index requests raise `Http404`; found files are served by Django’s generic static view. The `insecure` option is used by the development handlers.
    - Tags: [development, django, static-files, views]

---

## Links Child Folder docmaps

None.

# Related Features

Static asset discovery, collection and content-hashed storage, development-time serving, static URL configuration, and static-file access in live-server tests. Merged `management/`: Django static-file management and development serving. Merged `management/commands/`: Static asset collection, finder-based path discovery, and static-file serving from Django's development server.

# Agent Guidance

## Read When

Changing static asset lookup, storage or manifest behavior, URL generation, system checks, development serving, or staticfiles integration in live-server tests. Merged `management/`: Locating or changing commands for static-file collection, discovery, or serving. Merged `management/commands/`: Changing staticfiles command-line behavior for asset collection, discovery, or development serving.

## Modify When

The requested behavior belongs to a finder, storage backend, check, request handler, URL helper, or utility in this package. For management-command changes, consult `management/docmap.md`. Merged `management/`: The requested change concerns organization of staticfiles command resources. Merged `management/commands/`: The requested change concerns command arguments, collection output, finder results, or static serving through `runserver`.

## Avoid Modifying When

The change concerns an unrelated Django subsystem or a management command implementation rather than these package-level integrations. Merged `management/`: Changing an individual command implementation; use the commands folder index. Merged `management/commands/`: Changing static-file storage or finder behavior without a management-command requirement.

## Dependency Graph

Not generated. `dependencies` is empty; no dependencies were inferred.
