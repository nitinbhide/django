---
folder: "django/contrib/admin"
generated_on: "2026-10-03"
num_files: 35
semantic_tags: [action-choices, admin, administration, ajax, audit-log, authentication, authorization, autocomplete, change-form, change-list, changelist, contenttypes, css, database-schema, date-hierarchy, decorators, django, django-migrations, filtering, forms, html, inline-forms, javascript, json, logentry, models, orm, pagination, password-management, permissions, query-strings, search, sorting, staff, static, svg, template-overrides, template-tags, templates, timezone, urls, user-model, value-formatting, vector-graphics, views, web]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package implements Django's model-oriented administrative site and exposes its public registration and customization APIs. It combines model registration, request handling, changelist and edit-form behavior, and the presentation support needed by admin templates. The modules also provide built-in actions, filters, form fields, widgets, and system checks. Related migrations, browser assets, templates, template tags, and views are indexed in child maps. Merged `migrations/`: This folder contains the inventoried schema migrations for Django's admin application. Merged `static/`: This folder groups static assets for the Django admin. Merged `templates/`: This folder organizes HTML templates for the Django admin interface. Merged `templatetags/`: This folder provides template tags and filters used to render Django’s administration interface. Merged `views/`: This folder implements request-facing views and supporting logic for Django's admin.

## Major Responsibilities

The package defines `ModelAdmin` and `AdminSite`, registers models, prepares admin forms and filters, and handles CRUD-oriented administrative requests. It supplies model and action logging, permission-aware deletion, field and relation utilities, and validation checks for admin configuration. Public decorators and package exports provide extension points to applications. Merged `migrations/`: Create the admin action-log table and record schema changes to `LogEntry.action_time` and `LogEntry.action_flag` in migration order. Merged `static/`: Provide navigation to the Django admin static asset folders. Merged `static/admin/`: Group the admin stylesheet, image, and JavaScript asset areas and direct agents to their folder-level indexes. Merged `templates/`: Group admin-site and registration template resources and direct agents to their folder-level indexes. Merged `templates/registration/`: Renders the admin-facing pages and email content for logout and password change or reset flows. The HTML templates display form errors, confirmation messages, and workflow navigation, while protecting form submissions with CSRF tokens where applicable. Merged `templatetags/`: Registering admin-specific template tags and filters; preparing changelist pagination, headers, rows, date drill-down, search, and action context; preparing change-form controls and prepopulated-field data; preserving admin URL filters; and exposing admin log entries to templates. Merged `views/`: `autocomplete.py` validates autocomplete request parameters and returns paginated JSON results using the related `ModelAdmin` search configuration. `decorators.py` supplies the staff-membership access decorator for admin views. `main.py` defines changelist query parameters, the dynamic search form, and `ChangeList` behavior for filtering, searching, ordering, pagination, and result URLs. Changelist behavior delegates model-specific operations such as querysets, search results, permissions, and pagination to `ModelAdmin`.

## Technology Notes

