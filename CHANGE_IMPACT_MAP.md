# Change Impact Map

Likely affected areas below are derived from responsibilities and relationships stated in the generated docmaps. They are navigation hints, not a dependency graph.

## Settings, startup, or project scaffolding change

- `django/conf/docmap.md` — Settings access, defaults, project/app templates, and configuration URL helpers.
- `django/docmap.md` — Package setup and application registry summaries.

## HTTP handling, middleware, or URL routing change

- `django/core/docmap.md` — WSGI/ASGI handlers, middleware execution, and exception-to-response conversion.
- `django/middleware/docmap.md` — Request/response middleware.
- `django/docmap.md` — Merged HTTP and URL package summaries.

## Database or ORM behavior change

- `django/docmap.md` — Merged database package summary covering initialization, transactions, connections, ORM, migrations, and backends.
- `django/contrib/postgres/docmap.md` — PostgreSQL-specific database and ORM extensions.
- `django/contrib/gis/docmap.md` — GeoDjango spatial fields, queries, and backends.

## Form validation, widgets, or form rendering change

- `django/forms/docmap.md` — Fields, validation, forms, formsets, model forms, widgets, renderers, and built-in template summaries.
- `django/template/docmap.md` — Template parsing, rendering, tags, filters, backends, and loaders.
- `django/contrib/admin/docmap.md` — Admin form and widget integration.

## Admin page, action, or browser asset change

- `django/contrib/admin/docmap.md` — Admin registration, permissions, actions, filters, forms, templates, tags, views, and static assets.
- `django/contrib/admin/static/admin/css/docmap.md` — Admin styles, themes, RTL, and responsive rules.
- `django/contrib/admin/static/admin/img/docmap.md` — Admin vector assets and attribution.
- `django/contrib/admin/static/admin/js/docmap.md` — Admin browser interactions and widgets.

## Authentication or session behavior change

- `django/contrib/auth/docmap.md` — Authentication APIs and supporting areas.
- `django/contrib/sessions/docmap.md` — Session middleware, models, serializers, and backend summaries.
- `django/contrib/admin/docmap.md` — Admin authentication and permission-aware behavior.

## Message storage or presentation change

- `django/contrib/messages/docmap.md` — Message APIs, middleware, context integration, and storage.
- `django/template/docmap.md` — Template context processors and rendering.

## Static-file discovery, storage, or serving change

- `django/contrib/staticfiles/docmap.md` — Finders, storage, handlers, URLs, views, and management commands.
- `DOCMAP.md` — Root package and browser-tool configuration entries.

## GIS or spatial-data change

- `django/contrib/gis/docmap.md` — GeoDjango APIs and summaries for GIS database, GDAL/GEOS, forms, serialization, maps, and templates.

## Release, translation, or repository quality tooling change

- `scripts/docmap.md` — Release, branch, translation, migration-check, and pull-request quality tooling summaries.
- `DOCMAP.md` — Root packaging, tox, JavaScript, formatting, and workflow-check configuration.

## Testing infrastructure change

- `django/docmap.md` — Merged Django test framework and test-client summary.
- `scripts/docmap.md` — Merged pull-request quality checker tests.
- `DOCMAP.md` — Root tox and JavaScript test configuration summaries.
