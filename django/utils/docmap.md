---
folder: "django/utils"
generated_on: "2026-10-03"
num_files: 47
semantic_tags: [caching, dates, django, encoding, gettext, http, internationalization, localization, python, translation, utilities]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This package contains reusable utilities shared across Django's framework components. The modules cover data structures, dates and timezones, encoding and HTML safety, HTTP and URL handling, cryptographic helpers, logging, decorators, and compatibility support. The translation subpackage provides locale-specific translation behavior. These helpers support many Django subsystems without owning application-level features. Merged `translation/`: This package implements Django's translation API and its locale-specific machinery.

## Major Responsibilities

Provide shared low-level operations for data representation, text and URL processing, time handling, module loading, caching, deprecation, and framework integration. Merged `translation/`: Activate languages, resolve translated strings and plural forms, load translation catalogs, provide no-op translation behavior, and connect translations to templates and autoreload.

## Technology Notes

Python standard-library integrations for dates, regular expressions, cryptography primitives, logging, and asynchronous execution. Merged `translation/`: Python `gettext` catalog integration with locale and thread/context-local language state.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `translation` : This package implements Django's translation API and its locale-specific machinery. It exposes translation functions, supports null and active translation modes, and loads compiled message catalogs. Template helpers integrate language-aware behavior with Django's template system, while the reloader watches translation resources during development. Together these modules provide runtime internationalization. Activate languages, resolve translated strings and plural forms, load translation catalogs, provide no-op translation behavior, and connect translations to templates and autoreload.

## Files
- `archive.py` (Size : 8563 bytes): Implements archive extraction and compression helpers for supported archive formats.
    - Tags: [archives, filesystem, python, utilities]

- `asyncio.py` (Size : 1827 bytes): Provides helpers for adapting synchronous and asynchronous callables and detecting async execution contexts.
    - Tags: [async, asyncio, python, utilities]

- `autoreload.py` (Size : 25737 bytes): Implements file-change monitoring and autoreload machinery used by Django's development server.
    - Tags: [autoreload, development, filesystem, python]

- `cache.py` (Size : 17157 bytes): Provides cache-control parsing and response header helpers shared by cache middleware and response code.
    - Tags: [caching, http, python, utilities]
    - TODO/FIXME/NOTE: line 320 NOTE

- `choices.py` (Size : 4318 bytes): Defines helpers and types for choices collections, including enumeration-style choices used by model fields.
    - Tags: [choices, models, python, utilities]

- `connection.py` (Size : 2639 bytes): Implements a configurable connection wrapper that lazily opens and manages a single backend connection.
    - Tags: [connections, python, utilities]

- `copy.py` (Size : 603 bytes): Provides a helper for copying objects while preserving a shallow-copy protocol.
    - Tags: [copying, python, utilities]

- `crypto.py` (Size : 3481 bytes): Implements cryptographic utility functions for salted hashes, constant-time comparison, and random tokens.
    - Tags: [cryptography, hashing, python, security]

- `csp.py` (Size : 4099 bytes): Provides parsing and representation helpers for Content Security Policy directives and values.
    - Tags: [content-security-policy, http, python, security]

- `datastructures.py` (Size : 11228 bytes): Defines reusable mappings, ordered sets, multi-value dictionaries, and other framework data structures.
    - Tags: [data-structures, mappings, python, utilities]

- `dateformat.py` (Size : 10494 bytes): Formats date and time values using Django's date-format tokens and locale-aware formatting.
    - Tags: [dates, formatting, localization, python]

- `dateparse.py` (Size : 5569 bytes): Parses ISO-style date, time, datetime, and duration strings into Python values.
    - Tags: [dates, parsing, python, utilities]

- `dates.py` (Size : 2258 bytes): Defines shared date format constants and date-related utility values.
    - Tags: [dates, formatting, python, utilities]

- `deconstruct.py` (Size : 2187 bytes): Provides the `deconstructible` decorator used to serialize Python objects into importable construction descriptions.
    - Tags: [deconstruction, migrations, python, serialization]
    - TODO/FIXME/NOTE: line 59 NOTE

- `decorators.py` (Size : 8550 bytes): Implements reusable decorators for method caching, class properties, synchronization, and other framework call patterns.
    - Tags: [decorators, python, utilities]

- `deprecation.py` (Size : 17017 bytes): Provides deprecation warning classes and mixins used to warn about deprecated APIs and feature removals.
    - Tags: [deprecation, python, warnings]
    - TODO/FIXME/NOTE: line 110 NOTE

- `duration.py` (Size : 1276 bytes): Provides conversion and formatting helpers for Python `timedelta` values.
    - Tags: [dates, durations, python, utilities]

- `encoding.py` (Size : 9054 bytes): Implements text encoding, decoding, URI conversion, and byte/string coercion helpers.
    - Tags: [encoding, python, text, utilities]

- `feedgenerator.py` (Size : 18594 bytes): Generates RSS and Atom syndication feeds, including feed metadata, entries, and XML serialization.
    - Tags: [atom, feeds, python, rss, xml]

- `formats.py` (Size : 10560 bytes): Loads locale-specific date, number, and input format definitions and exposes format lookup helpers.
    - Tags: [formats, localization, python]

- `functional.py` (Size : 15237 bytes): Implements lazy values, memoized properties, and promise-style wrappers for deferred evaluation.
    - Tags: [lazy-evaluation, python, utilities]
    - TODO/FIXME/NOTE: line 244 NOTE

