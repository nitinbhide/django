---
folder: "django/forms/jinja2/django/forms"
generated_on: "2026-10-02"
num_files: 17
semantic_tags: [div, django-template, error-list, errors, forms, formsets, html, jinja2, lists, paragraphs, tables, templates, validation]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains Django form rendering templates for the Jinja2 template backend. Its direct templates render fields and forms using div, paragraph, table, and list layouts, with helper templates for attributes and labels. Child indexes cover formset layouts and error rendering for dictionary and list error structures. The templates conditionally present labels, widgets, errors, help text, and hidden fields. Merged `errors/`: This directory groups the built-in Jinja2 templates for form error output. Merged `formsets/`: This folder contains four Jinja2 templates for rendering formsets in alternate formats.

## Major Responsibilities

Provides Jinja2-based form, field, and label rendering, with child templates for formsets and errors. Merged `errors/`: Organizes Jinja2 error presentation variants for Django forms. Merged `errors/dict/`: Provide default, text, and HTML rendering variants for dictionary-shaped form errors. Merged `errors/list/`: Render list-shaped form errors in HTML and plain-text variants. Merged `formsets/`: Render each formset using one of four form output methods.

## Technology Notes

The templates use Jinja2 syntax and HTML markup for Django's forms API. Merged `errors/`: The child templates use Jinja2 syntax and HTML or plain text. Merged `errors/dict/`: Jinja2 templates and Django form error context. Merged `errors/list/`: Jinja2 templates and Django form error context. Merged `formsets/`: Jinja2 templates and Django formset rendering methods.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `errors/dict` : This folder contains three Jinja2 templates for rendering dictionary-shaped form errors. `default.html` delegates to the HTML list template. `text.txt` renders nested plain-text bullets. `ul.html` renders field and error pairs in an HTML list. Provide default, text, and HTML rendering variants for dictionary-shaped form errors.
- `errors/list` : This folder contains three Jinja2 templates for rendering form errors. `default.html` includes the unordered-list template. `ul.html` renders errors as HTML list items, while `text.txt` renders them as plain-text bullets. The templates iterate over the supplied errors, with the HTML list guarded against an empty collection. Render list-shaped form errors in HTML and plain-text variants.
- `errors` : This directory groups the built-in Jinja2 templates for form error output. Its `dict` and `list` child folders provide rendering variants for dictionary-shaped and list-shaped errors. No eligible source files are stored directly here. The child indexes document the default, plain-text, and HTML templates. Merged `dict/`: This folder contains three Jinja2 templates for rendering dictionary-shaped form errors. Merged `list/`: This folder contains three Jinja2 templates for rendering form errors. Organizes Jinja2 error presentation variants for Django forms. Merged `dict/`: Provide default, text, and HTML rendering variants for dictionary-shaped form errors. Merged `list/`: Render list-shaped form errors in HTML and plain-text variants.
- `formsets` : This folder contains four Jinja2 templates for rendering formsets in alternate formats. Each template emits the formset management form and then iterates over its forms. The templates use the `as_div()`, `as_p()`, `as_table()`, and `as_ul()` rendering methods. They provide div, paragraph, table, and unordered-list output variants. Render each formset using one of four form output methods.

## Files
- `attrs.html` (Size : 165 bytes): This template serializes an attribute dictionary into HTML attribute text. It omits attributes with false values and renders true values as name-only attributes. Other values are emitted with their names. The resulting attributes are space-separated and the template is used by `label.html`.
    - Tags: [attribute, html, jinja2, rendering, template]

- `div.html` (Size : 514 bytes): This template renders form fields inside div containers. It outputs top-level errors, iterates over field and error pairs, and renders each field group. Hidden fields are placed after errors when present or at the end of the form otherwise. Optional CSS classes come from the field.
    - Tags: [containers, div, field-rendering, forms, html, jinja2, template]

- `errors/dict/default.html` (Size: 49 bytes): Consists of one Jinja2 include directive for `django/forms/errors/dict/ul.html`. It delegates rendering to the included template. It defines no local variables. It contains no local loops or conditions.
  - Tags: [django-template, errors, forms, jinja2, template-inclusion]

- `errors/dict/text.txt` (Size: 116 bytes): Iterates over `errors` as `(field, errors)` pairs and writes each field with a leading bullet. For each field, it iterates over its errors and writes nested bullet lines. It renders plain text rather than HTML elements. The template uses the context values directly.
  - Tags: [django-template, errors, forms, jinja2, text-output]

- `errors/dict/ul.html` (Size: 137 bytes): Emits markup only when `errors` is truthy. It opens a `<ul>` whose class comes from `error_class`. It iterates over `(field, error)` pairs and places both values in an `<li>`. It closes the list after rendering the entries.
  - Tags: [django-template, errors, forms, html, jinja2, list-rendering]

- `errors/list/default.html` (Size: 49 bytes): Delegates rendering to `django/forms/errors/list/ul.html` using an include statement. It adds no surrounding markup of its own. It defines no conditional logic. It defines no iteration logic.
  - Tags: [django-template, error-list, jinja2, template-include]

