# Feature Map

This map is derived only from the generated root and folder docmaps. It describes documented capabilities and points to the indexes that contain their source summaries. Requirements or tests not represented in those indexes are called out rather than inferred.

## Framework setup and project scaffolding

- **Requirements:** Not available in the generated docmaps.
- **Design:** Settings configuration, app loading, command-line startup, and generated project/app templates are described as separate framework areas.
- **Source:** `django/docmap.md` (package setup and app registry); `django/conf/docmap.md` (settings, URL helpers, project and app templates).
- **Tests:** Not available in the generated docmaps.
- **Documented markers:** No feature-specific markers cited in these index summaries.

## HTTP request handling and routing

- **Requirements:** Not available in the generated docmaps.
- **Design:** Request handlers cover WSGI and ASGI lifecycles, middleware and view invocation, and exception-to-response conversion. URL indexes describe route construction, resolution, and reverse lookup.
- **Source:** `django/core/docmap.md` (handlers); `django/docmap.md` (merged HTTP and URL packages); `django/middleware/docmap.md`.
- **Tests:** Not available in the generated docmaps.
- **Documented markers:** `django/core/docmap.md` records a FIXME in `handlers/asgi.py` at line 166.

## Database models and persistence

- **Requirements:** Not available in the generated docmaps.
- **Design:** Django's database package separates ORM models and query operations from connection, transaction, migration, and backend support. Backend implementations expose database-specific behavior.
- **Source:** `django/docmap.md` (merged database package); `django/contrib/postgres/docmap.md`; `django/contrib/gis/docmap.md` (GeoDjango database support).
- **Tests:** Not available in the generated docmaps.

## Forms and validation

- **Requirements:** Not available in the generated docmaps.
- **Design:** Form fields validate and normalize submitted values; regular and model forms coordinate binding, errors, model metadata, and persistence. Widgets, formsets, and template renderers provide presentation and grouped form behavior.
- **Source:** `django/forms/docmap.md`; `django/template/docmap.md`.
- **Tests:** Not available in the generated docmaps.
- **Documented markers:** `django/forms/docmap.md` lists NOTE markers in `fields.py`, `forms.py`, and `models.py`, and a FIXME in `models.py`; exact lines are recorded in that docmap.

## Administrative site

- **Requirements:** Not available in the generated docmaps.
- **Design:** The admin package registers models, builds changelists and edit forms, applies permissions, and provides actions, filters, checks, and audit logging. Its templates and static assets are indexed as child areas.
- **Source:** `django/contrib/admin/docmap.md`.
- **Tests:** Not available in the generated docmaps.
- **Documented markers:** `django/contrib/admin/docmap.md` records a TODO in `options.py` at line 489.

## Authentication, sessions, and messages

- **Requirements:** Not available in the generated docmaps.
- **Design:** Authentication, session storage and middleware, and user-facing message storage are separate optional applications. Sessions support backend-specific persistence; the messages package documents storage implementations.
- **Source:** `django/contrib/auth/docmap.md`; `django/contrib/sessions/docmap.md`; `django/contrib/messages/docmap.md`.
- **Tests:** Not available in the generated docmaps.

## Static files

- **Requirements:** Not available in the generated docmaps.
- **Design:** Static-file finders locate assets, storage handles collection and serving, and management commands provide collection, discovery, and development-serving workflows.
- **Source:** `django/contrib/staticfiles/docmap.md`; admin asset summaries in `django/contrib/admin/docmap.md`.
- **Tests:** Not available in the generated docmaps.

## Geospatial features

- **Requirements:** Not available in the generated docmaps.
- **Design:** GeoDjango documents GIS fields, spatial queries and backends, geometry forms and widgets, GDAL/GEOS interfaces, GeoJSON serialization, sitemap output, and browser map assets.
- **Source:** `django/contrib/gis/docmap.md`.
- **Tests:** Not available in the generated docmaps.

## Sitemap and syndication output

- **Requirements:** Not available in the generated docmaps.
- **Design:** Sitemap APIs produce paginated URL data and sitemap responses; syndication views generate feed responses from application objects.
- **Source:** `django/contrib/docmap.md` (merged `sitemaps/` and `syndication/` summaries).
- **Tests:** Not available in the generated docmaps.

## Pull-request quality tooling

- **Requirements:** Not available in the generated docmaps.
- **Design:** Repository scripts include a pull-request quality checker that consults GitHub and Trac data and aggregates validation results. Its tests are represented in the merged script-folder summaries.
- **Source:** `scripts/docmap.md` (merged `pr_quality` content).
- **Tests:** The merged test summary in `scripts/docmap.md` describes checks for ticket extraction/status, title and description requirements, AI disclosure, checklists, polling, and result reporting.
