---
folder: "django/contrib/sessions"
generated_on: "2026-10-03"
num_files: 14
semantic_tags: [app-config, async, cache, cookies, database, django, filesystem, http, management-commands, middleware, migration, orm, serialization, sessions, signing, storage]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package integrates Django's session framework with application configuration, request and response processing, model persistence, and serialization. `SessionMiddleware` loads the configured backend and attaches cookie-based session state to each request. The model modules define the session record and its abstract persistence helpers, while exceptions represent invalid, suspicious, or interrupted sessions. Backend implementations, management commands, and migration details are indexed in the corresponding child-folder maps. Merged `backends/`: This folder implements the storage backends used by Django sessions. Merged `management/`: This folder organizes management commands for Django's session framework. Merged `migrations/`: This folder contains the initial database migration for Django’s sessions application.

## Major Responsibilities

Registers the sessions application and provides the database session model, session manager, and shared model behavior. Connects configured session stores to the HTTP request/response lifecycle, including cookie creation and removal, response variation, and save error handling. Exposes the JSON serializer used by session data and defines session-specific exceptions. Merged `backends/`: `base.py` defines common session behavior, key handling, expiry management, serialization, and the interface implemented by storage backends. The other modules implement backend-specific loading, saving, existence checks, deletion, and expired-session cleanup. The cached database backend combines cache reads with database persistence, while the signed-cookie backend stores signed session data in the client cookie. The filesystem backend writes session data to files and replaces them atomically. Merged `management/`: Provide navigation to session management commands. Merged `management/commands/`: Provides the command-line entry point for removing expired sessions from the configured session storage. Merged `migrations/`: Defines the initial `Session` model database table and its fields, table metadata, and manager.

## Technology Notes

Uses Django's application configuration, ORM, signing serializer, middleware, settings, and HTTP cookie APIs. Merged `backends/`: The implementations use Django settings, signing, cache APIs, the ORM, and filesystem operations. Synchronous APIs are paired with asynchronous variants, with `sync_to_async` used where required for synchronous database transactions. Merged `management/`: The child folder uses Django's management-command framework and configured session engines. Merged `management/commands/`: The command uses Django's management-command framework and dynamically loads the configured session engine. Merged `migrations/`: Uses Django’s migration operations and ORM model fields to describe a database schema change.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `backends` : This folder implements the storage backends used by Django sessions. Its modules provide a shared session interface and several ways to persist or transport session data. The backends include cache, database, cached database, filesystem, and signed-cookie implementations. Each backend exposes synchronous and asynchronous operations where supported. `base.py` defines common session behavior, key handling, expiry management, serialization, and the interface implemented by storage backends. The other modules implement backend-specific loading, saving, existence checks, deletion, and expired-session cleanup. The cached database backend combines cache reads with database persistence, while the signed-cookie backend stores signed session data in the client cookie. The filesystem backend writes session data to files and replaces them atomically.
- `management/commands` : This folder contains the Django sessions management-command package. Its command clears expired sessions by invoking the configured session backend. The command reports an error when the backend does not support expiration cleanup. The package initializer is empty. Provides the command-line entry point for removing expired sessions from the configured session storage.
- `management` : This folder organizes management commands for Django's session framework. Its `commands` child indexes the `clearsessions` command, which removes expired sessions through the configured session backend. No eligible files are listed directly in this folder. Merged `commands/`: This folder contains the Django sessions management-command package. Provide navigation to session management commands. Merged `commands/`: Provides the command-line entry point for removing expired sessions from the configured session storage.
- `migrations` : This folder contains the initial database migration for Django’s sessions application. It defines the schema used to persist session keys, serialized session data, and expiration timestamps in the `django_session` table. The migration also configures the `Session` model manager and an index on expiration dates. The folder contains one migration file and no child folders. Defines the initial `Session` model database table and its fields, table metadata, and manager.

## Files
- `apps.py` (Size : 201 bytes): Registers the sessions application with Django's application registry and sets its translated display name. The configuration identifies the app by its dotted package path. It contains no runtime session logic. The app configuration is used when Django loads the sessions application.
    - Tags: [app-config, django, sessions]

- `backends/base.py` (Size : 17568 bytes): Defines `SessionBase`, shared session exceptions, and the common contract for session backends. It provides dict-like accessors, signed serialization and decoding, key generation and validation, and sync/async expiry operations. It also defines abstract persistence methods that concrete backends implement. Session values are lazily loaded and cached on the session instance.
    - Tags: [async, django, serialization, sessions, signing, storage]

- `backends/cache.py` (Size : 4819 bytes): Implements sessions stored entirely in Django's cache. It handles cache-key construction, collision-resistant session creation, expiry-aware saves, reads, existence checks, and deletion. Synchronous operations have asynchronous counterparts. Expired-session cleanup is a no-op because cache expiration is delegated to the cache backend.
    - Tags: [async, cache, django, sessions, storage]

- `backends/cached_db.py` (Size : 4527 bytes): Extends the database session backend with a cache layer. It reads session data from cache first, loads and caches database data on a miss, and updates or removes cache entries alongside database operations. It includes synchronous and asynchronous methods and logs cache write or deletion failures. Cache read failures are treated as misses so the database can be consulted.
    - Tags: [async, cache, database, django, sessions, storage]

- `backends/db.py` (Size : 7105 bytes): Implements database-backed sessions through the configured session model. It loads unexpired records, creates and updates records transactionally, and translates database errors into session-specific exceptions. It provides asynchronous ORM operations and wraps the synchronous transaction block for async saves. Expired records are removed by the cleanup methods.
    - Tags: [async, database, django, orm, sessions, storage]

