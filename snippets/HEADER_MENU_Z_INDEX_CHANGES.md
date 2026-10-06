# Header Menu Z-Index Fix Documentation

This document outlines the modifications made to [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid) to guarantee that all header navigation elements (including desktop navigation, mega menu dropdowns, submenus, mobile drawers, and scroll containers) reliably stack above the floating Messenger and WhatsApp side tabs.

---

## 1. Problem Overview

### Affected Floating Widgets
- **Messenger Side Tab** ([`snippets/messenger_widget/messengerSideTab.liquid`](file:///home/fahad/Projects/shopify/snippets/messenger_widget/messengerSideTab.liquid)):
  Configured with fixed positioning and `z-index: 999;`.
- **WhatsApp Side Tab** ([`snippets/whatsApp_widget/whatsAppSideTab.liquid`](file:///home/fahad/Projects/shopify/snippets/whatsApp_widget/whatsAppSideTab.liquid)):
  Configured with fixed positioning and `z-index: 999;`.
- **WhatsApp & Messenger Bubbles/Tooltips** ([`snippets/whatsApp_widget/whatsAppWidget.liquid`](file:///home/fahad/Projects/shopify/snippets/whatsApp_widget/whatsAppWidget.liquid)):
  Configured with `z-index: {{ section.settings.z_index }}` (defaults to `999`–`1000`).

### Root Causes
1. **Low Layer Variable Default**: The mega menu and dropdown submenus in `_header_menu.liquid` originally used `z-index: var(--layer-header-menu);`. In Shopify themes (Horizon/Dawn), `--layer-header-menu` defaults to low values (typically `3` or unassigned `0`). Because `999 > 3`, the side tabs were displayed on top of the dropdown menus.
2. **Missing Component Stacking Context**: The desktop `<header-menu>` container had no explicit `z-index` or `position: relative`.
3. **Parent Stacking Context Trapping**: Header rows (`.header__row`) and `#header-component` elevate only to `--layer-heightened` (typically `2`). If a parent container has a lower `z-index` than a sibling fixed widget (`999`), children inside the header cannot break out of that stacking context without elevating the parent container.

---

## 2. Detailed Changes Made

### Change 1: Elevated CSS Layer Variable in `{% style %}`
- **File**: [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid)
- **Lines Changed**: Lines 227–231
- **Code Before**:
  ```liquid
  {% style %}
    .header__underlay {
      --color-submenu: rgb({{effective_submenu_color.rgb}});
    }
  {% endstyle %}
  ```
- **Code After**:
  ```liquid
  {% style %}
    :root {
      --layer-header-menu: 9999;
    }

    .header__underlay {
      --color-submenu: rgb({{effective_submenu_color.rgb}});
    }
  {% endstyle %}
  ```
- **Reason**:
  Inline `{% style %}` renders directly into the HTML document root. Setting `--layer-header-menu: 9999` ensures any theme component that calculates z-index relative to the menu layer (such as currency/language dropdown wrappers using `calc(var(--layer-header-menu) + 1)`) automatically scales above `999`.

---

### Change 2: Root Variable & Parent Container Stacking Contexts in `{% stylesheet %}`
- **File**: [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid)
- **Lines Changed**: Lines 236–249
- **Code Before**:
  ```css
  {% stylesheet %}
    .header__drawer {
  ```
- **Code After**:
  ```css
  {% stylesheet %}
    :root {
      --layer-header-menu: 9999;
    }

    .header-section:has(.header-menu),
    .header-section:has(.header__drawer),
    #header-component:has(.header-menu),
    #header-component:has(.header__drawer),
    .header__row:has(.header-menu),
    .header__row:has(.menu-list__submenu) {
      z-index: 9999 !important;
    }

    .header__drawer {
  ```
- **Reason**:
  In CSS, child elements are bound by the stacking context of their positioned ancestors. If `#header-component` or `.header__row` has `z-index: 2`, any child element inside it will appear behind a fixed element with `z-index: 999`. Target selectors using `:has()` elevate the entire header container to `9999 !important` whenever a menu or drawer is present.

---

### Change 3: Submenu Base Rule & Overflow Part Z-Index
- **File**: [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid)
- **Lines Changed**: Lines 480–487
- **Code Before**:
  ```css
    /** mega menu **/
    .menu-list__submenu,
    .overflow-menu::part(overflow) {
      --submenu-padding-block-start: var(--padding-3xl);
      --submenu-padding-block-end: var(--padding-3xl);

      background-color: transparent;
    }
  ```
- **Code After**:
  ```css
    /** mega menu **/
    .menu-list__submenu,
    .overflow-menu::part(overflow) {
      --submenu-padding-block-start: var(--padding-3xl);
      --submenu-padding-block-end: var(--padding-3xl);

      background-color: transparent;
      z-index: 9999 !important;
    }
  ```
- **Reason**:
  Ensures the base declaration for dropdown containers and the overflow menu shadow part explicitly enforce `z-index: 9999 !important`.

---

### Change 4: Mega Menu Dropdown Absolute Overlay Z-Index
- **File**: [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid)
- **Lines Changed**: Lines 506–515
- **Code Before**:
  ```css
      visibility: hidden;
      position: absolute;
      width: 100%;
      inset-inline-start: 0;
      top: calc(100% - 1px + var(--border-bottom-width) - (var(--full-open-header-height) - var(--submenu-height)));
      z-index: var(--layer-header-menu);
      padding-inline: var(--padding-inline);
      clip-path: rect(var(--submenu-clip-top) 100% var(--full-open-header-height) 0);
  ```
- **Code After**:
  ```css
      visibility: hidden;
      position: absolute;
      width: 100%;
      inset-inline-start: 0;
      top: calc(100% - 1px + var(--border-bottom-width) - (var(--full-open-header-height) - var(--submenu-height)));
      z-index: 9999 !important;
      padding-inline: var(--padding-inline);
      clip-path: rect(var(--submenu-clip-top) 100% var(--full-open-header-height) 0);
  ```
- **Reason**:
  Replaces `var(--layer-header-menu)` (which resolved to a low number or fallback 0) with `9999 !important`, forcing the dropdown to render over `z-index: 999`.

---

### Change 5: Desktop Header Menu Component Z-Index
- **File**: [`snippets/_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid)
- **Lines Changed**: Lines 622–626
- **Code Before**:
  ```css
    .header-menu {
      height: 100%;
    }
  ```
- **Code After**:
  ```css
    .header-menu {
      position: relative;
      height: 100%;
      z-index: 9999 !important;
    }
  ```
- **Reason**:
  Provides a positioned stacking context on the `<header-menu>` custom element so that all top-level menu triggers and inner navigation items are rendered at layer `9999`.

---

## 3. How to Reproduce and Verify Manually

### Step A: Reproduce the Original Overlapping Bug
1. Restore `_header_menu.liquid` lines 506–515 to use `z-index: var(--layer-header-menu);` and remove `z-index` from `.header-menu`.
2. Open a storefront page with both:
   - The WhatsApp or Messenger side tab enabled (fixed at the left or right edge at `top: 50%`, `z-index: 999`).
   - A multi-tier navigation link with a mega menu or submenu.
3. Hover over or click the menu link to expand the mega menu.
4. **Observed Failure**: The WhatsApp / Messenger tab remains visible on top of the menu dropdown content, obscuring links and images.

### Step B: Verify the Fix
1. Apply the changes in [`_header_menu.liquid`](file:///home/fahad/Projects/shopify/snippets/_header_menu.liquid).
2. Reload the page and hover over the header navigation item to open the mega menu.
3. **Observed Success**:
   - The menu dropdown completely overlays the WhatsApp and Messenger side tabs.
   - On mobile devices, opening the header drawer or navigation bar menu also stacks completely above the side tabs.
4. Open browser DevTools (Inspect Element):
   - Check `.menu-list__submenu`: computed `z-index` must be `9999`.
   - Check `.header-menu`: computed `z-index` must be `9999`.
   - Check `.messenger-sidetab` / `.whatsapp-sidetab`: computed `z-index` is `999`.
