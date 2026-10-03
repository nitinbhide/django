---
folder: "django/contrib/admindocs/templates/admin_doc"
generated_on: "2026-10-02"
num_files: 10
semantic_tags: [admin, documentation, django, templates]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains Django admin templates for the admindocs user interface. Its pages provide a documentation landing page and reference indexes for models, views, template tags, and template filters. Detail pages present model, view, and template information, while a separate page explains when docutils is unavailable. The templates use Django inheritance, URL tags, and translated text to render the documentation views.

## Major Responsibilities

Renders the admindocs navigation, reference indexes, and individual reference pages. It also presents the missing-docutils notice and browser bookmarklet instructions.

## Technology Notes

The templates use Django's HTML template language, including inheritance, regrouping, sorting, internationalization, and URL reversal. The bookmarklet page also contains JavaScript for documentation navigation.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `bookmarklets.html` (Size : 1309 bytes): This template presents browser bookmarklets for accessing admin documentation. It explains how to add the bookmarklet to a browser toolbar and includes JavaScript that reads the `x-view` response header to navigate to view documentation. The script uses an XMLHttpRequest and Django URL reversal. The page extends the admin base template and uses translated text.
    - Tags: [admin, bookmarklet, browser-tool, documentation, javascript, navigation]

- `index.html` (Size : 1396 bytes): This template is the landing page for the admindocs interface. It links to documentation for template tags, filters, models, views, and bookmarklets. Each section has descriptive text identifying the reference content. The page extends the admin base template and uses internationalization tags.
    - Tags: [admin, documentation, hub, index, navigation, overview]

- `missing_docutils.html` (Size : 815 bytes): This template explains that the docutils library is required for a documentation feature but is unavailable. It links to installation resources and advises contacting an administrator for assistance. The links are included in translated text. The page presents the missing dependency and does not install it.
    - Tags: [admin, dependency, documentation, error, installation, requirement]

- `model_detail.html` (Size : 1970 bytes): This template renders reference details for one model. It presents the model name, summary, and description, followed by a fields table with types and descriptions. An optional methods table lists model methods that accept arguments. Breadcrumbs and navigation links support movement through the documentation.
    - Tags: [admin, database, documentation, field, method, model, reference, table]

- `model_index.html` (Size : 1385 bytes): This template renders the model reference index grouped by Django application. It displays model and application names, using template regrouping and sorting for organization. A sidebar provides links to application sections. It serves as navigation to individual model documentation.
    - Tags: [admin, app, documentation, grouping, index, model, reference, sidebar]

- `template_detail.html` (Size : 1062 bytes): This template displays the search path for a named template. It lists directories in which Django searches and marks paths where the template does not exist. A link returns to the documentation root. The page presents path information supplied by the documentation view.
    - Tags: [admin, documentation, file-path, reference, search-path, template]

- `template_filter_index.html` (Size : 1802 bytes): This template renders the reference index for template filters, grouped by library. It displays filter names and their documented titles and descriptions. A sidebar provides alphabetical navigation. Regrouping and sorting tags organize built-in and custom library entries.
    - Tags: [admin, alphabetical-index, built-in, custom, documentation, filter, library, reference, sidebar]

- `template_tag_index.html` (Size : 1758 bytes): This template renders the reference index for template tags, grouped by library. It distinguishes built-in and custom libraries and displays each tag's name and documentation. A sidebar provides alphabetical navigation. Regrouping and sorting tags structure the entries.
    - Tags: [admin, alphabetical-index, built-in, custom, documentation, library, reference, sidebar, tag]

- `view_detail.html` (Size : 931 bytes): This template presents documentation for an individual view. It displays the view name, summary, and extracted documentation body. Optional sections show context information and templates used by the view. Breadcrumbs and a back link provide navigation to the view index.
    - Tags: [admin, context, documentation, meta, reference, template, view]

- `view_index.html` (Size : 1761 bytes): This template renders the view reference index grouped by URL namespace. Each entry can show its URL, function path, and URL name. A sidebar links to namespace sections, while regrouping and sorting tags organize the index. The template also uses `ifchanged` to manage repeated namespace headings.
    - Tags: [admin, alphabetical-index, app, documentation, grouping, index, namespace, reference, sidebar, url, view]

## Links Child Folder docmaps

None.

# Related Features

The indexed templates render the admindocs landing page and reference pages for Django models, views, templates, template tags, and filters, along with bookmarklet guidance and a missing-docutils notice.

# Agent Guidance

## Read When

Changing the HTML presentation or navigation of the Django admindocs interface.

## Modify When

The requested change concerns a documentation landing page, reference index, detail view, bookmarklet instructions, or the missing-docutils notice.

## Avoid Modifying When

Changing the data extraction or URL behavior that supplies these templates without a presentation requirement.