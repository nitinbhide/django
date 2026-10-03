---
folder: "django/contrib/admin/templates/admin"
generated_on: "2026-10-02"
num_files: 43
semantic_tags: [admin, authentication, django, django-template, django-templates, forms, html, inline-formsets, object-deletion, passwords, stacked-layout, summary, tabular-layout, templates, users, widgets]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains Django admin HTML templates for the main admin site and its model-oriented pages. The templates cover navigation, dashboards, authentication, forms, changelists, object history, and error responses. They extend shared admin layouts and render controls using Django template context, permissions, and internationalization. Separate standalone child indexes cover inline formsets, includes, widgets, and user-management templates. Merged `auth/`: This folder organizes Django admin authentication templates beneath a dedicated `auth` path and currently contains no eligible immediate files. Merged `edit_inline/`: This folder contains Django admin templates for rendering related inline formsets in two layouts. Merged `includes/`: This folder contains two Django admin templates for rendering form fieldsets and a model-count summary. Merged `widgets/`: This folder provides Django admin widget templates that compose shared form-widget templates with admin-specific wrappers and controls.

## Major Responsibilities

Provides the primary admin page layouts and reusable page-level controls for model operations. The templates render object lists and forms, apply permission-sensitive actions, and expose accessible navigation and status information. Merged `auth/`: Provide navigation for the admin authentication template area; the user-specific template implementation is maintained in the `user` child folder. Merged `auth/user/`: Customize the user creation form and render the admin password change or enable workflow. Merged `edit_inline/`: Render admin inline formsets in stacked and tabular layouts. Merged `includes/`: Render admin fieldsets and object deletion count summaries. Merged `widgets/`: Render admin-specific widget wrappers and controls for common and related-object form fields.

## Technology Notes

The files use Django's HTML template language, including template inheritance, blocks, filters, and tag libraries. Several templates use internationalization, static asset loading, CSRF tokens, or accessibility attributes. Merged `auth/`: No immediate files are present. The child index documents Django HTML templates using translation, static-asset, and admin form template tags. Merged `auth/user/`: Django templates, translation tags, static asset tags, and admin form components. Merged `edit_inline/`: Django templates, formsets, and admin fieldset includes. Merged `includes/`: Django templates, HTML form markup, and translation tags. Merged `widgets/`: Django templates, shared form widgets, admin static assets, and translation tags.

# Folder Navigation

## Merged Child Folders

`docmap.md` of following child folders are merged in this file.

- `auth/user` : This folder contains two Django admin templates for creating users and managing their passwords. `add_form.html` adjusts the user creation form with a notice and stylesheet. `change_password.html` renders the password-management form, navigation, and submission options. Both use Django template tags for translation and static assets. Customize the user creation form and render the admin password change or enable workflow.
- `auth` : This folder organizes Django admin authentication templates beneath a dedicated `auth` path and currently contains no eligible immediate files. Its `user` child contains the user creation and password-management templates, as described in that folder's standalone index. This index directs agents to the child instead of duplicating its file summaries. The documented templates use Django's template language and admin form components. Merged `user/`: This folder contains two Django admin templates for creating users and managing their passwords. Provide navigation for the admin authentication template area; the user-specific template implementation is maintained in the `user` child folder. Merged `user/`: Customize the user creation form and render the admin password change or enable workflow.
- `edit_inline` : This folder contains Django admin templates for rendering related inline formsets in two layouts. `stacked.html` arranges each inline form as a separate block and delegates field rendering to the admin fieldset include. `tabular.html` presents inline forms as rows beneath field-name headers and renders fields directly in table cells. Both templates include formset management and error output, optional collapsible sections, object and navigation links, and permission-gated deletion controls. Render admin inline formsets in stacked and tabular layouts.
- `includes` : This folder contains two Django admin templates for rendering form fieldsets and a model-count summary. `fieldset.html` lays out fieldset headings, descriptions, rows, and fields. `object_delete_summary.html` displays model names and object counts under a translated Summary heading. Together, they cover fieldset presentation and deletion-summary content. Render admin fieldsets and object deletion count summaries.
- `widgets` : This folder provides Django admin widget templates that compose shared form-widget templates with admin-specific wrappers and controls. Its nine entries cover file uploads, date and time inputs, URLs, radio and multiple inputs, and relation widgets. The relation templates add raw-ID lookup and permission-gated links for related objects. No child-folder entries are included. Render admin-specific widget wrappers and controls for common and related-object form fields.

