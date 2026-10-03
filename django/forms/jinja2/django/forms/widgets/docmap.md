---
folder: "django/forms/jinja2/django/forms/widgets"
generated_on: "2026-10-02"
num_files: 31
semantic_tags: [forms, jinja2, templates, widgets]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains the Jinja2 templates used to render Django form widgets. Most specialized input templates delegate to a shared input renderer, while option, choice, and compound widgets use dedicated shared templates. A small number of templates render their own markup for controls such as selects, textareas, and clearable file inputs. These templates consume widget context prepared by Django's form rendering system.

## Major Responsibilities

- Render standard HTML input types and their widget attributes.
- Compose checkbox, radio, select, and grouped-choice controls from reusable option and multiple-input templates.
- Render compound date/time widgets and clearable file inputs.

## Technology Notes

These are Django form-rendering templates written in Jinja2 and produce HTML form controls.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `attrs.html` (Size : 172 bytes): Iterates over the widget's attribute mapping. It omits attributes whose values are `False`. Attributes valued `True` are rendered without an assignment. Other values are emitted as quoted HTML attribute values.
    - Tags: [attributes, jinja2, template, widget]

- `checkbox.html` (Size : 48 bytes): Includes the shared input template. The widget context supplies the input type, name, value, and attributes. This keeps checkbox rendering aligned with the common input markup. The file adds no checkbox-specific wrapper markup.
    - Tags: [checkbox, forms, jinja2, template]

- `checkbox_option.html` (Size : 55 bytes): Includes the shared input-option template for a checkbox choice. The included template renders the input and conditionally wraps it with its label. The option's widget context supplies the choice-specific values. No separate choice markup is defined here.
    - Tags: [checkbox, forms, jinja2, template]

- `checkbox_select.html` (Size : 57 bytes): Includes the shared multiple-input template. That renderer iterates over choice groups and their option widgets. Each option is rendered through its own template name. This file selects that shared composition for checkbox-select widgets.
    - Tags: [checkbox, forms, jinja2, multiple-input, template]

- `clearable_file_input.html` (Size : 559 bytes): Renders the current file value and an initial-file link when the widget has an initial value. When the field is not required, it adds a checkbox and label for clearing the existing file. It then renders the file input with the shared attribute template. The widget context supplies the text, names, identifiers, and state used by this markup.
    - Tags: [file-upload, forms, jinja2, template, widget]

- `color.html` (Size : 48 bytes): Includes the shared input template for a color widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no color-specific HTML.
    - Tags: [color-input, forms, jinja2, template, widget]

- `date.html` (Size : 48 bytes): Includes the shared input template for a date widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no date-specific HTML.
    - Tags: [date-input, forms, jinja2, template, widget]

- `datetime.html` (Size : 48 bytes): Includes the shared input template for a datetime widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no datetime-specific HTML.
    - Tags: [datetime-input, forms, jinja2, template, widget]

- `email.html` (Size : 48 bytes): Includes the shared input template for an email widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no email-specific HTML.
    - Tags: [email-input, forms, jinja2, template, widget]

- `file.html` (Size : 48 bytes): Includes the shared input template for a file widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no file-specific HTML.
    - Tags: [file-input, forms, jinja2, template, widget]

- `hidden.html` (Size : 48 bytes): Includes the shared input template for a hidden widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no hidden-input-specific HTML.
    - Tags: [forms, hidden-input, jinja2, template, widget]

- `input.html` (Size : 172 bytes): Renders an HTML input using the widget's type and name. It emits a value only when the context value is not `None`. It includes the shared attribute template for additional HTML attributes. This is the common renderer used by many specialized input templates.
    - Tags: [forms, html-input, jinja2, template, widget]

- `input_option.html` (Size : 219 bytes): Renders the shared input template for a choice option. When `wrap_label` is true, it encloses the input and label text in a label element. It uses the widget's identifier for the label's `for` attribute when present. The wrapper is omitted when the context disables label wrapping.
    - Tags: [forms, jinja2, label, template, widget]

- `multiple_hidden.html` (Size : 54 bytes): Includes the shared compound-widget renderer. The included template iterates through the widget's subwidgets and selects each subwidget's template. This reuses compound rendering for multiple hidden inputs. No additional markup is defined in this file.
    - Tags: [forms, jinja2, multiwidget, template]

- `multiple_input.html` (Size : 395 bytes): Renders a container for grouped multiple-choice options. It carries the widget's identifier and CSS class when available. The template iterates over option groups and renders each option using its designated template. Nonempty groups receive a nested label wrapper.
    - Tags: [forms, jinja2, multiple-input, template, widget]

