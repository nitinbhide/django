---
folder: "."
generated_on: "2026-10-03"
num_files: 950
semantic_tags: [admin, database, django, framework, gis, http, javascript, orm, python, templates, testing, web]
todos_present: true
dependencies: []
---

# Repository Overview

Django is a high-level Python web framework for building web applications. The repository contains the `django` framework package, optional `contrib` applications, and scripts supporting development and quality checks. The framework is organized into packages for configuration, HTTP, URL routing, forms, templates, database access, middleware, and reusable views. Its database layer supports backend-specific integrations, including geospatial functionality. Tests, documentation, and build configuration complement the implementation.

- Repository purpose: develop and distribute the Django web framework.
- Business domain: web application development, HTTP request handling, data access, and related application services.
- Overall architecture: a modular Python framework with reusable core packages, optional applications, pluggable backends, and template-driven rendering.

## Technology Summary

Detected from the repository inventory and package/build configuration:

- Languages and formats: Python, JavaScript, CSS, HTML/Django templates, Jinja2 templates, and SQL-related backend code.
- Frameworks and libraries: Django, `asgiref`, `sqlparse`, and optional `argon2-cffi` and `bcrypt`.
- Databases: backend support is organized for SQLite, PostgreSQL, MySQL, and Oracle; GeoDjango adds spatial backend support.
- Build and test tooling: setuptools, tox, Grunt, QUnit, Biome, Black, Flake8, and isort.
- Python requirement: Python 3.12 or greater; the package metadata lists Python 3.12, 3.13, and 3.14 classifiers.

## Architecture Summary

Django exposes framework APIs through cohesive packages that separate settings and app loading, request/response handling, routing, middleware, forms, templates, database models and backend adapters. Optional `contrib` packages provide capabilities such as authentication, administration, sessions, sites, static files, PostgreSQL-specific operations, and geospatial support. Backend interfaces and template engines provide extension points while shared framework services support application code. Folder indexes provide progressively deeper summaries of implementation areas.

## Business Capability Summary

The repository supports application configuration and scaffolding, user authentication and authorization, model administration, forms and validation, database-backed application models, sessions and messages, static-file handling, URL routing, template rendering, and GIS features. Django also provides testing utilities and development tooling for applications built on the framework.

# Module Dependency Graph

Dependency graph generation is reserved for a future requirement and is not included in this index. The `dependencies` metadata field remains an empty list.

# Repository Navigation

## Specialized Cross Navigation Maps

- `FEATURE_MAP.md` : Documented capabilities, their source indexes, test availability, and recorded markers.
- `ARCHITECTURE_MAP.md` : Framework organization, architectural patterns, responsibilities, and explicit constraints.
- `TECHNOLOGY_MAP.md` : Languages, frameworks, dependencies, databases, build tooling, and discoverable versions.
- `TESTING_MAP.md` : Test strategy, documented coverage areas, and test-suite references.
- `CHANGE_IMPACT_MAP.md` : Common change scenarios and related folder indexes.

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

None.

## Folders

- `django/docmap.md` — Django's top-level Python package and its framework modules.
- `scripts/docmap.md` — Repository scripts and their quality-check tooling.

## Files

- `AUTHORS`: Lists contributors acknowledged for work on Django. The entries recognize patches, bug reports, translations, community support, and related contributions. Names are accompanied by contact or profile details where provided. The file describes itself as an incomplete list.
    - Size : 47410 bytes
    - Tags: [acknowledgements, contributors, project-history]
- `biome.json`: Configures Biome formatting and linting for selected Django admin, GIS, and documentation CSS and JavaScript files. Its schema declaration identifies Biome `2.4.15`. Include patterns select the relevant source areas and exclude vendor, generated, and minified assets. Rule overrides customize selected complexity, correctness, style, and suspicious-code checks; JSON formatting and linting are disabled.
    - Size : 1743 bytes
    - Tags: [biome, css, javascript, linting]
- `CONTRIBUTING.rst`: Introduces code patches, documentation improvements, bug reports, and patch reviews as ways to contribute. It directs contributors to the detailed contribution guidance and Code of Conduct. The file says non-trivial pull requests should have Trac tickets. It also explains that Django uses Trac to track tickets and associated patches.
    - Size : 1147 bytes
    - Tags: [contributing, development, guidelines]