- `hashable.py` (Size : 764 bytes): Provides recursive hash conversion for nested iterable values.
    - Tags: [hashing, python, utilities]

- `html.py` (Size : 19076 bytes): Provides HTML escaping, conditional escaping, HTML-safe formatting, and text-to-HTML helpers.
    - Tags: [escaping, html, python, security]
    - TODO/FIXME/NOTE: line 480 NOTE

- `http.py` (Size : 15686 bytes): Implements HTTP and URL utilities including header parsing, content disposition, redirects, query strings, and URL safety helpers.
    - Tags: [http, python, urls, utilities]
    - TODO/FIXME/NOTE: line 598 NOTE

- `inspect.py` (Size : 4955 bytes): Provides function and callable introspection helpers used by framework dispatch and compatibility code.
    - Tags: [introspection, python, utilities]

- `ipv6.py` (Size : 1887 bytes): Implements IPv6 address validation and formatting helpers.
    - Tags: [http, ipv6, networking, python]

- `json.py` (Size : 786 bytes): Provides JSON serialization helpers with Django's encoder integration.
    - Tags: [json, python, serialization]

- `log.py` (Size : 10617 bytes): Defines Django logging configuration defaults and logging-related exception/reporting helpers.
    - Tags: [logging, python, utilities]

- `lorem_ipsum.py` (Size : 5759 bytes): Generates deterministic and random placeholder text, words, and paragraphs for development use.
    - Tags: [development, lorem-ipsum, python, text]

- `module_loading.py` (Size : 5221 bytes): Provides module import, class resolution, and module-path inspection helpers.
    - Tags: [imports, modules, python, utilities]

- `numberformat.py` (Size : 3975 bytes): Formats numbers with locale-aware decimal, grouping, and precision rules.
    - Tags: [formatting, numbers, python]

- `regex_helper.py` (Size : 13126 bytes): Converts regular-expression patterns into representative matching strings, including handling grouped and repeated constructs.
    - Tags: [pattern-generation, python, regular-expressions]
    - TODO/FIXME/NOTE: line 596 FIXME

- `safestring.py` (Size : 2256 bytes): Defines string types and helpers that mark or preserve HTML-safe strings during rendering.
    - Tags: [html, python, safe-strings, security]

- `termcolors.py` (Size : 8051 bytes): Provides terminal color codes and helpers for coloring command-line output.
    - Tags: [command-line, formatting, python, terminal]

- `text.py` (Size : 15790 bytes): Implements text utilities including slugification, truncation, formatting, capitalization, and pluralization helpers.
    - Tags: [python, text, utilities]

- `timesince.py` (Size : 5060 bytes): Formats elapsed and remaining time intervals as human-readable localized strings.
    - Tags: [dates, localization, python, time]

- `timezone.py` (Size : 7550 bytes): Implements timezone configuration, current/local timezone access, and aware datetime conversion helpers.
    - Tags: [dates, python, timezones]

- `translation/reloader.py` (Size : 1150 bytes): Registers translation resources with Django's autoreloader so catalog changes can be detected in development.
    - Tags: [autoreload, internationalization, python, translation]

- `translation/template.py` (Size : 10795 bytes): Provides template-facing translation helpers and lazy translation string behavior.
    - Tags: [internationalization, python, template-tags, translation]

- `translation/trans_null.py` (Size : 1354 bytes): Implements the no-op translation backend used when translation is disabled or unavailable.
    - Tags: [internationalization, python, translation]

- `translation/trans_real.py` (Size : 23417 bytes): Implements catalog-based translation, pluralization, language selection, and lookup across locale message files.
    - Tags: [gettext, internationalization, localization, python, translation]

- `translation/__init__.py` (Size : 9180 bytes): Exposes the public translation API and manages active language state, lazy translation values, and translation function selection.
    - Tags: [internationalization, localization, python, translation]
    - TODO/FIXME/NOTE: line 282 NOTE

- `tree.py` (Size : 4520 bytes): Defines a generic tree structure used to represent hierarchical collections such as query expressions.
    - Tags: [data-structures, python, trees]

- `version.py` (Size : 9331 bytes): Parses and formats Django version strings and exposes version comparison and release metadata helpers.
    - Tags: [python, release, utilities, versioning]

- `warnings.py` (Size : 239 bytes): Defines Django-specific warning categories.
    - Tags: [python, warnings]

- `xmlutils.py` (Size : 1503 bytes): Provides XML escaping and serialization helpers.
    - Tags: [python, utilities, xml]

- `_os.py` (Size : 4972 bytes): Provides operating-system path helpers used to normalize paths and safely manage filesystem locations.
    - Tags: [filesystem, paths, python, utilities]

## Links Child Folder docmaps

None.

# Related Features

Shared framework utilities for text, HTTP, date/time, HTML safety, logging, file handling, and development autoreload. Merged `translation/`: Runtime translations, language activation, translated template content, and locale catalog reloads.

# Agent Guidance

## Read When

Tracing a shared helper used across framework components or investigating common formatting, encoding, time, or HTTP behavior. Merged `translation/`: Investigating translation lookup, plural forms, active language behavior, or gettext catalog loading.

## Modify When

Changing cross-cutting utility contracts or shared low-level behavior. Merged `translation/`: Changing Django's translation API or catalog resolution behavior.

## Avoid Modifying When

Changing a feature-specific API that does not use these shared helpers. Merged `translation/`: Changing template parser behavior unrelated to translation.
