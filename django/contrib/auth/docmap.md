---
folder: "django/contrib/auth"
generated_on: "2026-10-03"
num_files: 27
semantic_tags: [authentication, authorization, django, django-template, email, forms, groups, html, i18n, management, management-commands, middleware, migrations, mod_wsgi, password, password-hashing, password-reset, passwords, permissions, subject, superuser, template, template-tags, templates, translations, usernames, users, widget, widgets]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package implements Django's authentication and authorization APIs, including user and group models, backend authentication, password management, and permission checks. It integrates credentials and user state with sessions, request middleware, forms, views, and signals. Its extension points support custom user models and authentication backends. Management commands, migrations, templates, handlers, and template tags are indexed in child maps. Merged `handlers/`: This folder provides Django authentication integration for mod_wsgi. Merged `management/`: This folder contains Django authentication management support for permission provisioning and username defaults. Merged `templates/`: This folder organizes authentication-related Django templates. Merged `templatetags/`: This folder provides template tags related to Django authentication.

## Major Responsibilities

The package authenticates sync and async requests, exposes user and permission APIs, stores password hashes, validates password and username values, and provides login/logout and password-reset views. It defines reusable decorators and class-based-view mixins for authentication and permission requirements. App checks and post-migration hooks maintain configured user models and permissions. Merged `handlers/`: The module resolves active users, verifies passwords using Django's timing-attack-mitigated authentication check, and returns group names in the byte-string form expected by its caller. It resets query state before database work and closes old connections afterward. Merged `management/`: Creates missing default and model-defined permissions using content types and the selected database. Reconciles permission codenames and display names after model renames, reporting conflicts and applying successful changes atomically. Derives a candidate default username, validates it against the active user model, and avoids returning an existing username. Merged `management/commands/`: Implements command-line workflows for changing a user's password and creating a superuser. The commands gather and validate input, then persist the resulting user changes through Django's authentication and ORM facilities. Merged `templates/`: Provide a navigation point for authentication template resources. Merged `templates/auth/`: Organize authentication-specific interface templates, including the password hash display widget in the child `widgets` folder. Merged `templates/auth/widgets/`: Render the read-only password display and password-change action in the auth widget. Merged `templates/registration/`: Provides the translated subject line used by the password-reset email template. Merged `templatetags/`: The folder registers a simple template tag that presents safe password-hash summaries. It handles missing, unusable, and unrecognized password values with explicit messages. Hash summary values are rendered with Django's HTML-formatting helpers.

## Technology Notes

