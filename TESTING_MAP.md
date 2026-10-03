# Testing Map

This map is limited to test strategy and coverage facts present in the generated docmap hierarchy. It does not infer test coverage from implementation files.

## Test strategy

- `tox.ini`, summarized in `DOCMAP.md`, defines environments for the Python suite and multiple documentation, formatting, and lint checks.
- `Gruntfile.js`, summarized in `DOCMAP.md`, configures QUnit against `js_tests/tests.html`.
- `django/docmap.md` describes Django's test framework, HTTP test client, assertions, test runner, database test utilities, and `unittest` integration.

## Coverage areas

- The generated maps do not expose the repository's full test suite or a complete feature-to-test mapping.
- `scripts/docmap.md` contains merged documentation for the pull-request quality checker's tests. Those tests cover ticket extraction and status, title and description checks, AI disclosure, checklists, polling, and result reporting.
- Other feature-specific test coverage: `Not available in the generated docmaps`.

## Feature-to-test mapping

| Feature area | Test references represented in docmaps |
| --- | --- |
| JavaScript UI | `js_tests/tests.html`, referenced by the root Gruntfile summary in `DOCMAP.md` |
| Pull-request quality checks | Merged `pr_quality/tests` summary in `scripts/docmap.md` |
| Django framework features | `django/docmap.md` documents test infrastructure, but individual feature-to-test links are not available in the generated docmaps |

## Test suites and plans

- Django framework test infrastructure: `django/docmap.md` (merged `test` package summary).
- Pull-request quality tests: `scripts/docmap.md` (merged `pr_quality/tests` summary).
- JavaScript QUnit suite: `DOCMAP.md` (root `Gruntfile.js` file entry).
- Test-plan documents and further suite references: `Not available in the generated docmaps`.