- `Gruntfile.js`: Configures a QUnit task targeting `js_tests/tests.html`. It loads the Grunt QUnit plugin. The `test` task runs QUnit. The default task aliases `test`.
    - Size : 369 bytes
    - Tags: [grunt, javascript, qunit, testing]
- `INSTALL`: States that Python 3.12 or greater is required. It gives the package-install command using pip. The file directs readers to the detailed installation documentation. It is a short installation entry point rather than a complete setup guide.
    - Size : 245 bytes
    - Tags: [installation, python, setup]
- `LICENSE`: Contains Django's three-clause BSD license. It sets conditions for source and binary redistribution. The license restricts use of the Django and contributor names for endorsement without permission. It disclaims warranties and liability.
    - Size : 1579 bytes
    - Tags: [bsd, licensing]
- `LICENSE.python`: Explains that Django includes code from the Python standard library. It identifies the Python license as the applicable permissive license for that code. The file reproduces the Python license history and terms. Its stated purpose is compliance with Python's licensing conditions.
    - Size : 14544 bytes
    - Tags: [licensing, python, software-license]
- `MANIFEST.in`: Defines files and directories included in Django's source distribution. It includes selected root metadata and grafts the framework, documentation, extras, JavaScript-test, and test trees. It excludes compiled Python artifacts. The scripts directory is pruned from the distribution.
    - Size : 281 bytes
    - Tags: [packaging, source-distribution]
- `package.json`: Marks the npm package as private. It defines scripts for JavaScript tests and Biome checks. Development dependencies include `@biomejs/biome` `2.4.15`, Grunt, its QUnit plugin, and QUnit. The manifest declares an npm engine version constraint.
    - Size : 355 bytes
    - Tags: [biome, grunt, javascript, npm, qunit, testing]
- `pyproject.toml`: Selects setuptools as Django's build backend and declares package metadata. It requires Python 3.12 or newer, lists Python 3.12 through 3.14 classifiers, and declares runtime dependencies plus optional password-hashing extras. The project exposes the `django-admin` command-line entry point. Tool sections configure formatting, imports, dynamic version lookup, and package discovery.
    - Size : 2301 bytes
    - Tags: [build, packaging, python, setuptools]
- `README.rst`: Describes Django as a high-level Python web framework. It recommends a reading sequence covering installation, tutorials, deployment, topical guides, how-to material, and reference documentation. The file points to community and contribution channels. It also directs readers to the test-suite instructions.
    - Size : 2233 bytes
    - Tags: [documentation, getting-started, project-overview]
- `tox.ini`: Defines tox environments for Python testing, documentation, formatting, and lint checks. The Python environment runs Django's test runner from the tests directory. Additional environments cover JavaScript, documentation spelling and linting, and workflow checks. The configuration also declares test dependencies and environment variables for platform-specific integrations.
    - Size : 2661 bytes
    - Tags: [automation, documentation, linting, testing, tox]
- `zizmor.yml`: Configures zizmor checks for repository workflows. The dangerous-trigger rule ignores three named workflow files. The unpinned-uses rule requires reference pinning for the `actions/*` and `psf/*` namespaces. The file contains no further rule configuration.
    - Size : 367 bytes
    - Tags: [github-actions, security, zizmor]

---

# Instructions for AI Coding Agents

## When to Use This Index/DOCMAP

- Use docmaps to identify candidate files before searching.
- Scope source searches to the relevant package or feature directory; generated build artifacts are not source-of-truth files.
- Use this index hierarchy to understand repository architecture, locate implementation areas, find related tests and specifications, and determine likely files to read or modify.
- Avoid unnecessary broad repository exploration.

## How This Index Is Organized

This repository uses progressive disclosure. The root `DOCMAP.md` provides an overview and links to major modules; each surviving folder `docmap.md` summarizes that folder's contents and links to deeper surviving indexes; file entries describe purpose, responsibilities, tags, and any TODO/FIXME/NOTE markers.

## How to Use This Index/DOCMAP

1. Start here to understand the repository shape and top-level packages.
2. Use the specialized cross-navigation maps to locate relevant capabilities, architecture, technologies, tests, and likely change impact.
3. Follow the folder docmap links into the relevant package or feature.
4. Read source files only after narrowing the search to the relevant area.
5. Use folder summaries and semantic tags to avoid broad exploration.
6. Always read the actual source before making changes.