The implementation builds on Django forms, ORM models and querysets, URL routing, templates, system checks, and translated UI strings. Admin pages are served through Django's request and response APIs. Merged `migrations/`: The files use Django's migration operations and ORM field definitions to describe database schema changes. Merged `static/`: The child index covers CSS, JavaScript, and SVG assets. Merged `static/admin/`: The child folders document CSS, JavaScript, SVG, and Font Awesome assets. Merged `templates/`: The child folders document Django's HTML template language, template inheritance, and internationalization tags. Merged `templates/registration/`: The files use Django's HTML template language, template inheritance, and internationalization tags. Password forms load admin styles and include CSP nonce attributes on stylesheet links. Merged `templatetags/`: Django template libraries and inclusion nodes, admin changelist and form APIs, Django URL resolution, and safe HTML formatting. Merged `views/`: The implementation is Python code built on Django's admin and authentication APIs. It uses Django ORM querysets and field metadata, forms, generic list-view support, JSON responses, URL utilities, and timezone-aware dates.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `migrations` : This folder contains the inventoried schema migrations for Django's admin application. The migrations create and evolve the `LogEntry` model used to store admin action records. They establish the model's fields, database table options, and dependencies on the configured user model and contenttypes app. Later migrations alter timestamp behavior and add choices for action flags. Create the admin action-log table and record schema changes to `LogEntry.action_time` and `LogEntry.action_flag` in migration order.
- `static/admin` : This folder organizes static assets for the Django admin interface. Its CSS child contains page, widget, theme, direction, and responsive styles. The image child documents the admin SVG assets and their Font Awesome attribution. The JavaScript child covers browser-side admin interactions and links to a nested map for date/time shortcuts and related-object popups. Group the admin stylesheet, image, and JavaScript asset areas and direct agents to their folder-level indexes.
- `static` : This folder groups static assets for the Django admin. Its `admin` child organizes the stylesheet, image, and JavaScript asset areas and links to their detailed indexes. No eligible files are listed directly in this folder. Merged `admin/`: This folder organizes static assets for the Django admin interface. Provide navigation to the Django admin static asset folders. Merged `admin/`: Group the admin stylesheet, image, and JavaScript asset areas and direct agents to their folder-level indexes.
- `templates/registration` : This folder contains Django admin templates for logout and password management. The templates cover password change, password-reset requests, reset email, token confirmation, and completion pages. Most pages extend the shared admin site layout and use translated text, breadcrumbs, and Django form context. They provide presentation for the workflow while leaving authentication and password operations to the surrounding views and forms. Renders the admin-facing pages and email content for logout and password change or reset flows. The HTML templates display form errors, confirmation messages, and workflow navigation, while protecting form submissions with CSRF tokens where applicable.
- `templates` : This folder organizes HTML templates for the Django admin interface. The `admin` child documents page layouts and reusable templates for navigation, forms, changelists, authentication, and model operations. The `registration` child covers logout and password-change or reset pages. No eligible files are listed directly in this folder. Merged `registration/`: This folder contains Django admin templates for logout and password management. Group admin-site and registration template resources and direct agents to their folder-level indexes. Merged `registration/`: Renders the admin-facing pages and email content for logout and password change or reset flows. The HTML templates display form errors, confirmation messages, and workflow navigation, while protecting form submissions with CSRF tokens where applicable.
- `templatetags` : This folder provides template tags and filters used to render Django’s administration interface. Its modules prepare changelist data, change-form controls, URL parameters, log entries, and formatted values for admin templates. The tags connect view and model-admin data to the corresponding admin template fragments, with support for per-model and per-app template overrides. It is a Django template-library layer rather than a standalone view or persistence layer. Registering admin-specific template tags and filters; preparing changelist pagination, headers, rows, date drill-down, search, and action context; preparing change-form controls and prepopulated-field data; preserving admin URL filters; and exposing admin log entries to templates.
- `views` : This folder implements request-facing views and supporting logic for Django's admin. Its files provide related-model autocomplete responses, staff-only view access, and the admin model changelist. The changelist coordinates query-string handling, filters, search, ordering, pagination, and result counts. These components use Django's admin, authentication, forms, HTTP, and ORM APIs. `autocomplete.py` validates autocomplete request parameters and returns paginated JSON results using the related `ModelAdmin` search configuration. `decorators.py` supplies the staff-membership access decorator for admin views. `main.py` defines changelist query parameters, the dynamic search form, and `ChangeList` behavior for filtering, searching, ordering, pagination, and result URLs. Changelist behavior delegates model-specific operations such as querysets, search results, permissions, and pagination to `ModelAdmin`.

## Files
- `actions.py` (Size : 3370 bytes): Implements the built-in bulk-delete action for selected model instances. It gathers related deletions and permission/protection state, logs deletions, reports results through messages, and renders a confirmation response when required. Tags: [actions, admin, deletion, forms]

- `apps.py` (Size : 867 bytes): Defines the admin `AppConfig` variants. The simple config registers admin checks without discovery, while the default config also autodiscovers application admin modules. Tags: [app-config, checks, django]