- `errors/list/text.txt` (Size: 54 bytes): Renders the errors as a plain-text list. It iterates over `errors` with a loop. Each error is preceded by `* ` and followed by a newline. An empty collection produces no list entries.
  - Tags: [django-template, error-list, jinja2, plain-text]

- `errors/list/ul.html` (Size: 187 bytes): Renders errors as an HTML unordered list when `errors` is truthy. The `<ul>` class comes from `error_class`. When `errors.field_id` is present, it adds an ID formed by appending `_error`. Each error is rendered in its own `<li>`.
  - Tags: [django-template, error-list, html, jinja2, unordered-list]

- `field.html` (Size : 507 bytes): This template renders one form field using either a fieldset or a label wrapper. It presents the widget and field errors and conditionally includes help text. When available, the help text identifier is associated through `aria-describedby`. The field context determines the wrapper and accessibility attributes.
    - Tags: [accessibility, field-rendering, forms, html, jinja2, template, wrapping]

- `formsets/div.html` (Size: 86 bytes): Emits `formset.management_form` before iterating over `formset`. Each form is rendered with `form.as_div()`. The template contains no additional markup. It provides the div rendering variant for formsets.
  - Tags: [div, forms, formsets, jinja2, templates]

- `formsets/p.html` (Size: 84 bytes): Emits `formset.management_form` before iterating over `formset`. Each form is rendered with `form.as_p()`. The template contains no additional markup. It provides the paragraph rendering variant for formsets.
  - Tags: [forms, formsets, jinja2, paragraphs, templates]

- `formsets/table.html` (Size: 88 bytes): Emits `formset.management_form` before iterating over `formset`. Each form is rendered with `form.as_table()`. The template contains no additional markup. It provides the table rendering variant for formsets.
  - Tags: [forms, formsets, jinja2, tables, templates]

- `formsets/ul.html` (Size: 85 bytes): Emits `formset.management_form` before iterating over `formset`. Each form is rendered with `form.as_ul()`. The template contains no additional markup. It provides the unordered-list rendering variant for formsets.
  - Tags: [forms, formsets, jinja2, lists, templates]

- `label.html` (Size : 147 bytes): This template renders label text either inside a configurable HTML tag or as plain text. It includes `attrs.html` to serialize attributes for the wrapper. The selected tag and attributes are supplied through template context. The template provides label markup rather than generating label text.
    - Tags: [forms, html, jinja2, label, template, wrapping]

- `p.html` (Size : 740 bytes): This template renders form fields in paragraph elements. It presents labels, widgets, errors, and help text for each field and applies optional CSS classes. Top-level errors are rendered before the fields. Hidden fields are placed after errors when present or at the form's end.
    - Tags: [field-rendering, forms, html, jinja2, paragraphs, template]

- `table.html` (Size : 881 bytes): This template renders a form as an HTML table with labels in header cells and widgets in data cells. Top-level errors appear in a header row spanning both columns. Help text is rendered within the widget cell. Hidden fields are placed at the form's end or in the error row.
    - Tags: [field-rendering, forms, html, jinja2, tables, template]

- `ul.html` (Size : 779 bytes): This template renders form fields as list items in an unordered list. Each item can include its label, widget, errors, and help text, with optional CSS classes. Top-level errors appear in a list item before the fields. Hidden fields are placed at the form's end or alongside errors.
    - Tags: [field-rendering, forms, html, jinja2, lists, template]

## Links Child Folder docmaps
- `widgets/docmap.md` — This folder contains the Jinja2 templates used to render Django form widgets.

# Related Features

Jinja2 rendering of Django forms, fields, labels, formsets, and validation errors in multiple HTML layouts. Merged `errors/`: Jinja2 presentation of Django form validation errors. Merged `errors/dict/`: Jinja2 rendering of dictionary-shaped form errors. Merged `errors/list/`: Jinja2 list rendering for form errors. Merged `formsets/`: Jinja2 formset rendering variants.

# Agent Guidance

## Read When

Changing Django form rendering in the Jinja2 backend or determining which template controls a particular layout. Merged `errors/`: Locating built-in Jinja2 error output variants. Merged `errors/dict/`: Changing error rendering for Jinja2 forms. Merged `errors/list/`: Changing Jinja2 form error lists or their generated IDs. Merged `formsets/`: Changing how Jinja2 formsets render their forms.

## Modify When

The requested change concerns field markup, form layout, attributes, labels, formsets, or error presentation. Merged `errors/`: The requested change concerns how form errors are presented by Jinja2 templates. Merged `errors/dict/`: The output format or field/error presentation is implemented by these templates. Merged `errors/list/`: The task concerns the list markup or text output variants. Merged `formsets/`: The requested output corresponds to one of the four template layouts.

## Avoid Modifying When

Changing form validation or widget behavior that is implemented outside these templates. Merged `errors/`: Changing error construction or validation without changing template output. Merged `errors/dict/`: The change concerns form validation logic rather than rendering. Merged `errors/list/`: The change concerns error construction or validation logic. Merged `formsets/`: Changing formset validation or management-field behavior.