## Files
- `404.html` (Size : 282 bytes): This template renders the admin site's not-found response. It extends `base_site.html` and loads internationalization tags. Its content supplies translated title and message blocks. No other page behavior is defined here.
    - Tags: [error, http-status, minimal, not-found, template]

- `500.html` (Size : 578 bytes): This template renders the admin site's server-error response. It extends `base_site.html` and includes breadcrumb navigation. Its translated message identifies the HTTP 500 error and gives a user-facing error-reporting notice. The page content is limited to this error presentation.
    - Tags: [error, http-status, notification, server-error, template]

- `actions.html` (Size : 1176 bytes): This template provides the bulk-action controls used with admin object lists. It defines blocks for the action form, submit control, and selection counter. The controls include labeled form fields and an `aria-live` region for selection feedback. It is a reusable template structure rather than a specific action implementation.
    - Tags: [accessibility, actions, bulk-operations, form, template]

- `app_index.html` (Size : 519 bytes): This template specializes the admin app-listing page by extending `index.html`. It supplies app-specific page context and breadcrumb presentation. Popup mode conditionally suppresses sidebar and breadcrumb blocks. The template also loads internationalization tags.
    - Tags: [admin-index, app-listing, navigation, overrides, template]

- `app_list.html` (Size : 2233 bytes): This template renders applications and their models as a table. It presents links for model operations according to the supplied context and permissions. ARIA table scopes and descriptions associate links with their corresponding model rows. The file focuses on the model-listing presentation.
    - Tags: [aria-labels, model-listing, permissions, table-layout, template]

- `auth/user/add_form.html` (Size: 405 bytes): Extends `admin/change_form.html` and loads translation and static-file tags. Its `form_top` block shows a translated note about additional user options when the page is not a popup. Its `extrahead` block preserves the parent content. It loads the unusable-password stylesheet with a CSP nonce.
  - Tags: [admin, authentication, css, django-template, users]

- `auth/user/change_password.html` (Size: 4,206 bytes): Extends `admin/base_site.html` and loads translation, static-file, admin URL, and admin filter tags. It sets an error-aware title, adds form stylesheets, and builds breadcrumbs for the user being edited. The form includes CSRF protection, error and help text, and usable-password, password, and confirmation controls. Its submit options change a password, enable password authentication, or disable it, depending on the user's current password state.
  - Tags: [admin, authentication, csrf, django-template, forms, passwords]

- `base.html` (Size : 6501 bytes): This file defines the shared HTML document and layout for the admin interface. It provides language and text-direction attributes, viewport metadata, and support for a CSP nonce. Blocks arrange the header, breadcrumbs, sidebar, and main content, with a skip-to-content link. It loads internationalization, static-file, and timezone template tags.
    - Tags: [base-layout, csp-nonce, dark-mode, internationalization, responsive]

- `base_site.html` (Size : 450 bytes): This template extends `base.html` with site-level branding and user tools. It renders the site header, logout form, documentation and password-change links, and the theme toggle. Its content customizes shared layout blocks for the admin site. It does not define the underlying page structure.
    - Tags: [branding, color-theme, site-header, template-extends, user-interface]

- `change_form.html` (Size : 3746 bytes): This template renders the admin page for adding or changing a model instance. It composes breadcrumbs, object tools, fieldsets, inline formsets, and submit controls. The template accommodates add, change, and popup contexts. It includes a CSP nonce for the page's form-related JavaScript.
    - Tags: [add-form, change-form, edit-page, fieldsets, forms, inline-formsets]

- `change_form_actions.html` (Size : 35 bytes): This template extends `actions.html` without adding blocks or markup. Its behavior is inherited from the parent action template. The file provides a named extension point for the change-form context. No independent action controls are defined.
    - Tags: [actions, extends-only, reusable-block, template]

- `change_form_object_tools.html` (Size : 403 bytes): This template renders object-level tools on a change form. It provides a history link and conditionally displays a view-on-site link when an absolute URL is available. It loads the admin URL tag library for link construction. No other tools are rendered here.
    - Tags: [navigation-links, object-tools, template]

