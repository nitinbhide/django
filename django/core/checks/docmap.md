---
folder: "django/core/checks"
generated_on: "2026-10-03"
num_files: 17
semantic_tags: [async, compatibility, configuration, csrf, deprecation, models, security, system-checks, urls]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django's system-check framework and built-in checks for application configuration. The checks cover models, databases, caches, files, mail, templates, translations, URLs, commands, and asynchronous settings. Security and version-compatibility checks are indexed in dedicated child maps. Use this hierarchy to locate a check by the subsystem it validates. Merged `compatibility/`: This folder contains compatibility checks for framework features affected by version transitions. Merged `security/`: This folder implements security-focused system checks.

## Major Responsibilities

The package registers checks, defines check message types, and validates settings and registered framework components. Check functions return structured warnings and errors for management commands and other check callers. Merged `compatibility/`: The modules register and implement compatibility-related system checks. They use Django's check message types to present actionable warnings or errors. Merged `security/`: The modules provide reusable security warning helpers and validate security-sensitive settings. Their results are integrated with Django's broader system-check registry.

## Technology Notes

Checks integrate with application/model metadata, settings, URLs, and Django's check registry. Merged `compatibility/`: The implementation uses Django's system-check registry and message classes. Merged `security/`: The code uses Django settings and the system-check message API.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `compatibility` : This folder contains compatibility checks for framework features affected by version transitions. The checks report deprecated or incompatible usage through Django's system-check framework. Its current compatibility module targets Django 4.0-era changes. Read the module before changing compatibility diagnostics. The modules register and implement compatibility-related system checks. They use Django's check message types to present actionable warnings or errors.
- `security` : This folder implements security-focused system checks. It includes shared security check utilities plus checks related to CSRF and session configuration. The checks inspect project settings and emit Django check messages. Consult the relevant check module when modifying these security diagnostics. The modules provide reusable security warning helpers and validate security-sensitive settings. Their results are integrated with Django's broader system-check registry.

## Files
- `async_checks.py` (Size : 419 bytes): Defines checks related to asynchronous-safety configuration. It reports configuration problems through Django's check-message system. The module is scoped to async-related checks. No markers are present.
    - Tags: [async, system-checks]

- `caches.py` (Size : 2719 bytes): Validates configured cache settings and backend options. It iterates cache aliases and emits messages for invalid or suspicious configuration. The checks help catch cache setup problems before runtime. No markers are present.
    - Tags: [cache, configuration, system-checks]

- `commands.py` (Size : 993 bytes): Implements checks associated with management commands and their configuration. It uses the shared registry/message mechanism to report command-related issues. The module is separate from command execution itself. No markers are present.
    - Tags: [commands, system-checks]

- `compatibility/django_4_0.py` (Size : 691 bytes): Defines compatibility checks for framework changes associated with Django 4.0. It reports affected configuration or API usage using standard check messages. The module is version-scoped and registered through the checks package. No markers are present.
    - Tags: [compatibility, django-4.0, system-checks]

- `database.py` (Size : 355 bytes): Provides checks for database configuration. It reports invalid database settings through the standard check interface. Database feature-specific behavior is left to database backends. No markers are present.
    - Tags: [database, system-checks]

- `files.py` (Size : 541 bytes): Validates file-related settings used by Django. It contributes check messages for invalid file configuration. Runtime file and storage operations are implemented elsewhere. No markers are present.
    - Tags: [file-storage, settings, system-checks]

- `mail.py` (Size : 2055 bytes): Checks email-related settings and backend configuration. It evaluates configured values and reports potential mail setup errors. The module does not send messages. No markers are present.
    - Tags: [email, settings, system-checks]

- `messages.py` (Size : 2337 bytes): Defines Django's system-check message classes and severity identifiers. These structured messages represent check errors, warnings, and informational results. Check implementations use them to return consistent diagnostics. No markers are present.
    - Tags: [diagnostics, messages, system-checks]

- `model_checks.py` (Size : 9047 bytes): Implements checks over registered models and model metadata. It validates relationships, fields, and other model declarations and reports issues through check messages. It is registered as part of Django's built-in checks. No markers are present.
    - Tags: [models, system-checks]

- `registry.py` (Size : 4026 bytes): Provides the registry that stores and runs system-check functions. It supports registration, deployment-tag filtering, and aggregation of messages from registered checks. The package check entry points use this registry. No markers are present.
    - Tags: [registry, system-checks]

- `security/base.py` (Size : 11912 bytes): Provides shared helpers and checks used to identify security-related configuration problems. It centralizes reusable warning behavior and setting validation. Other security check modules build on this functionality. No markers are present.
    - Tags: [security, settings, system-checks]

- `security/csrf.py` (Size : 2154 bytes): Checks CSRF-related settings and reports configuration that can weaken or break CSRF protection. It defines system-check messages based on configured values. The check is part of Django's security check suite. No markers are present.
    - Tags: [csrf, security, system-checks]

- `security/sessions.py` (Size : 2667 bytes): Checks session-related settings for security configuration issues. It reports conditions that affect the safety of session cookies or storage. The module integrates with Django's standard check-message and registration mechanisms. No markers are present.
    - Tags: [security, sessions, system-checks]

- `templates.py` (Size : 308 bytes): Defines checks for template configuration. It reports problems using the shared system-check mechanism. Template rendering behavior is implemented outside this file. No markers are present.
    - Tags: [system-checks, templates]

- `translation.py` (Size : 2056 bytes): Validates translation and locale-related configuration. It reports settings and configuration conditions that can affect localization. The module contributes checks to the system-check registry. No markers are present.
    - Tags: [localization, system-checks, translation]

- `urls.py` (Size : 5064 bytes): Implements checks over configured URL patterns and resolvers. It reports malformed or problematic routes using structured check messages. It operates on resolver metadata rather than serving requests. No markers are present.
    - Tags: [system-checks, urls]

- `__init__.py` (Size : 1346 bytes): Defines the public check API and coordinates registration of built-in checks. It imports the check registry and exposes the check entry points and message types. Specialized compatibility and security implementations live in child folders. No markers are present.
    - Tags: [api, registration, system-checks]

---

## Links Child Folder docmaps

None.

# Related Features

Startup and deployment diagnostics for Django configuration and registered components. Merged `compatibility/`: Compatibility diagnostics during Django's system checks. Merged `security/`: Security configuration diagnostics for CSRF and sessions.

# Agent Guidance

## Read When

Changing built-in system checks, their registration, or check message behavior. Merged `compatibility/`: Changing compatibility checks or version-transition warnings. Merged `security/`: Changing security system checks or their reported messages.

## Modify When

Adding a validation diagnostic for framework configuration or metadata. Merged `compatibility/`: Adding a compatibility check for an explicitly represented framework change. Merged `security/`: Adding or updating a security-related setting check.

## Avoid Modifying When

Changing runtime behavior of the subsystem checked by a module. Merged `compatibility/`: Changing general check registration or unrelated checks. Merged `security/`: Changing runtime CSRF or session handling outside check reporting.
