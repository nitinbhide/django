# Technology Map

This map records technologies and versions explicitly represented in the generated DOCMAP hierarchy.

## Languages and formats

- **Python:** Primary implementation language for Django and its management, database, HTTP, forms, and application APIs.
- **JavaScript and CSS:** Used for admin and GIS browser-side interactions and presentation.
- **HTML and templates:** Django template syntax is used throughout; a Jinja2 backend and template tree are also documented.
- **SQL and database-specific code:** Database and GIS indexes describe backend SQL and spatial operations.
- **Other indexed formats:** JSON, XML, YAML, shell scripts, SVG, and reStructuredText appear in repository files or documented tooling.

## Frameworks and libraries

- **Django:** The framework developed by this repository.
- **asgiref** and **sqlparse:** Runtime dependencies declared in `pyproject.toml`.
- **argon2-cffi** and **bcrypt:** Optional password-hashing dependencies declared in `pyproject.toml`.
- **Jinja2:** Optional template backend documented under `django/template/docmap.md` and `django/forms/docmap.md`.
- **GeoDjango integrations:** GIS maps document GDAL, GEOS, GeoJSON, KML/KMZ, and OpenLayers use.
- **QUnit, Grunt, and Biome:** Root files document JavaScript testing and CSS/JavaScript linting workflows.

## Databases

The database indexes describe support for SQLite, PostgreSQL, MySQL, and Oracle, with separate GIS backend support. The database ORM/backend summaries are included in `django/docmap.md`; PostgreSQL-specific extensions are indexed in `django/contrib/postgres/docmap.md`, and spatial support is indexed in `django/contrib/gis/docmap.md`.

## Build and development tooling

- **Build/package:** setuptools with the `setuptools.build_meta` backend is declared in `pyproject.toml`.
- **Python tests and checks:** tox environments are described in `tox.ini` and summarized in `DOCMAP.md`.
- **JavaScript tests:** `Gruntfile.js` defines the QUnit test target `js_tests/tests.html`.
- **Lint/format:** Black, Flake8, isort, Biome, zizmor, and documentation checks are described in the root tooling summaries.

## Version information

- Python requirement: `>= 3.12`; Python 3.12, 3.13, and 3.14 classifiers are listed in `pyproject.toml`.
- Biome: `2.4.15` is declared in the root package and schema configuration.
- OpenLayers: `10.9.0` is recorded in the GIS static asset docmap summary.
- Django's package version is dynamically read from `django.__version__`; no literal release version is recorded in the generated maps.