- `change_list.html` (Size : 4442 bytes): This template renders the admin page for browsing model objects. Its components include filters, search, date hierarchy, bulk actions, results, and pagination. It handles formset and non-formset result modes and presents form errors where applicable. Conditional controls depend on the supplied changelist context.
    - Tags: [change-list, filtering, pagination, search, table-layout]

- `change_list_object_tools.html` (Size : 378 bytes): This template conditionally renders an add-object button for users with add permission. It preserves filter and popup state in the generated URL. The button is presented among changelist object tools. No other object-level controls are defined.
    - Tags: [add-button, conditional-rendering, permissions, template]

- `change_list_results.html` (Size : 1516 bytes): This template renders changelist results as a table. It includes hidden fields, column headings, and result rows. The headings support multi-column sorting and priority indicators. Per-row form errors are included when present in the context.
    - Tags: [sorting, table-results, template]

- `color_theme_toggle.html` (Size : 703 bytes): This template defines the admin color-theme toggle button. It includes automatic, light, and dark theme icons and visually hidden labels. The button markup supports accessible identification of each theme state. The SVG assets are embedded in the template.
    - Tags: [accessibility, button, dark-mode, inline-element, svg]

- `date_hierarchy.html` (Size : 617 bytes): This template renders date-based navigation for a changelist. It provides a link to a parent date level and choices for the current period. The navigation appears only when a date-hierarchy context value is available. Its links filter the displayed objects by date.
    - Tags: [date-filter, filtering, navigation, template]

- `delete_confirmation.html` (Size : 2819 bytes): This template presents confirmation for deleting an object. It distinguishes missing permission, protected related objects, and deletable objects. Related-object cascades can be displayed with optional truncation. The deletion form includes a CSRF token.
    - Tags: [confirmation, delete-operation, form-submission, permissions, template]

- `delete_selected_confirmation.html` (Size : 2458 bytes): This template presents confirmation for a bulk deletion. It handles permission and protected-object cases and iterates over selected objects. The form carries a hidden action field for the bulk operation. Its page structure parallels single-object deletion confirmation.
    - Tags: [bulk-deletion, confirmation, form-submission, template]

- `edit_inline/stacked.html` (Size: 3,108 bytes): Renders each inline form in its own block, with a heading that shows the related object or its form number. The form's fieldsets are rendered through `admin/includes/fieldset.html`, while management data, non-form errors, and required primary-key or foreign-key fields are included in the surrounding structure. Existing objects can link to their change or view page and to the site; deletion controls appear only when allowed. The fieldset can be collapsible, and an add-permitted final form receives the empty-form identifiers and classes.
  - Tags: [admin, django-template, fieldsets, inline-formsets, stacked-layout]

- `edit_inline/tabular.html` (Size: 4,436 bytes): Renders the inline formset as a table, with column headers derived from configured fields and indicators for required or hidden fields. Each form is represented by a row; field cells render read-only contents or editable fields with their errors, and a separate row can display non-field errors. Existing-object, change/view, and site links appear in the original-object cell, alongside required primary-key or foreign-key fields. The template also supports collapsible sections, help-text tooltips, empty-form rows, and deletion controls gated by formset and user permissions.
  - Tags: [admin, django-template, inline-formsets, permissions, table-rows, tabular-layout]

- `filter.html` (Size : 395 bytes): This template renders one changelist filter group. It places the filter title and choice links inside a collapsible fieldset. The current choice receives a selected class, and link values are encoded as IRIs. It does not implement filter evaluation.
    - Tags: [collapsible-section, filter-item, links, template]

- `includes/fieldset.html` (Size: 3,044 bytes): Renders an aligned admin fieldset from its name, description, and iterable rows and fields. It conditionally adds a heading and makes named fieldsets collapsible when configured. Rows and fields account for labels, help text, errors, hidden fields, checkboxes, read-only content, and nested fieldsets. It preserves fieldset IDs, CSS classes, and ARIA associations when those values are available.
  - Tags: [admin, django-template, forms, html, template]

- `includes/object_delete_summary.html` (Size: 192 bytes): Renders a translated Summary heading followed by an unordered list. It iterates over `model_count` as model-name and object-count pairs. Each list item capitalizes the model name and displays its count. Each item is an `<li>` within the list.
  - Tags: [admin, django-template, html, internationalization, object-deletion, summary, template]