- `checks.py` (Size : 53868 bytes): Implements admin system checks for app dependencies, template configuration, model-admin options, and registered sites. It validates configuration and reports structured Django check errors. Tags: [admin, configuration, checks, models]

- `decorators.py` (Size : 4058 bytes): Provides `action`, `display`, and `register` decorators that attach admin metadata or register a `ModelAdmin` with an `AdminSite`. These helpers preserve the underlying function or class and validate registration inputs. Tags: [api, decorators, registration]

- `exceptions.py` (Size : 532 bytes): Defines exceptions for invalid admin lookups, invalid `to_field` requests, and model registration state. The lookup exceptions integrate with Django's suspicious-operation handling. Tags: [admin, exceptions, validation]

- `filters.py` (Size : 28384 bytes): Implements admin changelist filters for model fields and custom query parameters. Filter classes provide choices, expected parameters, queryset filtering, and optional facet counts. Tags: [changelist, filters, models, querysets]

- `formfields.py` (Size : 1386 bytes): Defines strict boolean and nullable-boolean form fields for admin input. The fields delegate parsing to Django's nullable boolean field while rejecting invalid values. Tags: [forms, validation, widgets]

- `forms.py` (Size : 1054 bytes): Defines authentication and password-change forms used by the admin login and account pages. The authentication form additionally requires the authenticated account to be staff. Tags: [authentication, forms, permissions]

- `helpers.py` (Size : 19000 bytes): Builds template-facing representations of admin forms and fieldsets, including readonly fields and media. It also provides helpers for action checkboxes, deleted-object display, and other admin rendering data. Tags: [forms, templates, widgets]

- `migrations/0001_initial.py` (Size : 2582 bytes): Defines the initial migration for Django admin's `LogEntry` model. It depends on the configured user model and the initial contenttypes migration. Its `CreateModel` operation declares the action timestamp, object details, action flag, change message, content type, and user fields. The model options set the `django_admin_log` table, newest-first ordering, display names, and the admin `LogEntryManager`.
    - Tags: [admin, contenttypes, django-migrations, logentry, user-model]
    - TODO/FIXME/NOTE: None

- `migrations/0002_logentry_remove_auto_add.py` (Size : 574 bytes): Alters the `LogEntry.action_time` field in the second migration. It replaces automatic timestamp behavior with `timezone.now` as the default and sets the field as non-editable. The operation retains the field's “action time” verbose name. This migration depends on `0001_initial`.
    - Tags: [admin, django-migrations, logentry, timezone]
    - TODO/FIXME/NOTE: None

- `migrations/0003_logentry_add_action_flag_choices.py` (Size : 557 bytes): Alters `LogEntry.action_flag` to provide choices for addition, change, and deletion actions. The migration keeps the field as a `PositiveSmallIntegerField` and labels it “action flag.” Its operation is an `AlterField` with the three integer-to-label choices. This migration depends on `0002_logentry_remove_auto_add`.
    - Tags: [action-choices, admin, django-migrations, logentry]
    - TODO/FIXME/NOTE: None

- `models.py` (Size : 7066 bytes): Defines the admin `LogEntry` model and manager for recording add, change, and delete events. It formats stored change messages and resolves logged objects to their admin URLs. Tags: [audit-log, models, orm]

- `options.py` (Size : 119535 bytes): Implements `ModelAdmin` and inline-admin configuration, changelist preparation, form construction, permissions, object persistence, and admin URL/view behavior. Its extension hooks let applications customize list, edit, delete, and action workflows. Tags: [changelist, forms, models, permissions, views]
    - TODO/FIXME/NOTE: line 489: TODO: this should be handled by some parameter to the ChangeList.

- `sites.py` (Size : 24594 bytes): Implements `AdminSite`, the registry and URL/view coordinator for a configured collection of model admins. It manages model registration, site checks, shared context, authentication, and admin views. Tags: [authentication, models, registration, urls, views]

