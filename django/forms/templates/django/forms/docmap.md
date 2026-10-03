---
folder: "django/forms/templates/django/forms"
generated_on: "2026-10-02"
num_files: 17
semantic_tags: [django-template, django-templates, error-list, errors, form-rendering, forms, formsets, html, layouts, templates, validation]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains Django's built-in HTML templates for form rendering. Direct templates provide reusable attribute, field, and label rendering and layouts using divs, paragraphs, tables, and unordered lists. Child indexes cover formsets, form-error formats, and the set of built-in widget templates. Together, the hierarchy guides changes to the server-rendered presentation of Django forms. Merged `errors/`: This directory groups the built-in Django templates for form error output. Merged `formsets/`: This folder contains four retained Django formset templates, each providing a layout-specific rendering path.

## Major Responsibilities

Renders forms and fields into HTML layouts and provides navigation to widget, formset, and validation-error templates. Merged `errors/`: Organizes the Django-template error presentation variants for forms. Merged `errors/dict/`: Provide default, plain-text, and HTML rendering variants for dictionary-shaped form errors. Merged `errors/list/`: Render list-shaped form errors in HTML and plain-text variants. Merged `formsets/`: Render formsets in four Django form output layouts.

## Technology Notes

The files use Django's template language and form-rendering API. Merged `errors/`: The child templates use Django template syntax and HTML or plain text. Merged `errors/dict/`: Django templates and form error context. Merged `errors/list/`: Django template language and form error context. Merged `formsets/`: Django template language and form rendering methods.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `errors/dict` : This folder contains Django templates for dictionary-shaped form errors. Its default template delegates HTML rendering to the unordered-list template. The text template renders fields and errors as nested bullets. The HTML template renders field/error pairs as list items. Provide default, plain-text, and HTML rendering variants for dictionary-shaped form errors.
- `errors/list` : This folder contains three Django templates for rendering form errors. `default.html` includes the unordered-list template. `ul.html` renders errors as HTML list items, while `text.txt` renders them as plain-text bullets. The templates iterate over the supplied errors, with the HTML list guarded against an empty collection. Render list-shaped form errors in HTML and plain-text variants.
- `errors` : This directory groups the built-in Django templates for form error output. Its `dict` and `list` child folders contain distinct layouts for dictionary-shaped and list-shaped errors. No eligible source files are stored directly here. The child indexes describe the default, plain-text, and HTML output variants. Merged `dict/`: This folder contains Django templates for dictionary-shaped form errors. Merged `list/`: This folder contains three Django templates for rendering form errors. Organizes the Django-template error presentation variants for forms. Merged `dict/`: Provide default, plain-text, and HTML rendering variants for dictionary-shaped form errors. Merged `list/`: Render list-shaped form errors in HTML and plain-text variants.
- `formsets` : This folder contains four retained Django formset templates, each providing a layout-specific rendering path. Every template emits `formset.management_form` and loops over the forms, delegating per-form output to the matching rendering method. The variants are div, paragraph, table, and unordered-list output. All four entries have no TODO, FIXME, or NOTE markers. Render formsets in four Django form output layouts.

## Files
- `attrs.html` (Size : 165 bytes): This template renders widget attributes as HTML attribute text. It omits attributes whose values are false and renders true values as boolean attributes. Other values are emitted as name-value pairs. It is included by widget and element templates as a reusable component.
    - Tags: [attributes, django-templates, forms, html]

- `div.html` (Size : 525 bytes): This template renders form fields in div containers. It emits top-level errors before iterating over fields and applies each field's CSS classes. Individual fields are rendered through `field.as_field_group`. Hidden fields are positioned based on whether errors are present and the field's position in the loop.
    - Tags: [div-rendering, django-templates, forms, html]

- `errors/dict/default.html` (Size: 48 bytes): Includes `django/forms/errors/dict/ul.html`. It delegates its output to that template. It contains no error iteration. It contains no markup of its own.
  - Tags: [django-template, errors, forms, include]

- `errors/dict/text.txt` (Size: 116 bytes): Iterates over fields and their errors. It writes each field with a `*` prefix. It writes each error beneath its field with two spaces of indentation and a `*` prefix. It produces plain text output.
  - Tags: [django-template, errors, forms, plain-text]

- `errors/dict/ul.html` (Size: 137 bytes): Renders output only when `errors` is truthy. It wraps the output in a `<ul>` whose class comes from `error_class`. It iterates over field and error pairs. Each pair is rendered in a `<li>`.
  - Tags: [django-template, errors, forms, html, unordered-list]

- `errors/list/default.html` (Size: 48 bytes): Delegates rendering to `django/forms/errors/list/ul.html` using a Django template include. It adds no surrounding markup of its own. It defines no conditional logic. It defines no iteration logic.
  - Tags: [django-template, error-list, template-include]

- `errors/list/text.txt` (Size: 54 bytes): Renders the errors as a plain-text list. It iterates over `errors` with a Django template loop. Each error is preceded by `* ` and followed by a newline. An empty collection produces no list entries.
  - Tags: [django-template, error-list, plain-text]