- `index.html` (Size : 2170 bytes): This template renders the admin dashboard and extends `base_site.html`. It displays the application list and a recent-action sidebar. The log template tags provide action history for the current user. Dashboard styling is loaded for this page.
    - Tags: [dashboard, log-display, recent-actions, sidebar, template]

- `invalid_setup.html` (Size : 474 bytes): This template displays an admin error page for database setup problems. It extends the shared site layout and includes breadcrumb context. Its translated message describes missing tables or an inaccessible database. It presents the setup issue rather than performing database checks.
    - Tags: [database-error, error-page, setup-issue, template]

- `login.html` (Size : 2037 bytes): This template renders the admin login page. It displays authentication errors, username and password fields, and a password-reset link. It also handles an already-authenticated warning and suppresses user tools and global navigation. Form submission behavior is supplied through the template context and Django form rendering.
    - Tags: [authentication, csrf, form-submission, login-form, template]

- `nav_sidebar.html` (Size : 486 bytes): This template renders the admin navigation sidebar. It includes a search-filter input, application list, and sidebar toggle control. The sidebar is presented as a persistent navigation region. Filtering behavior is outside this template's markup.
    - Tags: [navigation, search-filter, sidebar, sticky-element, template]

- `object_history.html` (Size : 2406 bytes): This template renders an object's change history in a table. Columns present the timestamp, user, and action for each entry. The view supports pagination over a maximum of 100 history entries. Entries can link to their related admin pages.
    - Tags: [history-log, pagination, table-layout, template]

- `pagination.html` (Size : 654 bytes): This template renders navigation for paged admin results. It includes page links, a result count, and an optional show-all link. The paginator is conditionally displayed when pagination is required. Page selection is driven by the provided context.
    - Tags: [navigation, pagination, template]

- `popup_response.html` (Size : 360 bytes): This template produces a minimal HTML document for an admin popup response. It loads `popup_response.js` and supplies response data encoded as base64. The document contains only the structure needed for this script handoff. It does not implement the popup response handling itself.
    - Tags: [javascript-initialization, minimal-document, popup-handler, template]

- `prepopulated_fields_js.html` (Size : 238 bytes): This template emits a script element that initializes prepopulated fields. It loads `prepopulate_init.js` and passes the field mapping as JSON. The mapping is rendered from the supplied template context. Initialization logic resides in the referenced JavaScript asset.
    - Tags: [javascript-initialization, prepopulation, script-tag, template]

- `search_form.html` (Size : 1559 bytes): This template renders the changelist search toolbar. It includes a text input, submit button, result count, and preserved query parameters. Help text and full or partial result counts are conditional. Search execution is handled outside the template.
    - Tags: [search-input, template, toolbar, ui-component]

- `submit_line.html` (Size : 1121 bytes): This template renders the model-form submission controls. It includes save, save-as-new, save-and-add-another, save-and-continue, close, and delete actions. The available controls depend on permissions and page context. The template lays out actions but does not implement their server-side behavior.
    - Tags: [button-row, form-actions, permissions, template]

- `widgets/clearable_file_input.html` (Size: 666 bytes): Shows the initial file value as a link when present and conditionally displays the configured input label. For optional fields, it renders a clear checkbox using the supplied name, ID, label, disabled state, and checked state. The file input itself is always rendered. Its attributes come from the shared `django/forms/widgets/attrs.html` template.
  - Tags: [admin, file-upload, forms, template, widget]

- `widgets/date.html` (Size: 71 bytes): Wraps the shared date widget in a paragraph with the `date` CSS class. It delegates date-control rendering to `django/forms/widgets/date.html`. The wrapper provides an admin-facing styling hook. It contains no additional widget-specific conditions.
  - Tags: [admin, date, forms, template, widget]

- `widgets/foreign_key_raw_id.html` (Size: 412 bytes): Renders the shared forms input and optionally surrounds it with a container when a related-object URL is available. That URL enables a related-lookup link whose ID is derived from the widget name. An optional related-object label is linked when a link URL exists and otherwise shown as plain text. The lookup and related-object links are conditionally rendered from their supplied context values.
  - Tags: [admin, foreign-key, forms, lookup, relations, template, widget]

