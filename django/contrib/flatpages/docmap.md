---
folder: "django/contrib/flatpages"
generated_on: "2026-10-03"
num_files: 10
semantic_tags: [admin, app-config, csrf, django, flatpages, forms, http, middleware, migrations, models, routing, sitemap, sites, template-tags, templates, urls, validation, views, visibility]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django’s flatpages application, which stores and serves site-associated pages through database-backed models. Its code defines flatpage administration, form validation, URL routing, view rendering, and 404 fallback middleware. Flatpages can be restricted to authenticated users and rendered with a configured template or the default template. Sitemap integration exposes eligible pages when the sites application is installed. Merged `migrations/`: This folder contains the initial database migration for Django’s flatpages application. Merged `templatetags/`: This folder provides the Django template tag interface for retrieving flatpage objects.

## Major Responsibilities

The application configures the flatpages app, defines the `FlatPage` model, and provides an admin form and registration interface. Its view resolves pages for the current site, applies login redirects and template rendering, while middleware retries eligible 404 responses as flatpages. URL configuration routes requests to the view, and the sitemap class returns public flatpages for the current site. Merged `migrations/`: Defines the `FlatPage` model’s fields, many-to-many site association, and database metadata. The migration declares a prerequisite on the sites application’s initial migration. Merged `templatetags/`: The tag parser validates the `{% get_flatpages %}` syntax and configures a `FlatpageNode`. When rendered, the node selects flatpages for the current site, using the request's site when available or `SITE_ID` otherwise. It can restrict results to a URL prefix and excludes registration-required pages for anonymous or unspecified users. The resulting queryset is stored under the requested context name.

## Technology Notes

The implementation uses Django models, forms, admin, URL routing, views, middleware, templates, and the sites and sitemap APIs. Merged `migrations/`: Uses Django’s migration operations and model field definitions to create application schema. Merged `templatetags/`: This folder uses Django's template tag and node APIs, flatpage models, and current-site lookup.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `migrations` : This folder contains the initial database migration for Django’s flatpages application. The migration establishes the database representation for flat pages and connects that schema to the sites application. Defines the `FlatPage` model’s fields, many-to-many site association, and database metadata. The migration declares a prerequisite on the sites application’s initial migration.
- `templatetags` : This folder provides the Django template tag interface for retrieving flatpage objects. Its implementation is contained in `flatpages.py`. The tag makes the pages available to templates through a named context variable. It supports filtering by site, URL prefix, and user visibility. The tag parser validates the `{% get_flatpages %}` syntax and configures a `FlatpageNode`. When rendered, the node selects flatpages for the current site, using the request's site when available or `SITE_ID` otherwise. It can restrict results to a URL prefix and excludes registration-required pages for anonymous or unspecified users. The resulting queryset is stored under the requested context name.

## Files
- `admin.py` (Size : 723 bytes): Registers `FlatPageAdmin` with Django’s admin site and uses the flatpage-specific model form. Its fieldsets expose URL, title, content, site associations, registration restrictions, and template selection. The list display shows URL and title, while filters cover sites and registration requirements. Search is available for URL and title.
    - Tags: [admin, flatpages, models]

- `apps.py` (Size : 260 bytes): Defines `FlatPagesConfig`, the Django application configuration for `django.contrib.flatpages`. It sets `AutoField` as the default primary-key field type. The configuration provides the translated “Flat Pages” display name. It contains no runtime page-handling logic.
    - Tags: [app-config, django, flatpages]

- `forms.py` (Size : 2566 bytes): Defines `FlatpageForm`, a model form for `FlatPage` with URL syntax and length validation. It requires a leading slash and conditionally requires a trailing slash based on `APPEND_SLASH` and `CommonMiddleware`. Form-wide validation prevents a URL from being assigned to the same site on multiple flatpages. Validation errors use Django’s translated messages and named error codes.
    - Tags: [django, flatpages, forms, validation]

- `middleware.py` (Size : 826 bytes): Implements `FlatpageFallbackMiddleware`, which only attempts flatpage resolution for responses with status 404. It calls the flatpage view with the request path and returns the original 404 if the view also raises `Http404`. Other exceptions are re-raised in debug mode and otherwise leave the original response unchanged. The middleware declares that it is not async-capable.
    - Tags: [django, flatpages, middleware]

