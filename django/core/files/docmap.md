---
folder: "django/core/files"
generated_on: "2026-10-03"
num_files: 15
semantic_tags: [file-handling, file-storage, filesystem, images, in-memory, storage-api, uploads]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder provides Django's general file abstractions and upload-processing support. It includes file wrappers, uploaded-file types, upload handlers, temporary-file handling, image helpers, and filesystem utilities. Storage contracts and backends are indexed in the child `storage` map. Read this folder when changing how incoming or temporary file content is represented and processed. Merged `storage/`: This folder defines Django's storage API and its built-in storage implementations.

## Major Responsibilities

The modules wrap file objects, determine upload handling, manage temporary files, and provide helpers for file names, sizes, movement, and locking. Persistent storage behavior is delegated to `storage`. Merged `storage/`: The modules define storage operations, resolve configured storage instances, and implement local filesystem and memory-backed persistence. Shared mixins add reusable file operations to storage classes.

## Technology Notes

The code uses Python file objects, temporary-file support, and filesystem locking primitives. Merged `storage/`: The backends use Python filesystem APIs or process memory behind Django's storage interface.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `storage` : This folder defines Django's storage API and its built-in storage implementations. It includes a filesystem backend, an in-memory backend, storage lookup/configuration, and shared mixins. The storage abstractions are used by uploaded files and model file fields. Start with the base module to understand the common contract. The modules define storage operations, resolve configured storage instances, and implement local filesystem and memory-backed persistence. Shared mixins add reusable file operations to storage classes.

## Files
- `base.py` (Size : 5137 bytes): Defines Django's `File` wrapper and file operations built on Python file objects. It exposes name, size, chunks, and open/read behavior used by upload and storage code. Specialized uploaded-file behavior is implemented in a sibling module. No markers are present.
    - Tags: [file-handling, file-wrapper]

- `images.py` (Size : 2732 bytes): Defines image file support and utilities for reading image dimensions. It builds on the general file wrapper and image handling facilities. The module is used where file metadata requires image-specific interpretation. No markers are present.
    - Tags: [file-handling, images]

- `locks.py` (Size : 3742 bytes): Provides cross-platform file locking helpers. It selects platform-appropriate locking operations and exposes a common lock/unlock interface. The helpers are used around filesystem operations that require coordination. No markers are present.
    - Tags: [file-handling, filesystem, locking]

- `move.py` (Size : 3043 bytes): Implements moving a file between filesystem locations with fallback behavior. It handles the underlying file and path operations used by Django file workflows. No markers are present.
    - Tags: [file-handling, filesystem]

- `storage/base.py` (Size : 8503 bytes): Defines the abstract storage API and common filename, path, and save behavior. The class specifies methods expected from storage implementations and provides shared helpers. Filesystem and memory implementations build on this contract. No markers are present.
    - Tags: [file-storage, interface, storage-api]

- `storage/filesystem.py` (Size : 8734 bytes): Implements storage of files in a local filesystem directory. It handles paths, saving, opening, deletion, and URL generation using configured root and base URLs. The backend extends the common storage behavior. No markers are present.
    - Tags: [file-storage, filesystem, storage-backend]

- `storage/handler.py` (Size : 1553 bytes): Resolves configured storage instances and provides access to named storage backends. It supports lazy instantiation and setting-based configuration. The handler connects settings to the storage API. No markers are present.
    - Tags: [configuration, file-storage, storage-handler]

- `storage/memory.py` (Size : 10168 bytes): Implements a storage backend that retains file contents in memory. It supports opening, saving, listing, deleting, and URL-related operations using in-memory file objects. The backend conforms to the storage API without writing to disk. No markers are present.
    - Tags: [file-storage, in-memory, storage-backend]

- `storage/mixins.py` (Size : 715 bytes): Defines reusable storage mixins for operations shared among backend classes. The mixins extend storage implementations without imposing a separate persistence mechanism. The included operations work through the common storage API. No markers are present.
    - Tags: [file-storage, mixin, storage-api]

- `storage/__init__.py` (Size : 649 bytes): Exposes storage classes and compatibility imports from the storage package. It provides the public import surface for the built-in storage implementations. The concrete behavior is defined in sibling modules. No markers are present.
    - Tags: [api, file-storage, package]

- `temp.py` (Size : 2582 bytes): Provides Django temporary-file wrappers and documents behavior around temporary file creation and cleanup. It integrates Python's temporary-file implementation with Django's file API. The module documentation notes platform-specific behavior at line 8 (`NOTE`).
    - Tags: [file-handling, temporary-files]
    - TODO/FIXME/NOTE: line 8 NOTE

- `uploadedfile.py` (Size : 4418 bytes): Defines uploaded-file classes for in-memory and temporary-file-backed uploads. It provides metadata and access behavior consumed by forms and upload handlers. The classes build on Django's general file wrapper. No markers are present.
    - Tags: [file-handling, uploads]

- `uploadhandler.py` (Size : 8081 bytes): Defines upload handler classes that process incoming request body chunks. It supports memory and temporary-file upload handling and exposes upload lifecycle hooks. Request parsing selects handlers according to configuration and file size. No markers are present.
    - Tags: [file-handling, request-processing, uploads]

- `utils.py` (Size : 2678 bytes): Provides utility functions for file sizes, names, and path-related validation. These helpers support upload and storage code without implementing a storage backend. No markers are present.
    - Tags: [file-handling, filesystem, validation]

- `__init__.py` (Size : 63 bytes): Provides the public file wrapper import for the core files package. It exposes the common `File` abstraction from `base.py`. The implementation is kept in that module. No markers are present.
    - Tags: [api, file-handling, package]

---

## Links Child Folder docmaps

None.

# Related Features

Incoming file uploads, temporary-file management, and file storage. Merged `storage/`: File storage configuration, persistence, and storage API use by Django file fields.

# Agent Guidance

## Read When

Changing upload lifecycle, file wrappers, temporary files, or core file utilities. Merged `storage/`: Changing storage APIs, configured storage resolution, or built-in storage behavior.

## Modify When

Updating file handling shared by requests, uploaded files, and storage. Merged `storage/`: Updating a backend or common storage contract.

## Avoid Modifying When

Changing storage backend persistence that belongs in the child folder. Merged `storage/`: Changing upload parsing or model field behavior that does not affect storage.