- `backends/file.py` (Size : 8414 bytes): Implements session persistence in files under a configured storage directory. It validates session keys before deriving paths, decodes stored data, applies expiry handling, and removes expired files. Saves use a temporary file and move operation to make completed session data visible without locking the session file. Async methods delegate to the synchronous filesystem operations.
    - Tags: [async, django, filesystem, sessions, storage]
    - TODO/FIXME/NOTE: line 153: Note

- `backends/signed_cookies.py` (Size : 3321 bytes): Implements sessions whose serialized data is carried in a signed client cookie rather than an external store. It verifies and decodes the signed value on load, resets invalid session data, and marks sessions modified when creating or saving cookie content. The backend reports that stored keys do not exist in shared storage and has no expired-session cleanup work. Sync methods are exposed through asynchronous wrappers.
    - Tags: [async, cookies, django, serialization, sessions, signing]

- `base_session.py` (Size : 1539 bytes): Defines the abstract model and manager shared by database-backed session records. The manager obtains the configured session store to encode dictionaries, then saves populated sessions or deletes empty ones. The model declares the session key, encoded data, and expiration fields. Its decode helper delegates data decoding to the session store class.
    - Tags: [database, django, model, serialization, sessions]

- `exceptions.py` (Size : 378 bytes): Defines session-specific exception types derived from Django's `SuspiciousOperation` and `BadRequest` exceptions. `InvalidSessionKey` represents invalid characters in a session key, and `SuspiciousSession` represents potentially tampered session data. `SessionInterrupted` signals an interrupted session operation. These types let session code report failures through Django's request-handling exception hierarchy.
    - Tags: [django, exceptions, sessions]

- `management/commands/clearsessions.py` (Size : 682 bytes): This module defines Django's `clearsessions` management command. It loads the configured session engine and calls its `clear_expired()` method. A `CommandError` is raised when the backend does not implement expiration cleanup. The command can be run manually or scheduled for periodic cleanup.
    - Tags: [backend-abstraction, command, django-management, exception-handling, sessions]

- `middleware.py` (Size : 3859 bytes): Implements `SessionMiddleware`, loading the session backend named by `SESSION_ENGINE` and binding a cookie-selected session store to each request. During response processing it removes cookies for emptied sessions or saves changed sessions and refreshes their cookies. It skips session saves for server-error responses and raises `SessionInterrupted` if an update fails because the session was deleted concurrently. When session state was accessed or a cookie is set, it adds `Cookie` to the response's `Vary` header.
    - Tags: [cookies, django, http, middleware, sessions]

- `migrations/0001_initial.py` (Size : 1185 bytes): Defines the initial `Session` model schema for the sessions application. It creates the `django_session` table with a primary-key session key, session data, and an indexed expiration date, and specifies the `SessionManager`. The migration has no dependencies.
    - Tags: [database, django, migration, sessions]

- `models.py` (Size : 1285 bytes): Defines the concrete `Session` model using `AbstractBaseSession` and a manager enabled for migrations. Its documentation describes the framework's server-side session data and cookie-carried session identifiers. The model selects the database backend's `SessionStore` for encoding and decoding session data. Its metadata maps records to the `django_session` table.
    - Tags: [database, django, orm, sessions]

- `serializers.py` (Size : 109 bytes): Re-exports Django signing's `JSONSerializer` under the sessions package's serializer module. This keeps the session serializer available through a sessions-specific import path. Serialization implementation is provided by the signing module. The file defines no additional serializer behavior.
    - Tags: [django, json, serialization, sessions]

---

## Links Child Folder docmaps

None.

# Related Features

Session storage and lifecycle handling, including request/response cookie management, database model persistence, and session serialization. Merged `backends/`: Session storage and lifecycle management across Django's cache, database, filesystem, and signed-cookie backends. Merged `management/`: Django session lifecycle management. Merged `management/commands/`: Removal of expired sessions through the configured session backend. Merged `migrations/`: Session persistence, including stored session data and its expiration timestamp.

# Agent Guidance

## Read When

Investigating the sessions app registration, shared session model, session-specific errors, serializer import, or middleware behavior that binds sessions to requests and responses. Merged `backends/`: Read these modules when investigating session data loading, saving, key lifecycle, expiration, or differences between Django's available session storage backends. Merged `management/`: Locating or changing management commands for sessions. Merged `management/commands/`: Changing the expired-session cleanup management command. Merged `migrations/`: Inspecting the initial database schema for sessions or tracing how persisted session records are structured.

## Modify When

Changing how Django configures the sessions app, manages the database session model, serializes session data, reports session errors, or integrates sessions with HTTP requests and responses. Merged `backends/`: Modify the relevant backend when changing its persistence behavior or sync/async session operations. Update `base.py` when changing behavior or contracts shared by all session backends. Merged `management/`: The requested change concerns organization of the sessions command area. Merged `management/commands/`: The requested change concerns command behavior, configured backend dispatch, or unsupported cleanup reporting. Merged `migrations/`: Changing the sessions database schema and updating or reviewing its initial migration history.

## Avoid Modifying When

Changing the persistence behavior of a specific storage backend, management command, or database migration; consult the corresponding child-folder docmap instead. Merged `backends/`: Avoid changing backend-specific modules for behavior that belongs to a single unrelated storage implementation. Changes to session model schema or higher-level middleware may belong outside this folder. Merged `management/`: Changing the implementation of the `clearsessions` command or session backends. Merged `management/commands/`: Changing session storage or expiration semantics implemented by a backend without a command-level requirement. Merged `migrations/`: Changing session runtime behavior that does not require a database schema change.

## Dependency Graph

Not generated; `dependencies` is empty and no dependency relationships were inferred.