- `migrations/0001_initial.py` (Size : 2476 bytes): Defines the initial `FlatPage` database model and its schema options, including URL-based ordering and the `django_flatpage` table name. The model contains page URL, title, content, comment, template, registration, and site-association fields. It uses Django migration operations and model fields to create the schema. The migration declares `sites.0001_initial` as a prerequisite.
    - Tags: [django, flatpages, migrations, sites]

- `models.py` (Size : 1813 bytes): Defines the `FlatPage` database model, including its URL, title, HTML content, comment setting, template, registration requirement, and associated sites. Model metadata specifies the table name, translated singular and plural names, and URL ordering. `get_absolute_url()` tries to reverse the flatpage view for normalized URL forms. If reversal fails, it constructs a URI using the script prefix.
    - Tags: [django, flatpages, models, sites, urls]

- `sitemaps.py` (Size : 598 bytes): Defines `FlatPageSitemap`, a Django sitemap whose items are non-registration-required flatpages for the current site. It checks that `django.contrib.sites` is installed and raises `ImproperlyConfigured` otherwise. Site lookup uses the sites model and its current-site manager method. The returned queryset excludes pages that require registration.
    - Tags: [django, flatpages, sitemap, sites]

- `templatetags/flatpages.py` (Size : 3653 bytes): Defines the `get_flatpages` template tag and its `FlatpageNode`. The tag accepts an optional URL prefix, optional user, and required context variable name, rejecting invalid syntax with `TemplateSyntaxError`. At render time it selects pages associated with the current site and filters by the optional prefix. Pages requiring registration are excluded when no user is specified or the supplied user is unauthenticated.
    - Tags: [django, flatpages, template-tags, visibility]

- `urls.py` (Size : 185 bytes): Declares the flatpages URL pattern using Django’s `path()` routing API. The `<path:url>` converter captures a URL path and dispatches it to `views.flatpage`. The route is assigned the fully qualified flatpage-view name. This file contains no additional routing or view logic.
    - Tags: [django, flatpages, routing, urls]

- `views.py` (Size : 2794 bytes): Implements the public `flatpage` view, which normalizes the requested URL and finds a page associated with the current site. When slash-appending is enabled, it retries a missing trailing-slash URL and redirects permanently to the slash form. The CSRF-protected `render_flatpage` helper enforces registration requirements, selects the configured or default template, and renders the page. It marks the stored title and content as safe HTML before placing the page in the template context.
    - Tags: [csrf, django, flatpages, http, templates, views]

---

## Links Child Folder docmaps

None.

# Related Features

This folder owns the database-backed flatpages feature, including admin editing, URL validation, site association, page rendering, 404 fallback, sitemap exposure, and route configuration. Template-tag retrieval and database migration details are documented in the linked child indexes. Merged `migrations/`: Initial database schema for flat pages, including their association with sites. Merged `templatetags/`: This folder implements the template-facing retrieval of site-specific flatpages, including URL-prefix selection and visibility filtering based on user authentication.

# Agent Guidance

## Read When

Read this folder when changing flatpage data fields, admin editing, URL validation or routing, page rendering, authentication restrictions, 404 fallback behavior, or sitemap integration. Merged `migrations/`: Changing the initial flatpages schema or investigating how flat-page fields and site associations were first created. Merged `templatetags/`: Read this folder when changing the `{% get_flatpages %}` template tag syntax, its context output, site selection, or page visibility behavior.

## Modify When

Modify the file that owns the behavior: `models.py` for stored page data and URLs, `forms.py` for validation, `admin.py` for admin presentation, `views.py` for resolution and rendering, `middleware.py` for 404 fallback, `urls.py` for routing, `sitemaps.py` for sitemap inclusion, and `apps.py` for app configuration. Merged `migrations/`: Only when intentionally changing or documenting the historical initial migration; create a new migration for subsequent schema changes. Merged `templatetags/`: Modify `flatpages.py` when updating template tag parsing or flatpage queryset filtering.

## Avoid Modifying When

Avoid changing files in this folder for template-tag behavior or historical migration changes; consult `templatetags/docmap.md` or `migrations/docmap.md` respectively. Merged `migrations/`: Making ordinary flatpages model or schema changes that belong in a new migration rather than this initial migration. Merged `templatetags/`: Avoid changes here for flatpage models, administration, views, or other behavior not owned by the template tag.
