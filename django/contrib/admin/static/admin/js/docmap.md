---
folder: "django/contrib/admin/static/admin/js"
generated_on: "2026-10-02"
num_files: 19
semantic_tags: [accessibility, admin, autocomplete, calendar, changelist, date-formatting, date-time, dom, forms, formsets, javascript, jquery, local-storage, localization, namespace, navigation, popup, prepopulation, related-objects, select2, selectbox, selectfilter, selection, session-storage, sidebar, slug, themes, transliteration, unicode, unsaved-changes, utilities]
todos_present: true
dependencies: []
---

# Folder Overview

## Purpose

This folder contains browser-side JavaScript for Django admin pages and their interactive controls. Its direct files implement changelist actions and filters, navigation, themes, form autofocus, inlines, autocomplete, date calendars, and selection widgets. Shared utilities support DOM updates, date formatting, URL slug generation, and jQuery isolation. The `admin/` child has a standalone docmap for date/time shortcuts and related-object popup workflows. Merged `admin/`: This folder contains admin JavaScript for date/time shortcuts and related-object lookups.

## Major Responsibilities

Manage admin form and changelist interactions, including selection, filtering, inline formsets, autocomplete, popups, and field widgets. Provide shared browser utilities and persisted navigation, filter, and theme state. Merged `admin/`: Provide date and time controls for admin form fields and synchronize related-object selection and popup workflows.

## Technology Notes

Uses JavaScript, native browser DOM and storage APIs, `django.jQuery`, Select2 integration, and XRegExp for Unicode-aware slug filtering. Merged `admin/`: JavaScript, browser DOM APIs, Django localization and formatting helpers, `django.jQuery`, and `SelectBox`.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `admin` : This folder contains admin JavaScript for date/time shortcuts and related-object lookups. The date/time module adds calendar and clock dialogs, quick selections, and timezone warnings to matching inputs. The related-object module coordinates popup workflows and updates connected form controls after lookup or add, change, or delete actions. The two modules support interactive Django admin forms. Provide date and time controls for admin form fields and synchronize related-object selection and popup workflows.

## Files
- `actions.js` (Size: 8,999 bytes): Implements changelist action selection and updates the selected-object counter. It supports selecting all rows, selecting across the queryset, clearing that selection, and shift-click ranges. It tracks edits to list-editable fields and prompts before actions or saves that could discard changes. Initialization waits for the DOM and the counter is refreshed when a page is restored.
  - Tags: [admin, changelist, javascript, selection, unsaved-changes]

- `admin/DateTimeShortcuts.js` (Size: 27,979 bytes): Provides shortcuts and timezone mismatch warnings for admin date and time inputs. On window load, it finds matching fields and adds localized quick links and modal calendar or clock dialogs. Calendar navigation, date selection, and keyboard movement are handled alongside formatting through Django's configured input formats. It uses `Calendar`, `CalendarNamespace`, Django localization and formatting helpers, and DOM utilities.
  - Tags: [admin, calendar, date-time, dom, javascript, localization, timezone]

- `admin/RelatedObjectLookups.js` (Size: 11,452 bytes): Implements related-object lookup and add, change, and delete popup workflows. It tracks popup windows and returns selected or changed records to raw-ID fields and select widgets. Popup callbacks update options, `SelectBox` caches, Select2 labels, related links, and emit jQuery events. It exposes backward-compatible Add Another aliases and integrates with `django.jQuery` and `SelectBox`.
  - Tags: [admin, javascript, jquery, popup, related-objects, selectbox, widgets]

- `autocomplete.js` (Size: 1,066 bytes): Adds a `djangoAdminSelect2` jQuery plugin for admin autocomplete controls. Its AJAX data includes the search term, page, and model and field identifiers from element data attributes. It initializes existing autocomplete widgets while excluding empty form templates. Newly added formsets receive the same initialization through the `formset:added` event.
  - Tags: [admin, autocomplete, javascript, jquery, select2]

- `calendar.js` (Size: 12,223 bytes): Provides localized month and weekday names, leap-year and month-length helpers, and date formatting. It adjusts the current date using the server timezone offset and renders an accessible calendar table with today and selected-day labels. Calendar day links call a supplied callback, while the `Calendar` instance supports month and year navigation. It exports `Calendar` and `CalendarNamespace` for use by other admin scripts.
  - Tags: [admin, calendar, date-time, javascript, localization]

- `cancel.js` (Size: 886 bytes): Binds click handlers to admin cancel links after the DOM is ready. The handler prevents the link's default navigation and checks the `_popup` query parameter. In a popup it closes the current window; otherwise it returns to the previous history entry. The script uses `URLSearchParams` to inspect the current location.
  - Tags: [admin, javascript, navigation, popup]

- `change_form.js` (Size: 677 bytes): Reads the model name from the admin add-form constants element. It locates that model's form and scans its controls in document order. The first enabled, rendered button, input, select, or textarea receives focus. It stops after focusing the first eligible control.
  - Tags: [admin, focus, forms, javascript]

- `core.js` (Size: 6,432 bytes): Defines shared DOM helpers for creating elements, removing children, and calculating element positions. It extends `Date` with numeric and localized date and time accessors, plus `strftime` formatting. Its `String.strptime` extension parses supported date formats and constructs dates in UTC, including the documented two-digit-year boundary. Calendar names are used when `CalendarNamespace` is available.
  - Tags: [date-formatting, dom, javascript, utilities]

