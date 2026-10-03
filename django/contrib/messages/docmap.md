---
folder: "django/contrib/messages"
generated_on: "2026-10-03"
num_files: 14
semantic_tags: [application-configuration, class-based-views, context-processors, cookies, django, fallback-storage, http-middleware, message-serialization, message-storage, messages, python, request-api, request-signing, session-storage, settings, templates, testing]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder implements the public request-based API and integration points for Django's messages framework. It exposes message-level helpers and constants, connects message storage to requests and responses, and makes messages available to templates. It also provides application configuration, message-tag customization, and a success-message mixin for form views. Storage backend implementations are maintained in the child `storage` folder. Merged `storage/`: This folder implements the storage backends used by Django's messages framework.

## Major Responsibilities

The modules define message creation and retrieval, level settings, context processing, middleware lifecycle handling, and success notifications after valid form submissions. The app configuration refreshes level tags when the `MESSAGE_TAGS` setting changes. Public package imports re-export the API, constants, and base `Message` type. Merged `storage/`: `BaseStorage` and `Message` define shared message behavior and the backend contract. `CookieStorage` serializes and signs cookie data, while `SessionStorage` persists serialized messages in the request session. `FallbackStorage` tries cookie storage first and passes messages that cannot be stored to session storage.

## Technology Notes

These Python modules integrate with Django application configuration, settings, request/response middleware, template context processing, signals, and class-based form views. Merged `storage/`: The files are Python modules for Django's messages framework. Storage uses Django settings, request cookies or sessions, JSON serialization, and Django signing for cookie integrity.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `storage` : This folder implements the storage backends used by Django's messages framework. It provides a common interface for queueing, loading, and persisting messages, along with cookie-based, session-based, and combined fallback implementations. The default backend is resolved from the `MESSAGE_STORAGE` setting when requested. The backends handle message serialization and the constraints of their respective persistence mechanisms. `BaseStorage` and `Message` define shared message behavior and the backend contract. `CookieStorage` serializes and signs cookie data, while `SessionStorage` persists serialized messages in the request session. `FallbackStorage` tries cookie storage first and passes messages that cannot be stored to session storage.

## Files
- `api.py` (Size : 3377 bytes): Implements the request-based API for adding and retrieving messages and reading or setting the minimum recording level. It provides convenience functions for the DEBUG, INFO, SUCCESS, WARNING, and ERROR levels, all of which delegate to `add_message()`. Requests lacking installed message middleware raise `MessageFailure` unless silent failure is requested, while non-request objects raise `TypeError`. The API obtains storage through the request's `_messages` attribute and Django's default storage factory.
    - Tags: [http, messages, python, request-api]

- `apps.py` (Size : 630 bytes): Defines the Django `MessagesConfig` application configuration and its human-readable name. On application readiness, it connects `update_level_tags()` to Django's `setting_changed` signal. When `MESSAGE_TAGS` changes, the handler replaces the base storage level-tag mapping with a lazy call to `get_level_tags()`. This keeps customized message tags synchronized with runtime setting changes.
    - Tags: [application-configuration, django, messages, settings, signals]

- `constants.py` (Size : 333 bytes): Defines the numeric values for the five built-in message levels, including SUCCESS between INFO and WARNING. It maps those values to default lowercase CSS-style tags in `DEFAULT_TAGS`. The `DEFAULT_LEVELS` mapping exposes the same values under uppercase names for template use. The module centralizes the level and tag constants used by the API and context processor.
    - Tags: [constants, message-levels, messages, python]

- `context_processors.py` (Size : 367 bytes): Defines the `messages()` context processor for Django templates. It returns the request's message storage through `get_messages()` and includes `DEFAULT_MESSAGE_LEVELS` from the constants module. The storage lookup remains lazy according to the message API. Templates can therefore iterate messages and use the named level constants.
    - Tags: [context-processors, django-templates, messages, request]

- `middleware.py` (Size : 1034 bytes): Implements synchronous `MessageMiddleware` request and response hooks. The request hook attaches an instance of the configured default storage to `request._messages`. The response hook asks that storage to update the response and, in DEBUG mode, raises `ValueError` if some messages could not be stored. It tolerates requests where an earlier middleware layer did not attach message storage.
    - Tags: [http-middleware, messages, request-response, storage]