- `templates/registration/logged_out.html` (Size : 490 bytes): This template extends the admin site layout and renders the logout confirmation page. It includes breadcrumbs linking back to the admin home and identifies the current page as logout. The content thanks the user for the session and offers a link to log in again. It suppresses the navigation sidebar.
    - Tags: [admin, auth, breadcrumbs, confirmation, i18n, navigation, ui]

- `templates/registration/password_change_done.html` (Size : 772 bytes): This template extends the admin site layout and displays successful password-change confirmation. Its breadcrumbs identify the password-change page and link to admin home. It overrides user links to include documentation, logout, and the color-theme control. The confirmation text is translated.
    - Tags: [admin, auth, breadcrumbs, confirmation, i18n, navigation, ui, userlinks]

- `templates/registration/password_change_form.html` (Size : 2932 bytes): This template renders the admin password-change form and extends the shared site layout. It presents the old password and two new-password fields, with field-specific help text and errors. The form includes a CSRF token and a translated error summary when validation fails. It loads admin widget and form styles with CSP nonce attributes.
    - Tags: [admin, auth, breadcrumbs, csp, css, form, i18n, static, validation]

- `templates/registration/password_reset_complete.html` (Size : 444 bytes): This template extends the admin site layout and confirms that a password has been set. It includes breadcrumbs for the password-reset flow. The page provides a link to the supplied login URL. Its user-facing text is translated.
    - Tags: [admin, auth, breadcrumbs, confirmation, i18n, navigation, ui]

- `templates/registration/password_reset_confirm.html` (Size : 1900 bytes): This template handles confirmation of a password-reset link. When `validlink` is true, it renders two new-password fields and a CSRF-protected form; otherwise, it explains that the link is invalid and asks the user to request another reset. It extends the admin site layout and displays reset-confirmation breadcrumbs. Admin styles are loaded with CSP nonce attributes.
    - Tags: [admin, auth, breadcrumbs, conditional, confirmation, csp, css, form, i18n, static, validation]

- `templates/registration/password_reset_done.html` (Size : 615 bytes): This template extends the admin site layout and reports that reset instructions have been emailed when an account exists. It also advises checking the registered address and spam folder if no message arrives. Breadcrumbs identify the password-reset page. Both messages are translated.
    - Tags: [admin, auth, breadcrumbs, confirmation, i18n, navigation, ui]

- `templates/registration/password_reset_email.html` (Size : 606 bytes): This plain-text template formats a password-reset email using translated message blocks. It constructs a confirmation URL from protocol, domain, encoded user ID, and token values. The message identifies the site and username and includes a reset-link block for customization. Autoescaping is disabled for the email body.
    - Tags: [autoescape, auth, email, i18n, plain-text, reset]

- `templates/registration/password_reset_form.html` (Size : 1214 bytes): This template renders the password-reset request form within the admin site layout. It asks for an email address and displays the field's errors. The submission form includes a CSRF token and a reset button. Admin widget and form styles are loaded with CSP nonce attributes.
    - Tags: [admin, auth, breadcrumbs, csp, css, form, i18n, reset, static, validation]

- `templatetags/admin_filters.py` (Size : 2501 bytes): Registers display-oriented admin filters. `to_object_display_value` delegates value formatting to the admin display utility, while `truncated_unordered_list` walks nested items and renders an escaped unordered list. The latter honors a maximum item count and uses plural-aware text for omitted items. Its output is marked safe after applying the selected escaping behavior.
    - Tags: [admin, html, template-tags, value-formatting]

- `templatetags/admin_list.py` (Size : 20385 bytes): Supplies the template tags and context builders for admin changelists. It prepares pagination and sortable column headers, renders result rows with field display, links, editable forms, and hidden fields, and builds date-hierarchy navigation. It also supplies search, filter, action, and object-tool contexts. Registered inclusion tags use `InclusionAdminNode` from `base.py` to render the associated admin templates.
    - Tags: [admin, change-list, date-hierarchy, filtering, pagination, search, template-tags]