- `filters.js` (Size: 1,099 bytes): Restores the open or closed state of admin filter details from `sessionStorage`. It matches stored state to current filter titles and ignores titles not present on the page. Toggle events update the in-memory state and save it back to storage. The stored key is `django.admin.filtersState`.
  - Tags: [admin, changelist, javascript, session-storage]

- `inlines.js` (Size: 17,747 bytes): Implements the jQuery formset plugin for adding and removing admin inline forms. It updates form indexes, total counts, and add/delete control visibility according to the configured minimum and maximum. Tabular and stacked formsets additionally initialize prepopulated fields, date shortcuts, and select filters for added rows. Formset changes are exposed through callbacks and custom events.
  - Tags: [admin, formsets, javascript, jquery]
  - TODO/FIXME/NOTE: `Note` at line 256

- `jquery.init.js` (Size: 349 bytes): Places the bundled jQuery instance in the `django.jQuery` namespace. It calls `noConflict(true)` to release both `$` and `jQuery` from that instance. This preserves any pre-existing values of the global names. The script documents that isolation as its purpose.
  - Tags: [javascript, jquery, namespace]

- `nav_sidebar.js` (Size: 3,208 bytes): Controls the admin navigation sidebar's expanded state and stores it in `localStorage`. It synchronizes the main content's shifted class and the sidebar's `aria-expanded` value with that state. Its quick filter matches sidebar link text case-insensitively, supports clearing with Escape, and indicates when there are no results. The filter value is persisted in `sessionStorage`, and initialization is exposed as `window.initSidebarQuickFilter`.
  - Tags: [admin, javascript, local-storage, navigation, session-storage, sidebar]

- `popup_response.js` (Size: 774 bytes): Reads the popup response data embedded in the page and dispatches it to the opener window. Change responses call the related-object change callback, and delete responses call the delete callback. Other actions use the add-related-object callback with the returned object and option-group data. The script supplies the current popup window to each callback.
  - Tags: [admin, javascript, popup, related-objects]

- `prepopulate.js` (Size: 1,575 bytes): Defines a jQuery plugin that fills a field from the values of its dependent fields. It joins nonempty dependency values and passes them to `URLify` with the configured length and Unicode options. Once a user changes the target field, the plugin stops overwriting it. Automatic population is bound to dependency keyup, change, and focus events only when the target starts empty.
  - Tags: [admin, javascript, jquery, slug]

- `prepopulate_init.js` (Size: 726 bytes): Reads prepopulated-field configuration from the admin constants element. It marks matching fields in empty inline forms so they can be initialized when those forms are added. For each configured field, it stores the dependency list and invokes the prepopulate plugin. The plugin receives dependency IDs, the maximum length, and the Unicode setting.
  - Tags: [admin, forms, javascript, prepopulation]

- `SelectBox.js` (Size: 6,942 bytes): Implements the `SelectBox` cache used to manage options in admin selection widgets. It can rebuild selects, filter options by all whitespace-separated search terms, and preserve option groups when rendering. Move and move-all operations transfer selected or cached options between boxes, sorting grouped choices by group and option text. The API also exposes cache checks, hidden-option counts, and select-all behavior.
  - Tags: [admin, javascript, selectbox, selection]

- `SelectFilter2.js` (Size: 19,374 bytes): Transforms multiple-select fields into an accessible interface for filtering and moving available and chosen options. It builds the labels, help text, search fields, action buttons, and selected-option warning display. Mouse, keyboard, filtering, and form-submit handlers operate through `SelectBox` and refresh the interface state. A load handler initializes standard and stacked select-filter widgets.
  - Tags: [accessibility, admin, javascript, selectfilter]

- `theme.js` (Size: 1,708 bytes): Applies the selected theme to the document and stores the mode in `localStorage`. It accepts light, dark, or automatic mode and resets invalid values to automatic mode. The theme toggle cycles through modes in an order based on the system color-scheme preference. Toggle buttons are connected on window load, and the stored theme is applied during initialization.
  - Tags: [admin, javascript, local-storage, themes]

- `urlify.js` (Size: 9,985 bytes): Converts text into URL-friendly slugs, with transliteration maps for Latin, Greek, Cyrillic, and other scripts. It lazily combines those maps into a lookup and regular expression used to downcode characters. In Unicode mode it uses XRegExp to retain Unicode letters and numbers; otherwise it removes characters outside the ASCII-oriented slug set. It lowercases text, normalizes spaces and dashes, limits the result to the requested length, and trims trailing hyphens.
  - Tags: [javascript, slug, transliteration, unicode]

## Links Child Folder docmaps

None.

## Related Features

Admin changelist workflows, forms and inline formsets, relationship selection and autocomplete, date and time entry, navigation, theme selection, and slug prepopulation. Merged `admin/`: Admin date/time widgets, timezone guidance, and related-object selection.

## Agent Guidance

### Read When

Changing admin browser interactions, widgets, navigation state, inline formsets, or shared JavaScript utilities. Merged `admin/`: Changing admin date/time shortcuts or related-object popup behavior.

### Modify When

The behavior is implemented in one of these admin JavaScript modules or in the `admin/` child docmap. Merged `admin/`: The requested behavior is implemented in either JavaScript module listed here.

### Avoid Modifying When

The change concerns server-side admin behavior or styling without corresponding browser-side logic in this folder. Merged `admin/`: The change concerns server-side admin behavior or unrelated admin styling.

## Dependency Graph

Not generated. `dependencies` is empty; no dependencies were inferred.