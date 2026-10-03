---
folder: "django/core/cache"
generated_on: "2026-10-03"
num_files: 9
semantic_tags: [cache, database, filesystem, memcached, redis, template-fragments]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder provides Django's cache handler and shared cache utilities. It connects configured cache aliases to backend instances and supplies helper functions used by cache consumers. Concrete storage strategies are indexed in the child backend map. Read the handler before changing alias lookup or cache lifecycle behavior. Merged `backends/`: This folder implements Django's cache backend adapters.

## Major Responsibilities

The modules resolve configured cache backends, close cache connections, and construct cache keys for template fragments. Backend-specific data storage is delegated to the `backends` folder. Merged `backends/`: The modules define a common backend interface and concrete storage-specific cache implementations. They handle serialization, expiration, cache keys, and backend connection behavior appropriate to each store.

## Technology Notes

The code integrates Django settings and connection-handler abstractions with cache backends. Merged `backends/`: The modules interface with Django's database and file-storage APIs, Memcached clients, and Redis clients.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `backends` : This folder implements Django's cache backend adapters. It provides common cache operations alongside database, file, in-process, Memcached, and Redis storage strategies. The adapters plug into the cache framework through backend classes and shared key/timeout behavior. Select a backend module when changing storage-specific cache semantics. The modules define a common backend interface and concrete storage-specific cache implementations. They handle serialization, expiration, cache keys, and backend connection behavior appropriate to each store.

## Files
- `backends/base.py` (Size : 16206 bytes): Defines the base cache backend API and shared key, timeout, and validation behavior. Concrete backends inherit the common cache operations and specialize storage access. It also provides cache-key transformation and version handling. No markers are present.
    - Tags: [cache, interface, key-management]

- `backends/db.py` (Size : 12041 bytes): Implements a cache backend that stores entries in a database table. It reads and writes serialized values with expiry data and supports table creation. Backend operations reuse the common cache interface. Line 145 has a `NOTE` comment about datetime typecasting.
    - Tags: [cache, database, serialization]
    - TODO/FIXME/NOTE: line 145 NOTE

- `backends/dummy.py` (Size : 1077 bytes): Implements a cache backend whose operations do not retain values. Reads behave as misses and writes have no persistent effect. It conforms to the cache backend interface for configurations that intentionally disable caching. No markers are present.
    - Tags: [cache, dummy-backend]

- `backends/filebased.py` (Size : 6085 bytes): Stores cache entries as files under a configured directory. It handles key-to-filename mapping, expiry checks, and serialized values through filesystem operations. The class supplies the standard cache API using local files. No markers are present.
    - Tags: [cache, filesystem, serialization]

- `backends/locmem.py` (Size : 4154 bytes): Implements a process-local memory cache with synchronization around its shared in-process data. It tracks expiration and limits stored entries according to backend options. It is intended for local use rather than shared cross-process cache state. No markers are present.
    - Tags: [cache, in-memory, thread-safety]

- `backends/memcached.py` (Size : 6980 bytes): Provides Django cache backends for Memcached clients. It adapts client operations and configuration to Django's cache interface, including key validation and timeout handling. Backend variants support the client APIs exposed by their respective libraries. No markers are present.
    - Tags: [cache, memcached]

- `backends/redis.py` (Size : 8738 bytes): Implements the Redis cache backend and its connection/client configuration. Cache values and expiry are managed through Redis operations while honoring Django's cache key and serialization behavior. It exposes the standard backend methods to Django's cache handler. No markers are present.
    - Tags: [cache, redis, serialization]

- `utils.py` (Size : 492 bytes): Builds stable keys for template fragment caching from a fragment name and variation values. It provides the helper used to address cached template fragments. The module contains no backend storage behavior. No markers are present.
    - Tags: [cache, template-fragments]

- `__init__.py` (Size : 1995 bytes): Defines the cache handler responsible for constructing and retrieving configured cache backends. It exposes functions for accessing named caches and closing cache connections. Backend implementations are located in `backends`. No markers are present.
    - Tags: [cache, configuration, handler]

---

## Links Child Folder docmaps

None.

# Related Features

Named cache configuration, cache lifecycle, and template-fragment cache keys. Merged `backends/`: Cache reads, writes, expiry, and backend selection.

# Agent Guidance

## Read When

Changing cache selection, alias handling, or cache key construction. Merged `backends/`: Changing cache persistence, backend configuration, cache key handling, or storage-specific behavior.

## Modify When

Updating cache handler behavior or shared cache helpers. Merged `backends/`: Adding or correcting a cache backend implementation or shared backend behavior.

## Avoid Modifying When

Changing storage-specific behavior implemented by a backend. Merged `backends/`: Changing unrelated cache consumers that do not alter backend behavior.
