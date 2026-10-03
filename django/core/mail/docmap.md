---
folder: "django/core/mail"
generated_on: "2026-10-03"
num_files: 13
semantic_tags: [email, email-backends, email-messages, filesystem, headers, smtp, testing]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder implements Django's email API, message construction, and supporting utilities. It exposes connection and send helpers, models message headers and attachments, and preserves compatibility behavior. Delivery implementations are listed in the child backend map. Read the message and API modules when changing how messages are built or submitted. Merged `backends/`: This folder contains implementations of Django's email backend interface.

## Major Responsibilities

The modules construct and validate email messages, dispatch them through configured backends, and provide compatibility and exception helpers. Backends are selected and used through the public mail API. Merged `backends/`: The modules implement connection lifecycle and message delivery for each configured transport. Their common interface lets the mail API select a backend from settings.

## Technology Notes

The implementation builds on Python's email package and Django's configurable backend interface. Merged `backends/`: Backends use Python's SMTP and filesystem APIs, console output, or process-local memory.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `backends` : This folder contains implementations of Django's email backend interface. Backends deliver messages through SMTP or route them to console, files, memory, or a no-op implementation. The common base class defines shared connection and send behavior. Choose the backend module corresponding to the delivery destination being changed. The modules implement connection lifecycle and message delivery for each configured transport. Their common interface lets the mail API select a backend from settings.

## Files
- `backends/base.py` (Size : 4423 bytes): Defines the base email backend, including connection management and the send-messages contract. It provides shared handling for fail-silently behavior and message iteration. Concrete backends implement transport-specific delivery. No markers are present.
    - Tags: [email, interface, transport]

- `backends/console.py` (Size : 1523 bytes): Implements a backend that writes email messages to the configured console stream. It manages connection state and emits formatted message content. This backend is useful when delivery should be observable in command output. No markers are present.
    - Tags: [console, email, testing]

- `backends/dummy.py` (Size : 244 bytes): Implements a no-op email backend. It accepts sends without delivering messages. The backend satisfies the email interface when delivery is intentionally disabled. No markers are present.
    - Tags: [dummy-backend, email]

- `backends/filebased.py` (Size : 3758 bytes): Implements email delivery by writing messages to files in a configured directory. It opens and closes output files around message sending and formats each message for storage. The backend supports inspecting generated mail outside an SMTP service. No markers are present.
    - Tags: [email, filesystem, testing]

- `backends/locmem.py` (Size : 1145 bytes): Implements an in-memory email backend that appends sent messages to a process-local outbox. It provides the message collection used by tests and local development. It does not contact an external mail transport. No markers are present.
    - Tags: [email, in-memory, testing]

- `backends/smtp.py` (Size : 10083 bytes): Implements SMTP email delivery and configuration. It establishes an SMTP connection, applies authentication and TLS options, and sends messages through Python's SMTP client. The backend supports Django's configured email connection settings. No markers are present.
    - Tags: [email, smtp, tls]

- `backends/__init__.py` (Size : 38 bytes): Marks the mail backends package. It contains no backend behavior. Concrete delivery implementations are located in the sibling modules. No markers are present.
    - Tags: [email, package]

- `deprecation.py` (Size : 2309 bytes): Contains email compatibility and deprecation support. It preserves or signals behavior needed during API transitions. The module is separate from message formatting and backend transport. No markers are present.
    - Tags: [deprecation, email]

- `exceptions.py` (Size : 617 bytes): Defines exceptions raised by Django's mail functionality. The types distinguish mail-specific failures for callers and backend implementations. No markers are present.
    - Tags: [email, exceptions]

- `handler.py` (Size : 2815 bytes): Implements the email message handler used to send message objects through a connection. It coordinates message serialization to the email package and backend send operations. The public mail API uses it to process configured messages. No markers are present.
    - Tags: [email, email-messages]

- `message.py` (Size : 26710 bytes): Defines Django email message and attachment classes, including MIME construction and header handling. It validates message fields and converts content into Python email objects for delivery. The backend layer sends the resulting messages. No markers are present.
    - Tags: [attachments, email, headers, mime]

- `utils.py` (Size : 528 bytes): Provides small utilities used by Django's mail API. It centralizes helper behavior shared by mail modules. No markers are present.
    - Tags: [email, utilities]

- `__init__.py` (Size : 12955 bytes): Provides the public email sending API, connection helper, and convenience functions. It loads configured backends and dispatches messages through them. Lines 133 and 211 contain `NOTE` text in method documentation describing the frozen API.
    - Tags: [api, email, email-backends]
    - TODO/FIXME/NOTE: line 133 NOTE; line 211 NOTE

---

## Links Child Folder docmaps

None.

# Related Features

Email construction, attachment handling, sending, and configurable delivery. Merged `backends/`: Email delivery through configurable backends.

# Agent Guidance

## Read When

Changing message construction, mail APIs, or configured email delivery. Merged `backends/`: Changing email transport, connection configuration, or backend message delivery.

## Modify When

Updating public mail behavior, validation, or message dispatch. Merged `backends/`: Adding or correcting an email backend implementation.

## Avoid Modifying When

Changing a transport-specific concern implemented in the child backend folder. Merged `backends/`: Changing email message construction that is independent of transport.
