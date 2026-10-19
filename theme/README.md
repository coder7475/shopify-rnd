# Shopify Theme Code & Customizations

> Production-ready Liquid snippets, section overrides, settings schemas, and standalone blocks built for the [Naza Noor](https://nazanoor.com) store (Horizon 4.2.0 / Online Store 2.0).

[![Shopify CLI](https://img.shields.io/badge/Shopify_CLI-v3.x-95BF47?logo=shopify&logoColor=white)](https://shopify.dev/docs/apps/tools/cli)
[![Theme Architecture](https://img.shields.io/badge/Architecture-Online_Store_2.0-blue)](https://shopify.dev/docs/themes/architecture)
[![Base Theme](https://img.shields.io/badge/Base_Theme-Horizon_4.2.0-orange)](https://themes.shopify.com)
[![Dependencies](https://img.shields.io/badge/Dependencies-Zero_External_Apps-brightgreen)](#why-this-exists)

---

## Why This Exists

Most Shopify merchants rely on third-party App Store plugins for floating chat widgets, mobile logo switches, and product sliders. However, third-party apps frequently inject:
- Uncached JavaScript bundles (200kB–1MB+), slowing down Largest Contentful Paint (LCP) and Interaction to Next Paint (INP).
- External tracking scripts and iframes that cause Cumulative Layout Shift (CLS).
- Monthly recurring app subscriptions ($5–$30/mo per widget).

This directory provides **clean, zero-dependency Liquid, CSS, and vanilla Web Components** that integrate directly into your theme's native asset pipeline, delivering native speed and full visual control.

---

## 📂 File Architecture

The directory tree mirrors standard Shopify theme structure so files can be dropped directly into your repository:

```
theme/
├── blocks/
│   └── new_arrivals.liquid             # Autoplay product carousel block (Custom Element)
├── config/
│   └── settings_schema.json            # Theme settings schema (Mobile logo, logo heights)
├── sections/
│   └── header.liquid                   # Header section with desktop & mobile logo rendering
└── snippets/
    ├── _header-logo.liquid             # Sub-snippet rendering responsive logo images
    ├── _header_menu.liquid             # Header navigation menu with z-index protection
    ├── logo.liquid                     # Standalone logo SVG / image renderer
    ├── order_on_whatsapp.liquid        # Product detail page WhatsApp quick-order button
    ├── add-messenger-button/           # Custom Liquid block: Messenger checkout trigger
    │   ├── Button.css
    │   └── custom_liquid_block.liquid
    ├── add-whatsapp-button/            # Custom Liquid block: WhatsApp direct-order trigger
    │   ├── Button.css
    │   └── custom_liquid_block.liquid
    ├── messenger-widget/               # Floating Messenger bubble & side-tab widget
    │   ├── messengerSideTab.liquid
    │   └── messengerWidget.liquid
    └── whatsapp-widget/                # Floating WhatsApp bubble & side-tab widget
        ├── whatsAppSideTab.liquid
        └── whatsAppWidget.liquid
```

> **Important**: This folder contains targeted customizations, not an entire theme repository. File names and directory paths match standard Online Store 2.0 conventions so you can merge or copy them into your active theme without breaking `{% render %}` or `{% section %}` references.

---

## ⚡ Quick Start: Integrating into Your Theme

### Prerequisites
- **Shopify CLI**: Version 3.48+ (`shopify version`)
- **Theme Baseline**: Online Store 2.0 compatible theme (tested on Horizon 4.2.0 and Dawn)
- **Permissions**: Staff access with *Themes* write permissions or Partner access

### Step 1: Start a Theme Development Server
Pull your current live or staging theme to test locally:
```bash
# Authenticate and pull the theme
shopify theme pull --store your-store.myshopify.com

# Start the local hot-reloading development preview
shopify theme dev --store your-store.myshopify.com
```

### Step 2: Copy Desired Components
Copy only the components you need into your theme's root directory:
```bash
# Example: Deploying the New Arrivals block
cp theme/blocks/new_arrivals.liquid /path/to/your-theme/blocks/

# Example: Deploying the WhatsApp floating widget
cp -r theme/snippets/whatsapp-widget /path/to/your-theme/snippets/
```

### Step 3: Render or Mount in Theme Templates
Follow the component instructions below to wire up settings and Liquid tags.

---

## 🧩 Component Implementation Reference

### 1. Dual Desktop / Mobile Logo (`header.liquid` + `settings_schema.json`)
Allows merchants to upload two distinct logos in the Shopify Theme Customizer: a detailed wide logo for desktop and a compact icon or wordmark for mobile screens.

#### Theme Settings Integration
In `config/settings_schema.json`, the `mobile_logo` field is registered under the `logo_and_favicon` section:
```json
{
  "type": "image_picker",
  "id": "mobile_logo",
  "label": "Mobile Logo"
}
```

#### Liquid Template Usage
In `theme/sections/header.liquid` or `theme/snippets/_header-logo.liquid`:
```liquid
{% if settings.mobile_logo != blank %}
  <div class="header__logo-mobile medium-hide large-up-hide">
    <img
      src="{{ settings.mobile_logo | image_url: height: settings.logo_height }}"
      alt="{{ shop.name | escape }}"
      loading="eager"
      width="{{ settings.mobile_logo.width }}"
      height="{{ settings.logo_height }}"
    >
  </div>
{% endif %}
```
* **Full Guide**: [Horizon Dual Logo Guide](../docs/theme/horizon-dual-logo-guide.md) · [Mobile Logo Guide](../docs/theme/mobile-logo-guide.md)

---

### 2. Autoplay New Arrivals Carousel (`blocks/new_arrivals.liquid`)
A standalone theme block built using native Web Components (`customElements.define('product-carousel-...')`). Supports touch gestures, pause-on-hover, customizable autoplay intervals, and responsive desktop/mobile column counts.

#### Features
- **Zero Third-Party Libraries**: No Swiper.js or Slick Carousel dependency.
- **Responsive Layout**: Configurable 2–6 columns on desktop, 1–2 columns on mobile.
- **Accessible & Touch-Optimized**: Touch-drag gesture listeners with physics damping at boundary edges.

#### How to Add to a Section
Place `new_arrivals.liquid` in your theme's `blocks/` directory. Add it as an available block in any section schema:
```json
{
  "blocks": [
    {
      "type": "new_arrivals"
    }
  ]
}
```
Or insert it directly via the Shopify Theme Editor under sections that accept app or custom blocks.

---

### 3. Floating Chat Widgets (`whatsapp-widget` & `messenger-widget`)
Floating conversation widgets providing immediate direct-to-merchant communication via WhatsApp or Facebook Messenger.

#### Integration Method
Include the snippet before the closing `</body>` tag in `layout/theme.liquid`:
```liquid
{% comment %} Render WhatsApp Floating Widget {% endcomment %}
{% render 'whatsAppWidget' %}

{% comment %} Or Render Side Tab Variant {% endcomment %}
{% render 'whatsAppSideTab' %}
```

#### Z-Index Protection
Floating chat widgets use a configurable `z_index` setting. To ensure header mega-menus stay above floating chat buttons, the header snippet in `theme/snippets/_header_menu.liquid` applies an explicit stacking context:
```css
/* Keeps mega menus above chat tabs */
.header__menu-wrapper {
  z-index: 1000;
  position: relative;
}
```
* **Full Guide**: [Header Menu Z-Index Fix](../docs/theme/header-menu-z-index.md) · [Multi-Channel Chat Apps](../docs/support/multi-channel-chat-apps.md)

---

### 4. Direct-to-Chat Buy Buttons (`add-whatsapp-button` & `add-messenger-button`)
Custom Liquid blocks designed for product detail pages (PDP) to enable "Order via WhatsApp" or "Inquire on Messenger" with pre-filled product titles and URLs.

#### Liquid Snippet Example
```liquid
{% render 'order_on_whatsapp',
   phone_number: '1234567890',
   custom_message: 'Hi, I would like to order {{ product.title }} (SKU: {{ product.selected_or_first_available_variant.sku }})'
%}
```

---

## 📋 Quality Assurance & Verification Checklist

Before publishing theme updates to production, verify the following:

- [ ] **Desktop & Mobile Logo Rendering**: Verify desktop displays `settings.logo` and mobile (viewport < 750px) displays `settings.mobile_logo`.
- [ ] **Lighthouse Performance Score**: Ensure mobile performance score is ≥ 90; check that images have explicit `width` and `height` attributes to prevent CLS.
- [ ] **Z-Index Layering**: Open the desktop mega-menu navigation and ensure it renders over the WhatsApp/Messenger floating widget without clipping.
- [ ] **Touch Drag on Carousel**: Verify smooth horizontal swiping on physical mobile devices without unintended page scrolling.
- [ ] **Chat Link Encoding**: Verify that clicking the WhatsApp or Messenger button correctly URI-encodes the product title and links directly to the chat app.

---

## 🔗 Related Documentation

- [Root Repository README](../README.md)
- [Complete Documentation Index](../docs/README.md)
- [Horizon Dual Logo Guide](../docs/theme/horizon-dual-logo-guide.md)
- [Header Z-Index Resolution](../docs/theme/header-menu-z-index.md)
- [Customer Support & Chat Apps R&D](../docs/support/multi-channel-chat-apps.md)