The implementation uses Django ORM models, forms, signals, middleware, sessions, URL routing, class-based views, asynchronous adapters, and configurable import paths. Merged `handlers/`: Python, Django's authentication and database APIs, and the mod_wsgi authentication interface. Merged `management/`: The module uses Python and Django's app registry, authentication and content-types models, migration operations, database routers, transactions, and model validators. Merged `management/commands/`: The modules use Python and Django's management-command and authentication APIs, including password validators and user-model operations. Merged `templates/`: Django form widget templates. Merged `templates/auth/`: Django template syntax and the `auth` template tag library are used by the child widget template. Merged `templates/auth/widgets/`: Django template tags and authentication form widget rendering. Merged `templates/registration/`: The file uses Django template internationalization and autoescape tags. Merged `templatetags/`: The module uses Django template tags, the authentication hasher API, HTML formatting utilities, and translation functions.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `handlers` : This folder provides Django authentication integration for mod_wsgi. Its module exposes functions for checking a user's password and retrieving the names of the user's groups. Both functions use Django's configured user model and database connection management. The folder contains one Python source file and no child folders. The module resolves active users, verifies passwords using Django's timing-attack-mitigated authentication check, and returns group names in the byte-string form expected by its caller. It resets query state before database work and closes old connections afterward.
- `management/commands` : This folder contains Django authentication management command modules. The commands provide interactive password changes and superuser creation with interactive and non-interactive input modes. They integrate with Django's user model, password validation, and management-command framework. The package initializer is empty and contributes no additional code. Implements command-line workflows for changing a user's password and creating a superuser. The commands gather and validate input, then persist the resulting user changes through Django's authentication and ORM facilities.
- `management` : This folder contains Django authentication management support for permission provisioning and username defaults. Its package module creates model permissions during application migration and updates permission records when a model is renamed. It also provides a normalized operating-system username suggestion when that value is valid and available for the configured user model. The `commands` child package contains the authentication command-line workflows. Merged `commands/`: This folder contains Django authentication management command modules. Creates missing default and model-defined permissions using content types and the selected database. Reconciles permission codenames and display names after model renames, reporting conflicts and applying successful changes atomically. Derives a candidate default username, validates it against the active user model, and avoids returning an existing username. Merged `commands/`: Implements command-line workflows for changing a user's password and creating a superuser. The commands gather and validate input, then persist the resulting user changes through Django's authentication and ORM facilities.
- `templates/auth/widgets` : This directory contains a read-only password hash widget template. It has one retained entry, `read_only_password_hash.html`. The template renders a password value as a hash and provides a password-change link. No other files or folders are included in this index. Render the read-only password display and password-change action in the auth widget.
- `templates/auth` : This directory groups templates used by Django's authentication interface. Its discovered child folder, `widgets`, contains the read-only password hash widget template. That widget renders a password hash and a password-change action. No eligible files are directly in this directory. Merged `widgets/`: This directory contains a read-only password hash widget template. Organize authentication-specific interface templates, including the password hash display widget in the child `widgets` folder. Merged `widgets/`: Render the read-only password display and password-change action in the auth widget.
- `templates/registration` : This folder contains a Django email subject template for password reset messages. The template uses Django's translation tags to render a localized subject. It inserts the site name from template context and disables autoescaping for the subject text. No additional files or behavior are present in the folder. Provides the translated subject line used by the password-reset email template.
- `templates` : This folder organizes authentication-related Django templates. Its `auth` child indexes widget templates used by Django authentication forms. The child map provides the detailed template entry and links to its widget-level contents. No eligible files are listed directly in this folder. Merged `auth/`: This directory groups templates used by Django's authentication interface. Merged `registration/`: This folder contains a Django email subject template for password reset messages. Provide a navigation point for authentication template resources. Merged `auth/`: Organize authentication-specific interface templates, including the password hash display widget in the child `widgets` folder. Merged `auth/widgets/`: Render the read-only password display and password-change action in the auth widget. Merged `registration/`: Provides the translated subject line used by the password-reset email template.
- `templatetags` : This folder provides template tags related to Django authentication. Its listed module formats password-hash details for display in HTML. The output distinguishes unset or unusable passwords from hashes that can be summarized and from invalid formats. User-facing messages and summary labels are translated. The folder registers a simple template tag that presents safe password-hash summaries. It handles missing, unusable, and unrecognized password values with explicit messages. Hash summary values are rendered with Django's HTML-formatting helpers.

## Files
- `admin.py` (Size : 10414 bytes): Registers the built-in `User` and `Group` models with the admin site. It configures their forms and list displays and supplies admin-specific password and user-management views. Tags: [admin, groups, users, views]

- `apps.py` (Size : 1527 bytes): Defines the authentication app configuration and connects post-migration permission handlers, model checks, and the last-login signal receiver. Tags: [app-config, permissions, signals]

- `backends.py` (Size : 13352 bytes): Defines the authentication backend protocol and the default model backend. It supports sync and async credential checks, user lookup, permission retrieval, and permission evaluation. Tags: [authentication, async, backends, permissions]

- `base_user.py` (Size : 5057 bytes): Implements the abstract user model and manager used to build custom user models. It normalizes email addresses, stores password and last-login state, and provides username, password, and authentication methods. Tags: [models, passwords, users]

- `checks.py` (Size : 10041 bytes): Implements system checks for the configured user model, middleware, and permission model configuration. It reports invalid auth settings through Django's check framework. Tags: [configuration, checks, models, permissions]

- `common-passwords.txt.gz` (Size : 80228 bytes): Compressed common-password data used by the common-password validator. The compressed payload is not summarized from decoded contents. Tags: [compressed-data, password-validation, vocabulary]

- `context_processors.py` (Size : 1978 bytes): Adds the current user and a template-friendly permissions proxy to template context. The proxy delegates app and permission lookups to the user object. Tags: [context-processors, permissions, templates]

- `decorators.py` (Size : 4973 bytes): Provides function decorators for login requirements, permission checks, and custom user tests. The wrappers handle both sync and async views and preserve redirect metadata used by middleware. Tags: [authentication, decorators, permissions, views]

- `forms.py` (Size : 21399 bytes): Implements authentication, user creation/change, password change, and password reset forms. It normalizes usernames, validates passwords, and sends reset messages using token and site utilities. Tags: [authentication, forms, passwords, users]
    - TODO/FIXME/NOTE: line 237: TODO: Drop ImportError and KeyError when dropping support for PY312.