- `templatetags/admin_modify.py` (Size : 5506 bytes): Supplies template tags and filters for admin change forms. It gathers prepopulated fields from the main form and new inline forms and serializes their metadata for JavaScript. Its submit-row context computes which save, delete, close, and related controls to show using permissions and form state. It also counts visible inline-form cells and registers change-form action and object-tool tags through the shared inclusion node.
    - Tags: [admin, change-form, inline-forms, template-tags]

- `templatetags/admin_urls.py` (Size : 2108 bytes): Registers filters for constructing admin URL names and quoting URL values. Its context-aware `add_preserved_filters` tag parses existing and preserved query parameters, resolves changelist URLs to handle nested changelist filters, and optionally adds popup and target-field parameters. It then merges the query parameters and reconstructs the URL. The module uses Django’s URL resolver and query-string utilities.
    - Tags: [admin, query-strings, template-tags, urls]

- `templatetags/base.py` (Size : 1939 bytes): Defines `InclusionAdminNode`, the shared inclusion node used by the admin tag modules. It inspects the supplied function signature and parses tag arguments, validating the context-first argument when context passing is enabled. On each render it selects a template from model-specific, app-specific, and general admin template locations. The template is selected at render time rather than stored on the node.
    - Tags: [admin, template-overrides, template-tags]

- `templatetags/log.py` (Size : 2097 bytes): Registers the `get_admin_log` tag for placing a limited set of admin log entries into a template context variable. The parser validates the limit and tag syntax, while `AdminLogNode` optionally filters entries by a literal user ID or a user object in the context. It slices the entries to the requested limit and returns no rendered text. The documentation explains both accepted user argument forms.
    - Tags: [admin, audit-log, template-tags]
    - TODO/FIXME/NOTE: NOTE (line 41; source marker: `Note`)

- `utils.py` (Size : 23925 bytes): Supplies shared admin utilities for field lookup, display formatting, nested object deletion, lookup parsing, model labels, and URL-safe object identifiers. These helpers are used by forms, filters, changelists, and model-admin operations. Tags: [fields, formatting, models, querysets]

- `views/autocomplete.py` (Size : 4508 bytes): Implements the admin autocomplete endpoint for AJAX requests from autocomplete widgets. It validates app, model, field, registered admin, search configuration, and the requested output field before checking view permission. It applies the related field's choice limit and `ModelAdmin` search behavior to a queryset, then returns serialized results with pagination state as JSON. The view delegates pagination, queryset construction, and permissions to the associated `ModelAdmin`.
    - Tags: [admin, ajax, autocomplete, django, json, permissions, search, views]

- `views/decorators.py` (Size : 658 bytes): Defines `staff_member_required`, a decorator for restricting views to active staff users. It builds on Django's `user_passes_test` and uses the admin login URL by default. Callers may supply a view function directly or use the returned decorator. The redirect field name and login URL can be customized.
    - Tags: [authentication, authorization, decorators, django, staff]

- `views/main.py` (Size : 23180 bytes): Implements the admin changelist form and `ChangeList`, which builds the result list presented for a model in the admin. It processes query parameters for filters, search, facets, popups, field selection, and ordering, validating lookups and translating invalid parameters into admin lookup errors. It combines list-filter querysets with model-admin search, applies related-object loading and deterministic ordering, and removes duplicates when needed. It also coordinates pagination and result counts and constructs URLs for result objects and filter state.
    - Tags: [admin, changelist, django, filtering, forms, pagination, search, sorting]
    - TODO/FIXME/NOTE: `Note` at line 305 — `# Note this isn't necessarily the same as result_count in the case of`

- `widgets.py` (Size : 21209 bytes): Implements admin form widgets for related-object selection, autocomplete, filtered selections, and date/time inputs. It adds the media and rendering behavior required by admin templates and JavaScript. Tags: [forms, javascript, templates, widgets]

