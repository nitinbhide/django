---
folder: "scripts"
generated_on: "2026-10-03"
num_files: 11
semantic_tags: ["branch maintenance", "django", "git", "github", "localization", "pull request validation", "python", "release tooling", "testing", "tests", "trac"]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder contains operational scripts for maintaining Django branches, releases, translations, and commit workflows. Release tooling builds artifacts and checks their signatures, checksums, and installation behavior. Other scripts inspect migration state and test release and commit-message helpers. PR quality automation is maintained in the `pr_quality` child folder. Merged `pr_quality/`: This folder implements automated quality checks for Django pull requests.

## Major Responsibilities

The scripts support release artifact creation and verification, stable-branch backports and archiving, migration checks, translation catalog management, and unit tests for selected script behavior. The `pr_quality` child folder handles pull request validation and its tests. Merged `pr_quality/`: `check_pr.py` coordinates retrieval of PR and ticket information, validation rules, logging, and optional job-summary or pull-request updates. `errors.py` centralizes formatted warning and error messages linked to contribution guidance. The child test folder covers individual checks and integrated behavior. Merged `pr_quality/tests/`: The test suite verifies ticket extraction and status handling, title and description requirements, AI disclosure, checklist rules, has-patch polling, and integrated result behavior. It also checks recent-commit handling and job-summary generation.

## Technology Notes

The inventory-listed files use Python and Bash. The release verifier invokes GPG and checksum utilities, creates virtual environments, installs release packages, and smoke-tests Django projects. Merged `pr_quality/`: The checker uses Python's standard-library HTTP, JSON, logging, regular-expression, and date/time facilities to call GitHub and Trac APIs. The tests use `unittest` and `unittest.mock` to isolate network interactions. Merged `pr_quality/tests/`: The tests use Python's `unittest` framework and `unittest.mock`; network fixtures create mocked `urllib` responses instead of contacting GitHub or Trac.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `pr_quality/tests` : This folder contains tests for the pull-request quality checker in the parent folder. Its test module covers individual validation rules as well as integrated processing and Markdown job-summary output. Fixtures construct PR bodies and Trac responses, while mocks replace network calls and other side effects. The tests focus on observable pass, fail, and skip outcomes for GitHub and Trac-backed checks. The test suite verifies ticket extraction and status handling, title and description requirements, AI disclosure, checklist rules, has-patch polling, and integrated result behavior. It also checks recent-commit handling and job-summary generation.
- `pr_quality` : This folder implements automated quality checks for Django pull requests. The checker validates PR descriptions and checklist disclosures, and consults GitHub and Trac data when ticket-related checks apply. It collects results so multiple issues can be reported together and defines reusable message content for failures. The `tests` child folder exercises the checker with mocked network responses. Merged `tests/`: This folder contains tests for the pull-request quality checker in the parent folder. `check_pr.py` coordinates retrieval of PR and ticket information, validation rules, logging, and optional job-summary or pull-request updates. `errors.py` centralizes formatted warning and error messages linked to contribution guidance. The child test folder covers individual checks and integrated behavior. Merged `tests/`: The test suite verifies ticket extraction and status handling, title and description requirements, AI disclosure, checklist rules, has-patch polling, and integrated result behavior. It also checks recent-commit handling and job-summary generation.

## Files
- `archive_eol_stable_branches.py` (Size : 4867 bytes): Implements an interactive helper for selecting remote stable branches, recording their last commit and update time, creating signed archival tags, and optionally deleting branches. Its functions separate command execution, checkout validation, branch discovery, metadata lookup, tag creation, and branch deletion. The `--dry-run` option lets the helper print commands rather than execute them. The script can restrict selection to branch names supplied with `--branches`.
    - Tags: [branch maintenance, git, python, release operations]

- `backport.sh` (Size : 690 bytes): Automates cherry-picking a supplied commit on a Django stable branch and amending its commit message with a branch prefix and backport attribution. It derives the stable branch name from the current Git branch and resets the working tree before starting. The script writes the amended message through a temporary file and removes that file after the amend. The shell commands run with tracing and exit-on-error enabled.
    - Tags: [backporting, bash, git, release branches]

- `check_migrations.py` (Size : 995 bytes): Runs Django's `makemigrations --check` command against the test applications selected by the repository's test-runner utilities. It adds the repository's test and root directories to Python's import path, initializes Django, and installs the applications required by discovered test modules. The command uses increased verbosity so migration discrepancies are visible. Its comment explains that it avoids `check=True` because the migration check exits through `sys.exit(1)`.
    - Tags: [django, migrations, python, validation]
    - TODO/FIXME/NOTE: NOTE line 25

- `do_django_release.py` (Size : 7915 bytes): Guides and automates preparation of Django release artifacts, including building a wheel and source tarball, computing MD5/SHA1/SHA256 checksums, and writing release verification instructions. It reads release-signing and destination settings from environment variables and records the current Git commit in the generated checksum document. It also unpacks and compares the wheel contents with the checkout, then prints follow-up signing, tagging, upload, verification, and publication commands. The script expects build artifacts and a destination directory to be available and asserts required release metadata before proceeding.
    - Tags: [checksums, django, packaging, python, release tooling]

