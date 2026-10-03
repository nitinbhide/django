---
folder: "django/contrib/admin/static/admin/css"
generated_on: "2026-10-02"
num_files: 13
semantic_tags: [admin, autocomplete, css, dark-mode, forms, responsive, rtl, widgets]
todos_present: false
dependencies: []
---

# Folder Overview

## Purpose

This folder contains the 13 direct CSS stylesheets listed below for the Django admin interface. The styles cover shared presentation and specialized screens or controls, including changelists, dashboard, login, forms, navigation, widgets, and autocomplete. Separate files provide dark-theme variables, right-to-left adjustments, and tablet and mobile overrides. The stylesheets use shared custom properties, component selectors, and media queries.

## Major Responsibilities

Shared admin styling; page and widget presentation; theme and direction variants; responsive rules.

## Technology Notes

CSS custom properties, media queries, and pseudo-classes including `:has()`.

# Folder Navigation

## Merged Child Folders

None.

## Files

- `autocomplete.css` (Size: 9,583 bytes): Styles Django admin's Select2 autocomplete control through `.select2-container--admin-autocomplete` selectors. Rules cover single and multiple selections, selected chips, clear and search fields, grouped results, and highlighted options. Focus, open, disabled, above/below dropdown states, error borders, and RTL direction receive separate styling. Dimensions, colors, borders, and text largely use admin CSS custom properties, with a 200px results viewport.
  - Tags: [admin, autocomplete, css, select2, widgets]
- `base.css` (Size: 24,514 bytes): Defines light-theme CSS custom properties on `:root` and `html[data-theme="light"]`, then applies shared page and typography defaults. It styles links, headings, prose, tables, sorting controls, form inputs and buttons, modules, messages, errors, breadcrumbs, action icons, and object tools. It also sets page structure, change-history presentation, and skip-to-content positioning. Many component colors reference shared variables, while some colors and backgrounds are literal.
  - Tags: [admin, css, global-styles, layout, theme]
- `changelists.css` (Size: 6,216 bytes): Styles the admin changelist form area as a flex layout, including filtered and unfiltered widths, results tables, the footer, and pagination. Rules cover the search toolbar, filter column, collapsible filter headings, selected filter values, and date drill-down links. Table headers, action checkboxes, footers, and selected rows receive dedicated presentation. Forced-colors rules outline filters and preserve selected-row contrast, while `:has()` detects checked action controls.
  - Tags: [admin, changelist, css, filters, tables]
- `dark_mode.css` (Size: 3,583 bytes): Defines dark color variables for both the `prefers-color-scheme: dark` condition and the explicit `html[data-theme="dark"]` state. The variables cover page and text colors, links, borders, errors, messages, selected rows, and close buttons. Both dark-mode blocks set `color-scheme: dark`. Theme-toggle rules show the label and SVG icon matching the `auto`, `dark`, or `light` theme state.
  - Tags: [admin, color-scheme, css, dark-mode, theme]
- `dashboard.css` (Size: 442 bytes): Styles table cells within the admin dashboard to break long words. Dashboard module table headings occupy the full available width, while cells keep their contents on one line. Links in those cells display as blocks with right padding. Recent action list items have no bullets and truncate overflowing text with an ellipsis.
  - Tags: [admin, css, dashboard, recent-actions, tables]
- `forms.css` (Size: 7,951 bytes): Defines form-row spacing, checkbox alignment, selected option colors, and flex layouts for form content. It styles labels, radio lists, aligned and collapsible fieldsets, help text, monospace textareas, and submit rows. The file sets dimensions and spacing for date, time, text, URL, UUID, and ID fields, and styles inline and tabular forms. It also formats related-object lookup links, file inputs, and inline add-row controls.
  - Tags: [admin, css, forms, inlines, widgets]