- `multiwidget.html` (Size : 86 bytes): Iterates over the widget's subwidgets. Each subwidget is rendered by including its named template. Whitespace trimming keeps the generated sequence compact. The template provides shared composition for compound widgets.
    - Tags: [forms, jinja2, multiwidget, template, widget]

- `number.html` (Size : 48 bytes): Includes the shared input template for a number widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no number-specific HTML.
    - Tags: [forms, jinja2, number-input, template, widget]

- `password.html` (Size : 48 bytes): Includes the shared input template for a password widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no password-specific HTML.
    - Tags: [forms, jinja2, password-input, template, widget]

- `radio.html` (Size : 57 bytes): Includes the shared multiple-input template for radio choices. The included renderer handles option groups and each option's named template. This keeps radio-choice composition aligned with other grouped controls. This file adds no separate choice markup.
    - Tags: [forms, jinja2, multiple-input, radio, template]

- `radio_option.html` (Size : 55 bytes): Includes the shared input-option template for a radio choice. The included template renders the input and conditionally wraps it with its label. The option's widget context supplies the choice-specific values. No separate choice markup is defined here.
    - Tags: [forms, jinja2, label, radio, template]

- `search.html` (Size : 48 bytes): Includes the shared input template for a search widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no search-specific HTML.
    - Tags: [forms, jinja2, search-input, template, widget]

- `select.html` (Size : 365 bytes): Renders a select element with the widget's name and shared attributes. It iterates over option groups and includes each option's named template. Named groups are enclosed in `optgroup` elements. The output structure follows the widget's grouped choices.
    - Tags: [forms, jinja2, select, template, widget]

- `select_date.html` (Size : 54 bytes): Includes the shared compound-widget renderer. The included template iterates over the date widget's subwidgets and renders each through its named template. This delegates the component sequence to common multiwidget behavior. No additional date-specific markup appears here.
    - Tags: [date, forms, jinja2, multiwidget, template]

- `select_option.html` (Size : 110 bytes): Renders one option element using the widget's value and label. It includes the shared attribute template for option attributes. The option's context determines the displayed text and selection-related attributes. This template is used by select rendering for individual choices.
    - Tags: [forms, jinja2, option, select, template]

- `splitdatetime.html` (Size : 54 bytes): Includes the shared compound-widget renderer. The included template iterates over the widget's subwidgets and renders each through its named template. This delegates component composition to common multiwidget behavior. No additional split-datetime markup appears here.
    - Tags: [date, datetime, forms, jinja2, multiwidget, template]

- `splithiddendatetime.html` (Size : 54 bytes): Includes the shared compound-widget renderer. The included template iterates over the widget's subwidgets and renders each through its named template. This delegates component composition to common multiwidget behavior. No additional hidden-datetime markup appears here.
    - Tags: [date, datetime, forms, hidden-input, jinja2, multiwidget, template]

- `tel.html` (Size : 48 bytes): Includes the shared input template for a telephone widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no telephone-specific HTML.
    - Tags: [forms, jinja2, phone-input, template, widget]

- `text.html` (Size : 48 bytes): Includes the shared input template for a text widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no text-specific HTML.
    - Tags: [forms, jinja2, template, text-input, widget]

- `textarea.html` (Size : 145 bytes): Renders a textarea with the widget's name and shared attributes. It emits the widget value when that value is truthy. The closing tag follows the rendered content. This template provides the dedicated markup for multiline text input.
    - Tags: [forms, jinja2, template, textarea, widget]

- `time.html` (Size : 48 bytes): Includes the shared input template for a time widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no time-specific HTML.
    - Tags: [forms, jinja2, template, time-input, widget]

- `url.html` (Size : 48 bytes): Includes the shared input template for a URL widget. The included renderer uses the widget context for its type and attributes. Reusing the shared template keeps the input markup consistent. This file adds no URL-specific HTML.
    - Tags: [forms, jinja2, template, url-input, widget]

---

## Links Child Folder docmaps

None.

# Related Features

Django form field rendering, Jinja2 template backend support, HTML input widgets, choice controls, and compound widgets.

# Agent Guidance

## Read When

Tracing Jinja2 form rendering, changing widget markup, or comparing template behavior with Django's widget rendering context.

## Modify When

Changing the HTML output of a Jinja2-backed form widget or its shared input, attribute, choice, or compound-widget rendering.

## Avoid Modifying When

Changing widget Python behavior or template-engine integration; those responsibilities belong to the form widget classes and template backend code.