- `widgets/many_to_many_raw_id.html` (Size: 54 bytes): Includes the admin foreign-key raw-ID template rather than defining separate markup. This reuses its input, lookup, and optional related-object label behavior. The template itself adds no conditions. It defines no additional elements.
  - Tags: [admin, many-to-many, relations, template, widget]

- `widgets/radio.html` (Size: 57 bytes): Includes the shared `django/forms/widgets/multiple_input.html` template. It delegates option rendering to that forms widget implementation. The admin template adds no markup of its own. It contains no admin-specific presentation logic.
  - Tags: [admin, multiple-input, radio, template, widget]

- `widgets/related_widget_wrapper.html` (Size: 2,102 bytes): Wraps the rendered widget in a related-widget container and adds a model reference unless choices are limited. When the widget is visible, it conditionally renders change, add, delete, and view links according to the supplied permission flags. The links use provided URLs or URL templates, widget-derived IDs, and translated titles. Their icons are loaded from Django admin's static assets.
  - Tags: [admin, permissions, related-objects, template, widget]

- `widgets/split_datetime.html` (Size: 420 bytes): Renders separate date and time labels around the two datetime subwidgets. Each label targets its subwidget's ID when the parent widget has an ID. Each control is rendered through its own `template_name`. The two controls are separated by a line break inside a `datetime` paragraph.
  - Tags: [admin, datetime, forms, template, widget]

- `widgets/time.html` (Size: 71 bytes): Wraps the shared time widget in a paragraph with the `time` CSS class. It delegates time-control rendering to `django/forms/widgets/time.html`. The wrapper provides an admin-facing styling hook. It contains no additional widget-specific conditions.
  - Tags: [admin, forms, template, time, widget]

- `widgets/url.html` (Size: 218 bytes): When the URL is valid, displays the current value as a link and the configured change label before the input. It always includes the shared `django/forms/widgets/input.html` template. The valid-URL condition also controls the surrounding paragraph and its `url` CSS class. The change label is not shown for an invalid URL.
  - Tags: [admin, forms, input, template, url, widget]

## Links Child Folder docmaps

# Related Features

The indexed templates cover Django admin navigation, dashboards, authentication, model add/change and list pages, deletion confirmation, history, filtering, pagination, and user-facing error pages. The child indexes cover inline formsets, shared includes, widgets, and user-management pages. Merged `auth/`: Admin user creation and password management. Merged `auth/user/`: Admin user creation and password management. Merged `edit_inline/`: Django admin inline formsets and their stacked and tabular presentations. Merged `includes/`: Admin fieldset rendering and object deletion summaries. Merged `widgets/`: Admin file, date/time, URL, selection, and related-object widgets.

# Agent Guidance

## Read When

Changing or investigating the HTML presentation of Django admin pages, model forms and lists, navigation, or page-level controls. Merged `auth/`: Locating templates for Django admin authentication screens, especially user creation or password management. Merged `auth/user/`: Changing the Django admin user creation or password-management screens. Merged `edit_inline/`: Changing the layout or controls for admin inline forms. Merged `includes/`: Changing admin fieldset display or delete-confirmation summaries. Merged `widgets/`: Changing admin widget rendering or related-object controls.

## Modify When

The requested change concerns admin template rendering, inheritance blocks, accessible markup, or conditional presentation based on admin context. Merged `auth/`: The requested change concerns navigation or template organization for the admin authentication area; modify the specific user templates in `user/` when their rendered behavior needs to change. Merged `auth/user/`: The requested change concerns these user authentication templates or their rendered controls. Merged `edit_inline/`: The requested behavior is implemented by either inline formset template. Merged `includes/`: The requested presentation is rendered by either include template. Merged `widgets/`: The requested presentation is implemented by one of these widget templates.

## Avoid Modifying When

The change concerns server-side admin behavior or static JavaScript behavior without a template-rendering requirement. Merged `auth/`: The change concerns authentication logic or admin templates outside this folder. Merged `auth/user/`: The change concerns authentication logic outside these presentation templates. Merged `edit_inline/`: Changing formset validation or model relationship behavior. Merged `includes/`: Changing field validation or deletion behavior outside template rendering. Merged `widgets/`: Changing underlying widget Python behavior or form validation.