- `__init__.py` (Size : 1327 bytes): Re-exports the admin site's registration, display, action, filter, and inline APIs. It defines `autodiscover()` to load application admin modules into the default site. The module is the package-level public interface. Tags: [api, django, imports]

## Links Child Folder docmaps
- `static/admin/css/docmap.md` — Admin page and widget styles, including themes, RTL adjustments, and responsive rules.
- `static/admin/img/docmap.md` — Admin SVG vectors and sprites with Font Awesome version and attribution information.
- `static/admin/js/docmap.md` — Browser-side admin interactions, widgets, navigation, and shared utilities.
- `templates/admin/docmap.md` — Indexes the primary Django admin page templates and reusable controls.

# Related Features

Model registration, model administration, changelists, forms and inlines, filters, built-in actions, admin authentication, and audit logging. Merged `migrations/`: Django admin action logging through the `LogEntry` model and its migration history. Merged `static/`: Django admin static assets. Merged `static/admin/`: Django admin static presentation and browser interactions. Merged `templates/`: Django admin page rendering and registration password-management presentation. Merged `templates/registration/`: The templates cover the admin logout, password change, and password-reset user flows, including email delivery content, confirmation-link validation presentation, and completion messages. Merged `templatetags/`: Admin changelist rendering and navigation, admin change-form controls, admin URL filter preservation, formatted admin values, and display of admin log entries. Merged `views/`: Admin autocomplete fields, staff-only access to admin views, and model changelist browsing, filtering, search, sorting, and pagination.

# Agent Guidance

## Read When

Changing model-admin behavior, admin registration, permissions, list filtering, admin forms, actions, or admin request handling. Merged `migrations/`: Investigating the schema or recorded fields for Django admin action-log entries, or tracing how their migration history evolves. Merged `static/`: Locating or changing static resources used by the Django admin. Merged `static/admin/`: Changing or locating static assets used by the Django admin interface. Merged `templates/`: Locating or changing templates for the Django admin site or its registration pages. Merged `templates/registration/`: Changing the admin-facing HTML or email content for logout, password change, or password reset. Merged `templatetags/`: Changing or tracing admin template tags and filters, changelist rendering data, change-form controls, preserved admin URLs, or admin-log template behavior. Merged `views/`: Working on admin autocomplete responses, access restrictions for admin views, or how admin changelists process filters, search terms, ordering, and result pages.

## Modify When

The change affects reusable admin behavior or a public admin extension point. Merged `migrations/`: Adding or changing a migration for the admin `LogEntry` schema. Merged `static/`: The requested change concerns this folder's organization. Merged `static/admin/`: The requested change concerns organization or navigation of the admin static asset areas. Merged `templates/`: The requested change concerns organization of the admin template areas. Merged `templates/registration/`: The requested change concerns page layout, translated copy, form presentation, breadcrumbs, or reset-email content in these workflows. Merged `templatetags/`: An admin template-facing tag/filter or its preparation of context, rendered values, or admin navigation parameters needs to change. Merged `views/`: Changing the behavior of autocomplete requests, the staff view-access decorator, or changelist query and result handling.

## Avoid Modifying When

The change is limited to a specific page's markup or browser behavior; inspect the corresponding child template or static-asset map first. Merged `migrations/`: Changing admin behavior unrelated to the action-log schema; those changes belong outside these schema migration files. Merged `static/`: Changing a specific asset; use the corresponding child folder or source asset. Merged `static/admin/`: Changing an individual stylesheet, image, or JavaScript behavior; use the corresponding child folder instead. Merged `templates/`: Changing a specific template; use the corresponding child folder or template file instead. Merged `templates/registration/`: Changing password validation, reset-token handling, authentication, or email delivery behavior without a template requirement. Merged `templatetags/`: The change concerns admin view behavior, model-admin configuration, or template markup itself without requiring changes to these tag and filter implementations. Merged `views/`: Changing admin registration or model-specific configuration that belongs in `ModelAdmin`, or changing shared ORM, form, authentication, or HTTP framework behavior. ---
