---
folder: "django/contrib/sites"
generated_on: "2026-10-03"
num_files: 11
semantic_tags: [app-configuration, database, django, django-admin, django-management, django-middleware, django-migrations, django-orm, domain-validation, model, post-migrate, queryset-filtering, request-processing, request-routing, request-site, schema, settings-validation, signals, sites-framework, system-checks]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django’s sites framework, which represents sites associated with a project and resolves the current site from configuration or a request. It provides the persisted `Site` model, its managers, and a non-persistent request-backed fallback. Application setup, migration-time initialization, request middleware, system checks, and admin integration connect these capabilities to Django. The `migrations` child folder documents the schema history, including creation of the sites table and the domain uniqueness constraint. Merged `migrations/`: This folder records database schema changes for Django's sites application.

## Major Responsibilities

The modules define site storage and lookup, filter related model querysets for the configured site, validate `SITE_ID` and manager relationships, and clear cached lookups when site records change. They also provide a request-based fallback when the sites app is not installed, expose the resolved site on requests, create a default record after migration, and register administration and application-startup hooks. Merged `migrations/`: Defines the initial `django_site` table and the subsequent alteration that makes site domains unique.

## Technology Notes

The folder uses Django’s application registry, ORM, system checks, signals, middleware, management hooks, and admin framework. Merged `migrations/`: Uses Django's migration operations and model-field definitions.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `migrations` : This folder records database schema changes for Django's sites application. Its migrations create the `Site` model and then refine the domain field's uniqueness constraint. The migration sequence depends on Django's migration framework and the sites model's domain-name validator and manager. Read these files when tracing or changing the persisted schema for sites. Defines the initial `django_site` table and the subsequent alteration that makes site domains unique.

## Files
- `admin.py` (Size : 222 bytes): Registers the `Site` model with Django’s admin and defines its `SiteAdmin` presentation. The change list displays the domain and name, and both fields are searchable. This module contains the framework’s admin integration for site records.
    - Tags: [django-admin, sites-framework]

- `apps.py` (Size : 579 bytes): Defines the `SitesConfig` application configuration, including the app name, translated display name, and default auto field. Its `ready()` hook connects default-site creation to `post_migrate` and registers the site-ID system check under the sites tag. These hooks connect app initialization and migration completion to the framework’s setup behavior.
    - Tags: [app-configuration, django, post-migrate, sites-framework, system-checks]

- `checks.py` (Size : 1079 bytes): Implements `check_site_id`, a Django system check for the configured `SITE_ID`. It converts the setting through the `Site` primary-key field and reports validation errors or values whose type changes during conversion as `sites.E101`. The model import is deferred inside the check to avoid accessing models before the app registry is ready.
    - Tags: [django, settings-validation, system-checks]

- `management.py` (Size : 1693 bytes): Implements the `post_migrate` hook that creates an `example.com` `Site` record when the historical app registry contains the model, migration routing permits it, and no site already exists. The new record uses the configured `SITE_ID` or primary-key default, and verbosity controls progress output. It resets the database sequence after saving the explicitly keyed record when the backend provides reset SQL.
    - Tags: [database, django-management, sites-framework]

- `managers.py` (Size : 2059 bytes): Defines `CurrentSiteManager`, which filters its queryset using the configured `SITE_ID` and the selected `site` or `sites` relationship. The field name can be supplied explicitly; otherwise the manager selects the available default. Its system checks report missing fields and fields that are not foreign-key or many-to-many relations.
    - Tags: [django-orm, queryset-filtering, sites-framework, system-checks]

- `middleware.py` (Size : 343 bytes): Defines synchronous `CurrentSiteMiddleware` using Django’s `MiddlewareMixin`. Its request hook resolves the current site through `get_current_site` and assigns it to `request.site`. The module marks the middleware as not async-capable and delegates resolution to the shared shortcut.
    - Tags: [django-middleware, request-processing, sites-framework]

- `migrations/0001_initial.py` (Size : 1404 bytes): Defines the initial schema for the sites application by creating the `Site` model and its `django_site` table. It declares the primary key, domain and display-name fields, default ordering, and site-specific manager. The domain field uses the sites model's simple domain-name validator. This is the starting migration on which later sites migrations build.
    - Tags: [django-migrations, schema, sites-framework]

- `migrations/0002_alter_domain_unique.py` (Size : 570 bytes): Alters the `Site.domain` field introduced by the initial migration. The updated field has a uniqueness constraint while retaining its length, verbose name, and simple domain-name validator. Its migration dependency is `sites.0001_initial`. Apply this migration when following the schema change that prevents duplicate site domains.
    - Tags: [django-migrations, schema, sites-framework]

- `models.py` (Size : 3815 bytes): Defines the persisted `Site` model, its `SiteManager`, and a validator that rejects whitespace in domain values. The manager resolves a site by configured ID or request host, caches lookups, and retries host lookup after removing the port. The model stores a unique domain and display name and exposes natural-key support. Save and delete signal handlers clear cached entries for the affected site.
    - Tags: [django-orm, domain-validation, model, signals, sites-framework]

- `requests.py` (Size : 661 bytes): Defines `RequestSite`, a lightweight object exposing the `domain` and `name` attributes from an HTTP request’s host. Its string representation is the domain, and it does not persist data. Its `save()` and `delete()` methods raise `NotImplementedError`.
    - Tags: [request-site, sites-framework]

- `shortcuts.py` (Size : 591 bytes): Implements `get_current_site` to resolve a site from a request. When `django.contrib.sites` is installed, it imports the `Site` model inside the function and delegates lookup to its manager; otherwise, it returns a `RequestSite`. The deferred import avoids loading the model for optional use without the sites application.
    - Tags: [request-routing, sites-framework]

---

## Links Child Folder docmaps

None.

# Related Features

Site records and domain names; resolving the current site from settings or an HTTP request; exposing the resolved site through middleware; validating `SITE_ID`; filtering model querysets by site; and creating a default site after migration. Merged `migrations/`: Database persistence and schema evolution for the Django sites framework, including the `Site` model and unique domain names.

# Agent Guidance

## Read When

Read this folder when working on site lookup, `Site` model or manager behavior, `SITE_ID` validation, request middleware, default-site initialization, admin integration, or site-specific queryset filtering. Read `migrations/docmap.md` when investigating the schema history. Merged `migrations/`: Read these migrations when investigating the sites database schema, the `Site.domain` constraint, or the migration sequence that creates and alters the model.

## Modify When

Modify the relevant module when changing site resolution, persistence, validation, request integration, setup hooks, or admin presentation. Add schema changes through a new migration in the migrations folder. Merged `migrations/`: Modify or add migrations here when making a schema change to the sites application; follow the existing migration dependency sequence.

## Avoid Modifying When

Avoid changing these modules for unrelated application models or request handling that does not depend on Django’s sites framework. Merged `migrations/`: Avoid editing already-applied migrations for ordinary model changes; create a new migration instead.
