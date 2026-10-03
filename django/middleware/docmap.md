---
folder: "django/middleware"
generated_on: "2026-10-03"
num_files: 10
semantic_tags: [caching, csrf, django, http, middleware, python, security]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package contains request/response middleware for common HTTP concerns. Implementations cover caching, security headers and redirects, common URL handling, content security policy, CSRF protection, compression, conditional requests, and localization. The package initializer provides middleware construction helpers. These classes plug into Django's configured middleware chain.

## Major Responsibilities

Apply request/response transformations and policy checks around view processing, including security validation, caching, locale activation, and HTTP content negotiation.

## Technology Notes

Python middleware callables supporting synchronous and asynchronous request handling where implemented.

# Folder Navigation

## Merged Child Folders
None. All child folders remain standalone.

## Files
- `__init__.py` (Size : 2286 bytes): Provides middleware handler construction utilities that adapt configured middleware classes into the request/response chain.
    - Tags: [django, middleware, python]

- `cache.py` (Size : 9751 bytes): Implements update and fetch cache middleware, handling cache keys, response eligibility, conditional requests, and cache-control headers.
    - Tags: [caching, http, middleware, python]

- `clickjacking.py` (Size : 1794 bytes): Sets the `X-Frame-Options` response header according to Django's clickjacking protection settings.
    - Tags: [clickjacking, http, middleware, security]

- `common.py` (Size : 8404 bytes): Implements common request/response behaviors including URL normalization, allowed-host checks, and conditional content-length handling.
    - Tags: [http, middleware, redirects, url-normalization]
    - TODO/FIXME/NOTE: line 177 note

- `csp.py` (Size : 1334 bytes): Adds configured Content Security Policy headers to responses.
    - Tags: [content-security-policy, http, middleware, security]

- `csrf.py` (Size : 20027 bytes): Implements CSRF middleware checks and response cookie handling, coordinating token validation with Django's CSRF utilities.
    - Tags: [cookies, csrf, http, middleware, security]
    - TODO/FIXME/NOTE: line 99 NOTE

- `gzip.py` (Size : 2712 bytes): Compresses eligible response bodies with gzip and updates content-encoding and related headers.
    - Tags: [compression, gzip, http, middleware]

- `http.py` (Size : 1645 bytes): Implements conditional GET processing for ETag and last-modified headers, including not-modified responses.
    - Tags: [conditional-requests, etag, http, middleware]

- `locale.py` (Size : 3542 bytes): Determines and activates a request language from URL prefixes, cookies, or accepted-language headers, then manages language response metadata.
    - Tags: [internationalization, locale, middleware, requests]

- `security.py` (Size : 2687 bytes): Adds configured security headers and handles HTTPS redirection and related transport-security policy.
    - Tags: [https, http, middleware, security]

---

## Links Child Folder docmaps
None.

# Related Features

Request/response caching, security protections, localization, compression, and HTTP protocol behavior.

# Agent Guidance

## Read When

Tracing configured middleware behavior, response headers, request filtering, or middleware ordering effects.

## Modify When

Changing middleware behavior or introducing a cross-cutting request/response policy.

## Avoid Modifying When

Changing core request/response primitives or application-specific view logic.