- `handlers/modwsgi.py` (Size : 1692 bytes): Provides mod_wsgi authentication and group-authorization helpers backed by Django's configured user model. `_get_user()` returns only existing active users, while `check_password()` uses Django's timing-attack-mitigated password check and returns its authentication result. `groups_for_user()` returns the active user's group names as encoded bytes, or an empty list when the user is missing or inactive. Both public helpers reset query state and close old database connections around their work.
    - Tags: [authentication, authorization, database, django, groups, mod_wsgi]
    - TODO/FIXME/NOTE: none

- `hashers.py` (Size : 24372 bytes): Implements password encoding, verification, hasher selection, and hash upgrades. The APIs include async wrappers and timing-mitigation behavior for invalid or missing password hashes. Tags: [cryptography, hashing, passwords]

- `management/commands/changepassword.py` (Size : 2768 bytes): This module implements a Django management command for changing a user's password. It obtains the target user from a username argument or the current operating-system user and prompts for password input. It checks password confirmation and validators for up to three attempts before saving the new password. The command uses Django's authentication system and database routing.
    - Tags: [auth, basecommand, command, database, getpass, management, password, user-lookup, validation]

- `management/commands/createsuperuser.py` (Size : 14061 bytes): This module implements the Django command for creating a superuser. It supports interactive prompts and non-interactive input through environment variables, and validates required fields and password confirmation. It can create a user through the ORM and includes input, output, TTY-detection, and username-uniqueness helpers. Password validation can be bypassed when the command's supported option requests it.
    - Tags: [auth, basecommand, command, environment-variables, getpass, interactive, management, password-validation, superuser, user-creation]

- `management/__init__.py` (Size : 9517 bytes): Provides post-migration authentication management by creating permissions for installed app models and reconciling permission records after model renames. It derives default permission codenames from model metadata, obtains content types, checks existing permissions on the configured database, and bulk-creates missing records. Rename handling collects migration `RenameModel` operations, detects codename conflicts, and updates permission names and codenames atomically. It also suggests a default username from the operating-system account after normalization and user-model validation, returning an empty string when the candidate is invalid or already in use.
    - Tags: [authentication, content-types, django, migrations, permissions, user-model, usernames]
    - TODO/FIXME/NOTE: line 237: TODO

- `middleware.py` (Size : 12140 bytes): Attaches lazy sync and async user accessors to requests and implements login-required and remote-user middleware. It resolves users from sessions or server-provided credentials and redirects unauthenticated requests when configured. Tags: [authentication, middleware, requests, sessions]

- `mixins.py` (Size : 4796 bytes): Defines class-based-view mixins for login, permission, and user-test requirements. Shared access logic selects a login URL, redirects unauthenticated requests, or raises permission-denied errors. Tags: [class-based-views, mixins, permissions]

- `models.py` (Size : 22118 bytes): Defines permissions, groups, the default user model, and managers for natural-key lookup. It implements permission assignment and group relationships and includes the login signal receiver that updates last-login state. Tags: [groups, models, permissions, users]

- `password_validation.py` (Size : 10226 bytes): Loads configured password validators and coordinates validation, change notifications, and help-text rendering. The module also implements built-in similarity, length, common-password, and numeric-password checks. Tags: [configuration, passwords, validation]

- `signals.py` (Size : 123 bytes): Declares the login, login-failure, and logout signals sent by authentication flows. Tags: [authentication, signals]

- `templates/auth/widgets/read_only_password_hash.html` (Size: 234 bytes): Loads the `auth` library and includes the widget attributes template on a `div`. It renders `widget.value` through `render_password_as_hash`. It outputs a button link using `password_url`, defaulting to `../password/`, and `button_label`. The file is a read-only password hash display with a password-change link.
  - Tags: [authentication, password, template, widget]

- `templates/registration/password_reset_subject.txt` (Size : 134 bytes): This template produces the subject text for a password-reset email. It uses a translated block and inserts the site name from the rendering context. Autoescaping is disabled around the subject content. No message body or email-delivery behavior is defined here.
    - Tags: [autoescape, django-template, email, i18n, password-reset, subject]

- `templatetags/auth.py` (Size : 961 bytes): Registers the `render_password_as_hash` simple template tag, which renders a translated message for missing or unusable passwords and for invalid or unknown hash formats. For recognized hashes, it obtains the hasher's safe summary and translates each summary key. It formats the result as HTML using Django's escaping-aware formatting helpers and wraps values in bidirectional isolation markup. The module depends on Django's template, authentication-hasher, HTML, and translation APIs.
    - Tags: [authentication, django-template, html, password-hashing, template-tags, translations]
    - TODO/FIXME/NOTE: none found