- `login.css` (Size: 951 bytes): Applies login-specific backgrounds and layout to the admin header, content, and container. The header title is centered, and the container uses a fixed width with a minimum width, border, rounded corners, and vertical margin. Username and password inputs fill their row, use border-box sizing, and receive additional padding. Form labels display as blocks, while the submit row and password-reset link are centered.
  - Tags: [admin, css, forms, login]
- `nav_sidebar.css` (Size: 2,814 bytes): Defines sticky positioning and viewport height limits for the sidebar. The navigation toggle and `#nav-sidebar` use flex sizing, off-canvas positioning, and visibility changes when `.main.shifted` is present. RTL rules switch border and positioning sides, and current app and model entries receive distinct highlighting. At widths up to 767px, the sidebar and toggle are hidden, content fills the available width, and the navigation filter receives its own input styling.
  - Tags: [admin, css, navigation, sidebar]
- `responsive.css` (Size: 15,019 bytes): Contains tablet rules at `max-width: 1024px` and mobile rules at `max-width: 767px`, beginning with default appearance adjustments for submit inputs and buttons. Tablet rules adjust page sizing, headers, dashboard columns, changelist search and filters, form controls, selectors, messages, login, maps, and documentation tables. Mobile rules stack changelist layout, forms, selectors, inline formsets, and submit actions while adapting login, calendars, and history tables. Other rules adjust control padding and text sizes, inline-group overflow, and calendar and clock dialog positioning.
  - Tags: [admin, css, mobile, responsive-design, tablets]
- `responsive_rtl.css` (Size: 1,821 bytes): Adds RTL overrides within tablet (`max-width: 1024px`) and mobile (`max-width: 767px`) media queries. Tablet overrides adjust margins and alignment for user tools, action controls, changelist regions, dashboard links, inline add links, and message icons. Mobile rules adjust filter and checkbox spacing, selector button backgrounds, and message padding and icon placement. Most overrides are scoped to `[dir="rtl"]`.
  - Tags: [admin, css, responsive-design, rtl]
- `rtl.css` (Size: 3,726 bytes): Overrides global admin alignment for RTL pages, including table headings, lists, action icons, object tools, and page columns. It repositions user tools, breadcrumbs, main and related content, changelist filters, and pagination. Form lists, submit alignment, selector controls, related widgets, calendar navigation, and inline delete controls also switch direction. Message-list padding and icon positions move to the right, with related floats and margins switched.
  - Tags: [admin, css, layout, rtl]
- `unusable_password_field.css` (Size: 667 bytes): Uses `:has()` to condition visibility of admin user-password form elements on the checked usable-password choice. When the `true` option is checked, it hides the message list and the unset-password submit button. When the `false` option is checked, it hides the password field wrappers and the set-password submit button. The selectors target `#id_usable_password` inputs with the literal values `true` and `false`.
  - Tags: [admin, css, forms, password]
- `widgets.css` (Size: 11,991 bytes): Styles the dual-list selector used to move options between available and chosen lists, including its stacked variant. It formats filtering controls, select lists, chooser buttons, search and help icons, and the chosen-list footer. Other rules cover date and time shortcuts, timezone warnings, URL and file upload text, calendars, clocks, and inline delete controls. The related-widget wrapper uses flex layout, and `.dj_map` is assigned fixed dimensions of 600 by 400 pixels.
  - Tags: [admin, calendar, css, selectors, widgets]

## Links Child Folder docmaps

None.

## Related Features

Django admin changelists, dashboard, login, forms, navigation, widgets, autocomplete, themes, and responsive and RTL presentation.

## Agent Guidance

### Read When

Changing visual presentation for the Django admin pages or controls covered above, or investigating their theme, responsive, or RTL styles.

### Modify When

A presentation change concerns one of the components or states described in the corresponding stylesheet entry.

### Avoid Modifying When

The requested change concerns behavior rather than presentation and none of these stylesheets controls the relevant visual state.

## Dependency Graph

Not generated. `dependencies` is empty; no dependencies were inferred.