- `errors/list/ul.html` (Size: 186 bytes): Renders errors as an HTML unordered list when `errors` is truthy. The `<ul>` class comes from `error_class`. When `errors.field_id` is present, it adds an ID formed by appending `_error`. Each error is rendered in its own `<li>`.
  - Tags: [django-template, error-list, html, unordered-list]

- `field.html` (Size : 502 bytes): This template renders a field using a fieldset and legend when requested, or a standard label otherwise. It includes help text and associates it with the field using accessibility attributes when available. Field errors and the widget are rendered with the selected wrapper. The field context determines the markup and help-text identifiers.
    - Tags: [django-templates, fieldsets, forms, html, labels]

- `formsets/div.html` (Size: 84 bytes): Defines the div-oriented formset output template. It renders `formset.management_form` before looping over the forms. Each form is rendered with `form.as_div` using Django template syntax. The file contains no TODO, FIXME, or NOTE markers.
  - Tags: [django-templates, div-rendering, form-rendering, formsets, html]

- `formsets/p.html` (Size: 82 bytes): Defines the paragraph-oriented formset output template. It renders `formset.management_form` before looping over the forms. Each form is rendered with `form.as_p` using Django template syntax. The file contains no TODO, FIXME, or NOTE markers.
  - Tags: [django-templates, form-rendering, formsets, html, paragraph-rendering]

- `formsets/table.html` (Size: 86 bytes): Defines the table-oriented formset output template. It renders `formset.management_form` before looping over the forms. Each form is rendered with `form.as_table` using Django template syntax. The file contains no TODO, FIXME, or NOTE markers.
  - Tags: [django-templates, form-rendering, formsets, html, table-rendering]

- `formsets/ul.html` (Size: 83 bytes): Defines the unordered-list-oriented formset output template. It renders `formset.management_form` before looping over the forms. Each form is rendered with `form.as_ul` using Django template syntax. The file contains no TODO, FIXME, or NOTE markers.
  - Tags: [django-templates, form-rendering, formsets, html, list-rendering, ul-rendering]

- `label.html` (Size : 122 bytes): This template renders label text with or without an HTML wrapper. When a tag is requested, it emits the opening and closing tags and includes `attrs.html` for attributes. Otherwise, it outputs the label text without a wrapper. The tag and attributes are supplied through template context.
    - Tags: [django-templates, forms, html, labels]

- `p.html` (Size : 751 bytes): This template renders each form field inside a paragraph element. It displays form-level errors, optional field CSS classes, labels, widgets, and help text. Help text identifiers are included when available. Hidden fields are placed according to error state and loop position.
    - Tags: [django-templates, forms, html, paragraph-rendering]

- `table.html` (Size : 892 bytes): This template renders a form as an HTML table with one row per field. Form-level errors occupy a header row spanning both columns. Each field's label appears in a header cell and its widget and help text in a data cell. Hidden fields are placed in a final row or after the last visible field.
    - Tags: [django-templates, forms, html, table-rendering]

- `ul.html` (Size : 790 bytes): This template renders a form as an unordered list, with each field inside a list item. Form-level errors appear in their own item when present. Field items can include labels, widgets, help text, and optional CSS classes. Hidden fields are positioned according to error state and iteration position.
    - Tags: [django-templates, forms, html, list-rendering]

## Links Child Folder docmaps
- `widgets/docmap.md` — Thirty-one widget templates render inputs, selects, textareas, and shared attributes or options.

# Related Features

Django form and field rendering, including HTML layout variants, reusable widget markup, formsets, and validation-error presentation. Merged `errors/`: Django-template presentation of form validation errors. Merged `errors/dict/`: Django-template rendering of dictionary-shaped form errors. Merged `errors/list/`: Django-template list rendering for form errors. Merged `formsets/`: Django formset rendering variants.

# Agent Guidance

## Read When

Changing built-in Django form HTML or determining which template controls a rendering layout. Merged `errors/`: Locating built-in Django-template error output variants. Merged `errors/dict/`: Changing error presentation in Django templates. Merged `errors/list/`: Changing Django-template form error lists or their generated IDs. Merged `formsets/`: Changing Django-template formset output layouts.

## Modify When

The requested change concerns field markup, form layout, attributes, labels, widgets, formsets, or error presentation. Merged `errors/`: The requested change concerns how form errors are presented by Django templates. Merged `errors/dict/`: The output layout or field/error markup is part of the requested change. Merged `errors/list/`: The task concerns the list markup or text output variants. Merged `formsets/`: The task affects the rendering variant or management form output.

## Avoid Modifying When

Changing form validation or widget behavior implemented in Python without a template-rendering requirement. Merged `errors/`: Changing error construction or validation without changing template output. Merged `errors/dict/`: The change concerns validation behavior rather than template rendering. Merged `errors/list/`: The change concerns error construction or validation logic. Merged `formsets/`: Changing formset data handling outside these templates.