- `storage/base.py` (Size : 6265 bytes): Defines `Message`, which prepares message content for serialization and exposes its string representation and level tags. `BaseStorage` queues new messages, lazily loads stored messages, and tracks whether queued or previously loaded messages should be persisted during update. Subclasses provide `_get()` and `_store()` to implement backend-specific retrieval and persistence. The base class also applies the configured recording level and normalizes lazy message values before storage.
    - Tags: [django-settings, message-queue, message-serialization, message-storage]

- `storage/cookie.py` (Size : 8929 bytes): Implements cookie-backed message storage and JSON encoder/decoder classes for `Message` values, including preservation of safe-string status. Cookie data is signed and compressed through Django's signing utilities, and invalid or tampered data is discarded. The backend limits cookie size and uses a completion sentinel plus binary-search helpers to identify messages that do not fit. Those unpersisted messages are returned to the caller for possible storage elsewhere.
    - Tags: [cookies, django-signing, json, message-serialization, message-storage]

- `storage/fallback.py` (Size : 2149 bytes): Implements a composite backend that tries cookie storage before session storage. Retrieval gathers messages across the backends until all messages are found or an unused backend indicates retrieval can stop. Persistence passes messages not stored by one backend to the next. It tracks backends that supplied messages so they can be flushed on a later update.
    - Tags: [cookie-storage, fallback-storage, message-storage, session-storage]

- `storage/session.py` (Size : 1816 bytes): Implements session-backed message storage using the `_messages` session key. Initialization requires request session middleware and raises `ImproperlyConfigured` when the request has no session. Stored messages are encoded and decoded with the message encoder and decoder from `cookie.py`. An empty message list removes the session key.
    - Tags: [django-sessions, json, message-serialization, message-storage, session-storage]

- `storage/__init__.py` (Size : 404 bytes): Resolves the configured message storage backend when the framework requests a storage instance. It reads `MESSAGE_STORAGE` at call time rather than importing the configured backend at module load. The resulting callable provides the same request-based interface as storage classes. This keeps backend selection tied to runtime settings.
    - Tags: [django, messages, settings, storage-backend]

- `test.py` (Size : 432 bytes): Provides `MessagesTestMixin` for asserting messages attached to a response's WSGI request. Its assertion method supports ordered equality or order-independent count equality. It materializes the request storage before comparison. The module marks itself with `__unittest = True` so unittest excludes its frames from failure reports.
    - Tags: [messages, testing, unittest]

- `utils.py` (Size : 268 bytes): Implements `get_level_tags()` to produce the mapping from message levels to display tags. It begins with `DEFAULT_TAGS` and overlays any `MESSAGE_TAGS` configured in Django settings. The returned dictionary lets custom settings replace or extend defaults. The app configuration uses this function when message-tag settings change.
    - Tags: [configuration, message-tags, messages, settings]

- `views.py` (Size : 543 bytes): Defines `SuccessMessageMixin` for form views that should emit a success message after valid submission. Its `form_valid()` method first delegates to the parent implementation, then formats the configured `success_message` with cleaned form data. It adds a message only when the formatted result is nonempty. `get_success_message()` provides the formatting hook.
    - Tags: [class-based-views, forms, messages, success-notifications]

- `__init__.py` (Size : 174 bytes): Re-exports the messages API and level constants from their defining modules. It also exposes the storage `Message` class as part of the package-level interface. Wildcard imports marked `NOQA` keep the selected public names available to callers. This module contains no independent message-processing logic.
    - Tags: [messages, python, re-exports, storage]

---

## Links Child Folder docmaps

None.

# Related Features

Django's user-facing messages framework: request-level message APIs, level tags, template access, middleware integration, success notifications for form views, and configurable storage backends. Merged `storage/`: Django's contrib messages feature, including configurable message backends, cookie persistence, session persistence, and fallback storage.

# Agent Guidance

## Read When

Changing message APIs, message levels or tags, template access, request/response integration, or success notifications for form submissions. Merged `storage/`: Changing message lifecycle behavior, configuring or implementing a storage backend, or investigating how messages are serialized and persisted.

## Modify When

The change affects public message helpers, message middleware, application configuration, context processing, message-related utilities, or form-view success messages. Merged `storage/`: The change concerns shared message-storage behavior or cookie, session, or fallback backend implementation.

## Avoid Modifying When

The change is limited to serialization or persistence behavior in a storage backend; inspect and modify `storage/` instead. Merged `storage/`: The change concerns message presentation, middleware integration, or public message APIs without changing backend storage behavior.

## Dependency Graph

Not generated.