- `manage_translations.py` (Size : 13942 bytes): Provides command-line operations for Django translation catalogs, including reporting catalog changes, showing language statistics, and fetching recent translations from Transifex. It discovers core and contrib locale directories, translates local resource names to Transifex slugs, and obtains API data using a token from the environment or the user's Transifex configuration. Catalog updates invoke Django's `makemessages`, while fetch operations use API responses to identify translated resources and languages. The file documents a TODO to merge with the latest English catalog before updating catalogs.
    - Tags: [django, localization, python, transifex, translation catalogs]
    - TODO/FIXME/NOTE: TODO line 246

- `prepare_commit_msg.py` (Size : 3727 bytes): Implements a Git `prepare-commit-msg` hook that normalizes commit summaries and adds stable-branch or backport information when appropriate. It separates message body lines from trailing Git comment lines, strips surrounding blank lines, ensures the summary ends with a period, and capitalizes its first character. On stable branches it adds a branch prefix, and when a cherry-pick hash is available it appends a backport attribution unless that text is already present. The module documentation describes installation as a repository hook.
    - Tags: [commit messages, git, python, release branches]

- `pr_quality/check_pr.py` (Size : 20130 bytes): Implements independent pull-request checks for Django contribution requirements, including ticket references and status, the Trac has-patch flag, PR title and description, AI disclosure, and checklist completion. It obtains data from GitHub and Trac, limits network calls with a timeout, and uses sentinels to distinguish skipped checks and missing tickets. The main routine combines check results, logs them, and can write a Markdown job summary or close failing PRs. Required and optional inputs are documented in the module header as environment variables.
    - Tags: [github, http, pull request validation, python, trac]

- `pr_quality/errors.py` (Size : 6961 bytes): Defines the shared error and warning levels and a `Message` object that formats titles and bodies with runtime values. It provides reusable messages for missing or invalid ticket references, contribution checklists, PR descriptions, AI disclosures, and Trac ticket state. The message text links to Django contribution and triage guidance, the forum, and Trac. These constants provide the user-facing explanations consumed by the checker.
    - Tags: [contribution guidance, error messages, pull request validation, python, trac]

- `pr_quality/tests/test_check_pr.py` (Size : 40021 bytes): Exercises the checker and message types from the parent `pr_quality` package using `unittest`. The suite builds representative PR descriptions and ticket payloads, mocks HTTP responses and checker dependencies, and tests both isolated validation functions and integrated outcomes. Coverage includes ticket extraction and fetch errors, Trac stage/status/resolution and has-patch behavior, PR title and description checks, AI disclosure, checklist handling, job summaries, and recent commit counts. The test cases also verify skipped checks and error-message details for applicable scenarios.
    - Tags: [github, integration tests, pull request validation, python, trac, unit tests]

- `tests.py` (Size : 9650 bytes): Contains unit tests for utilities in `do_django_release.py` and `prepare_commit_msg.py`. The cases verify major-version parsing across final, alpha, beta, and release-candidate versions, checksum-file contents, release artifact discovery, and commit-message formatting. Temporary directories and synthetic package contents isolate file-related test behavior. Its module documentation gives commands for running the tests from the scripts directory or repository root.
    - Tags: [commit messages, django, python, release tooling, tests]

- `verify_release.sh` (Size : 2892 bytes): Verifies a published Django release by downloading its checksum document, checking its GPG signature, obtaining linked artifacts, and validating their MD5, SHA1, and SHA256 hashes. It then creates separate virtual environments for the source tarball and wheel, installs each package, creates a project, runs migrations, and starts Django's development server as a smoke test. The script requires a `VERSION` environment variable and accepts an optional `GPG_KEY` fingerprint. It removes its working directory on exit.
    - Tags: [bash, checksums, django, gpg, release verification, smoke tests]

---

## Links Child Folder docmaps

None.

# Related Features

Release preparation and verification, stable-branch maintenance, migration validation, translation management, commit-message handling, and pull request quality checks. Merged `pr_quality/`: Pull request contribution-quality validation, including GitHub/Trac ticket checks and contribution-template requirements. Merged `pr_quality/tests/`: Automated behavioral coverage for the parent folder's Django pull-request quality checks.

## Dependency Graph

Not generated.

# Agent Guidance

## Read When

Read this index when changing release workflows, stable-branch maintenance, translation tooling, migration checks, or commit-related script tests. Follow the child index for PR quality-check behavior. Merged `pr_quality/`: Read this index when changing the PR quality workflow, contribution requirements enforced by the checker, or user-facing quality messages. Read the child test index to locate behavior coverage. Merged `pr_quality/tests/`: Read this index when investigating or extending automated tests for PR quality validation, ticket state handling, or the checker's reported results.

## Modify When

Modify the corresponding script when changing an operational workflow or its directly associated checks. Update `tests.py` when behavior in the tested release or commit-message helpers changes. Merged `pr_quality/`: Modify `check_pr.py` for validation or result-flow changes, and `errors.py` when changing the corresponding explanatory messages. Update the tests when a check's accepted or rejected behavior changes. Merged `pr_quality/tests/`: Update `test_check_pr.py` when changing validation rules, network-response handling, or output behavior in the parent package.

## Avoid Modifying When

Avoid changing these scripts for application-runtime behavior unrelated to their operational tasks. Do not infer dependencies from this index; dependency analysis is not generated. Merged `pr_quality/`: Avoid changing these files for general Django application behavior or unrelated release scripts. Dependency relationships are not calculated in this index. Merged `pr_quality/tests/`: Avoid changing this test suite for features outside the PR quality checker. Dependencies are not calculated or inferred here.
