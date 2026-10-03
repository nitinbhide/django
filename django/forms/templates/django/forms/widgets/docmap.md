---
folder: "django/forms/templates/django/forms/widgets"
generated_on: "2026-10-02"
num_files: 31
semantic_tags: [django-templates, forms, html, widgets]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains Django templates used to render form widgets and their constituent controls. Shared templates provide input attributes, standard input markup, multiwidget rendering, and option markup. Specialized templates compose these shared pieces for checkbox, radio, select, date/time, file, and other widget types. The templates contain no TODO, FIXME, or NOTE markers.

## Major Responsibilities

Render form input elements, options, grouped choices, multiple widgets, and clearable file controls using reusable template includes.

## Technology Notes

Django templates render HTML and compose widget markup through includes and per-widget template names.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `attrs.html` (Size: 172 bytes): Iterates over a widget's attributes. It omits attributes whose value is `False`. It renders attributes with `True` as boolean attributes. Other values are converted to strings and rendered as quoted attribute values.
  - Tags: [attributes, django-templates, html]
- `checkbox.html` (Size: 48 bytes): Includes `input.html`. It delegates the input element markup to that shared template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [checkbox, django-templates, forms]
- `checkbox_option.html` (Size: 55 bytes): Includes `input_option.html`. It delegates option label wrapping and input rendering to that shared template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [checkbox, django-templates, forms, options]
- `checkbox_select.html` (Size: 57 bytes): Includes `multiple_input.html`. It delegates the rendering of the multiple-choice widget to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [checkbox, django-templates, forms, multiple-choice]
- `clearable_file_input.html` (Size: 559 bytes): Renders the initial value and upload input for a clearable file widget. When an initial value exists, it displays the configured initial text and a link to the current file URL. For non-required widgets, it renders a clear checkbox and its label, honoring disabled and checked attributes. It then renders the configured input text and a file input with shared widget attributes.
  - Tags: [file-input, forms, html, upload]
- `color.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [color-input, django-templates, forms]
- `date.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [date-input, django-templates, forms]
- `datetime.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [datetime-input, django-templates, forms]
- `email.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, email-input, forms]
- `file.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, file-input, forms]
- `hidden.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, hidden-input]
- `input.html` (Size: 189 bytes): Renders an HTML input element. It sets the input type and name from the widget context. It renders a value only when the widget value is not `None`, converting that value to a string. It includes `attrs.html` to render the widget's remaining attributes.
  - Tags: [django-templates, forms, html, input]
- `input_option.html` (Size: 219 bytes): Conditionally wraps an input in a label when `widget.wrap_label` is true. If the widget has an ID, that ID is used as the label's `for` attribute. It includes `input.html` to render the input control. When wrapping is enabled, it also renders the widget label.
  - Tags: [django-templates, forms, html, labels, options]
- `multiple_hidden.html` (Size: 54 bytes): Includes `multiwidget.html`. It delegates rendering of its subwidgets to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [django-templates, forms, hidden-input, multiwidget]
- `multiple_input.html` (Size: 426 bytes): Renders a container for a widget's option groups. It conditionally applies the widget ID and class to the container. For each group, it renders a group label when one is present and iterates through the group's options. Each option is rendered using its own `template_name`.
  - Tags: [django-templates, forms, html, multiple-choice]
- `multiwidget.html` (Size: 117 bytes): Iterates over the widget's subwidgets. Each subwidget is rendered using its `template_name`. The loop is wrapped in Django's `spaceless` tag. The file contains no surrounding HTML element.
  - Tags: [django-templates, forms, multiwidget, subwidgets]
- `number.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, number-input]
- `password.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, password-input]
- `radio.html` (Size: 57 bytes): Includes `multiple_input.html`. It delegates rendering of the multiple-choice widget to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [django-templates, forms, multiple-choice, radio]
- `radio_option.html` (Size: 55 bytes): Includes `input_option.html`. It delegates option label wrapping and input rendering to that shared template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, options, radio]
- `search.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, search-input]
- `select.html` (Size: 384 bytes): Renders a `select` element with the widget's name and shared attributes. It iterates over the widget's option groups. Named groups are wrapped in `optgroup` elements with their group name as the label. Each choice is rendered using its own `template_name`.
  - Tags: [django-templates, forms, html, select]
- `select_date.html` (Size: 54 bytes): Includes `multiwidget.html`. It delegates rendering of its subwidgets to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [date-input, django-templates, forms, multiwidget]
- `select_option.html` (Size: 127 bytes): Renders an HTML `option` element. It sets the option value from the widget value after converting it to a string. It includes `attrs.html` to render additional widget attributes. It renders the widget label as the option's contents.
  - Tags: [django-templates, forms, html, options, select]
- `splitdatetime.html` (Size: 54 bytes): Includes `multiwidget.html`. It delegates rendering of its subwidgets to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [datetime-input, django-templates, forms, multiwidget]
- `splithiddendatetime.html` (Size: 54 bytes): Includes `multiwidget.html`. It delegates rendering of its subwidgets to that shared template. The included template receives the current widget context. The file contains no additional markup.
  - Tags: [datetime-input, django-templates, forms, hidden-input, multiwidget]
- `tel.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, telephone-input]
- `text.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, text-input]
- `textarea.html` (Size: 145 bytes): Renders a `textarea` element with the widget's name and shared attributes. It renders the widget value only when that value is truthy. The value is placed between the opening and closing `textarea` tags. The template does not render a value for a falsey widget value.
  - Tags: [django-templates, forms, html, textarea]
- `time.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, time-input]
- `url.html` (Size: 48 bytes): Includes `input.html`. It delegates input element markup to the shared input template. The included template receives the current widget context. The file contains no additional element markup.
  - Tags: [django-templates, forms, url-input]

## Links Child Folder docmaps

None.

## Related Features

Django form widget rendering for scalar inputs, choices, files, dates and times, and compound or multi-value controls.

## Agent Guidance

### Read When

Changing HTML rendering for built-in Django form widgets or their shared template fragments.

### Modify When

The desired output is controlled by a widget template in this folder.

### Avoid Modifying When

The change is limited to widget Python behavior or project-specific admin wrappers rather than these shared form templates.

## TODO / FIXME / NOTE

No TODO, FIXME, or NOTE markers were found in these 31 files.

## Dependency Graph

Not generated. `dependencies` is empty; no dependencies were inferred.