- `tokens.py` (Size : 4460 bytes): Generates and validates time-limited password-reset tokens using user state and secret-key-based HMACs. It supports secret-key fallbacks during token verification. Tags: [cryptography, passwords, tokens]

- `urls.py` (Size : 1221 bytes): Maps named URL patterns to built-in login, logout, password-change, and password-reset views. The module notes that the patterns are also provided as a deployment convenience outside `AdminSite`. Tags: [authentication, routing, urls, views]

- `validators.py` (Size : 747 bytes): Defines ASCII and Unicode regular-expression validators for usernames. Both are deconstructible for use in model fields and migrations. Tags: [validation, usernames]

- `views.py` (Size : 14249 bytes): Implements login, logout, password-change, and password-reset class-based views and redirect helpers. The views apply CSRF, cache, and sensitive-parameter decorators and use safe redirect validation. Tags: [authentication, passwords, redirects, views]

- `__init__.py` (Size : 15103 bytes): Exposes authentication APIs for loading backends, authenticating users, logging users in and out, and retrieving the active user model. It coordinates sync and async authentication, user session state, permission checks, and auth signals. Tags: [api, authentication, async, sessions]

## Links Child Folder docmaps
- `migrations/docmap.md` — Authentication schema and permission migrations.

# Related Features

User authentication, authorization and permissions, custom user models, password hashing and validation, login and logout, password reset, and admin user/group management. Merged `handlers/`: Django user authentication and authorization based on user-group membership through mod_wsgi. Merged `management/`: Permission creation for installed applications, permission updates after model renames, and default username suggestions for authentication users. Merged `management/commands/`: The command modules support authentication user administration through password changes and superuser creation. Merged `templates/`: Django authentication form presentation. Merged `templates/auth/`: Read-only password hash display and password changes in authentication forms. Merged `templates/auth/widgets/`: Read-only password display and password changes in authentication forms. Merged `templates/registration/`: Password-reset email subject rendering. Merged `templatetags/`: Displaying a safe, localized summary of a user password hash in a template.

# Agent Guidance

## Read When

Changing identity models, authentication backends, session user state, permission checks, password handling, or login-related request behavior. Merged `handlers/`: Working on authentication or group authorization provided to mod_wsgi, or on the database connection handling used by those helpers. Merged `management/`: Changing permission creation or migration behavior, model-rename permission updates, or default username suggestions. Merged `management/commands/`: Changing Django's command-line workflows for user password changes or superuser creation. Merged `templates/`: Locating or changing templates used by Django authentication forms. Merged `templates/auth/`: Changing authentication interface templates or locating the password hash widget. Merged `templates/auth/widgets/`: Changing the password hash widget or its change-password link. Merged `templates/registration/`: Changing the translated subject line of password-reset emails. Merged `templatetags/`: Working on authentication-related template tags or the HTML display of password-hash metadata.

## Modify When

The behavior is shared across authentication flows or is part of a public auth API. Merged `handlers/`: The mod_wsgi authentication contract or Django user/group behavior needs to change. Merged `management/`: A change concerns post-migration permission handling, permission metadata or database routing, rename conflict handling, or default username normalization and validation. Merged `management/commands/`: The requested behavior concerns command arguments, prompts, input validation, password handling, or superuser creation. Merged `templates/`: The requested change concerns the organization of authentication templates. Merged `templates/auth/`: A requested change concerns authentication template organization or the rendered authentication interface. Merged `templates/auth/widgets/`: The requested change concerns this widget's displayed value or action. Merged `templates/registration/`: The requested change concerns the subject text or template rendering for password-reset messages. Merged `templatetags/`: Changing how password hashes are summarized, how exceptional password values are presented, or how their output is localized and formatted.

## Avoid Modifying When

The change is limited to one management command, migration, template, or template tag; consult the corresponding child map first. Merged `handlers/`: Changing authentication behavior used only by other interfaces; this folder's functions specifically provide the mod_wsgi integration. Merged `management/`: Changing password-change or superuser command workflows; those implementations are in the `commands` child package. Merged `management/commands/`: Changing unrelated authentication views or user-management presentation; these files implement command-line workflows. Merged `templates/`: Changing an individual widget template or authentication form implementation. Merged `templates/auth/`: Changing authentication policy, password hashing, or form behavior that is implemented outside these templates. Merged `templates/auth/widgets/`: Changing password hashing or authentication policy logic. Merged `templates/registration/`: Changing password-reset token handling, message-body content, or email delivery behavior without a subject-template requirement. Merged `templatetags/`: Changing password verification, password storage, or hasher implementations; this folder only renders hash summaries.
