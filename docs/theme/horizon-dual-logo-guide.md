# Guideline: Implementing Dual Logos (Desktop & Mobile) in Shopify Horizon Theme

This guide documents the technical requirements, Shopify theme architecture, and exact code changes needed to support two separate logos (desktop and mobile) in the **Shopify Horizon theme** (version 4.x+).

---

## 1. Shopify Architecture Overview & Documentation Insights

In modern Shopify themes like Horizon (built on Online Store 2.0 and Component-driven architecture):
- **Global Settings Schema (`config/settings_schema.json`)**:
  - Global theme settings define attributes accessible site-wide via the `settings` Liquid object (e.g., `settings.logo`, `settings.mobile_logo`).
  - Settings of type `image_picker` upload files directly through the Shopify CDN.
  - The `visible_if` attribute allows conditional visibility in the Theme Customizer based on expressions like `"{{ settings.logo != blank or settings.mobile_logo != blank }}"`.
- **Static Theme Blocks (`content_for 'block', ...`)**:
  - Horizon renders the header logo using static block invocation:
    ```liquid
    content_for 'block', type: '_header-logo', id: 'header-logo', mobile_logo: settings.mobile_logo, mobile_logo_height: settings.logo_height_mobile
    ```
  - As detailed in [Shopify Theme Architecture Docs](https://shopify.dev/docs/themes/architecture/blocks/theme-blocks), `content_for 'block', type: ...` allows developers to statically position fixed components while passing dynamic parameter variables into the block.
- **Structured Data (JSON-LD)**:
  - Google Schema recommendations specify an `Organization` logo. When introducing a mobile logo, Liquid fallbacks ensure search engines always receive a valid logo URL:
    ```liquid
    {% assign organization_logo = settings.logo | default: settings.mobile_logo %}
    ```

---

## 2. File Changes Overview

| File | Purpose |
| :--- | :--- |
| [`theme/config/settings_schema.json`](../../theme/config/settings_schema.json) | Declares the `mobile_logo` image picker setting and `logo_height_mobile` range slider in the theme customizer. |
| [`theme/sections/header.liquid`](../../theme/sections/header.liquid) | Passes `mobile_logo` attributes to the header block, updates JSON-LD schema markup, and defines responsive CSS rules. |

---

## 3. Step-by-Step Implementation

### Step 1: Add Mobile Logo to `settings_schema.json`

Open [`theme/config/settings_schema.json`](../../theme/config/settings_schema.json) and locate `"name": "t:names.logo_and_favicon"`. Add the `mobile_logo` setting immediately after the primary `logo` setting:

```json
{
  "name": "t:names.logo_and_favicon",
  "settings": [
    {
      "type": "paragraph",
      "content": "t:content.manage_store_name"
    },
    {
      "type": "image_picker",
      "id": "logo",
      "label": "t:settings.default_logo"
    },
    {
      "type": "image_picker",
      "id": "mobile_logo",
      "label": "Mobile Logo"
    },
    {
      "type": "image_picker",
      "id": "logo_inverse",
      "label": "t:settings.inverse_logo",
      "info": "t:content.inverse_logo_info"
    },
    {
      "type": "range",
      "id": "logo_height",
      "label": "t:settings.desktop_height",
      "min": 12,
      "max": 100,
      "step": 1,
      "unit": "px",
      "default": 36,
      "visible_if": "{{ settings.logo != blank or settings.mobile_logo != blank or settings.logo_inverse != blank }}",
      "info": "t:info.logo_height"
    },
    {
      "type": "range",
      "id": "logo_height_mobile",
      "label": "t:settings.mobile_height",
      "min": 12,
      "max": 100,
      "step": 1,
      "unit": "px",
      "default": 28,
      "visible_if": "{{ settings.logo != blank or settings.mobile_logo != blank or settings.logo_inverse != blank }}",
      "info": "t:info.logo_height"
    },
    {
      "type": "image_picker",
      "id": "favicon",
      "label": "t:settings.favicon"
    }
  ]
}
```

---

### Step 2: Pass Parameters in `header.liquid`

In [`theme/sections/header.liquid`](../../theme/sections/header.liquid), locate the logo block capture (around line 81):

```liquid
capture logo
  content_for 'block', type: '_header-logo', id: 'header-logo', mobile_logo: settings.mobile_logo, mobile_logo_height: settings.logo_height_mobile
endcapture
```

---

### Step 3: Update Organization Schema (JSON-LD)

In [`theme/sections/header.liquid`](../../theme/sections/header.liquid) around line 326, update the schema markup so fallback logic protects structured data if only one logo is uploaded:

```liquid
<script type="application/ld+json">
  {
    "@context": "http://schema.org",
    "@type": "Organization",
    "name": {{ shop.name | json }},
    {% assign organization_logo = settings.logo | default: settings.mobile_logo %}
    {% if organization_logo %}
      "logo": {{ organization_logo | image_url: width: 500 | prepend: "https:" | json }},
    {% endif %}
    "url": {{ request.origin | append: page.url | json }}
  }
</script>
```

---

### Step 4: Add Responsive Switching (Block / Standalone Markup)

If customizing or overriding the `_header-logo` markup directly (or rendering within a custom snippet):

```liquid
<a href="{{ routes.root_url }}" class="header-logo">
  {%- assign mobile_logo = settings.mobile_logo | default: settings.logo -%}

  {%- if settings.logo != blank -%}
    {{
      settings.logo
      | image_url: width: 600
      | image_tag:
        class: 'header-logo__image header-logo__image--desktop',
        alt: shop.name,
        loading: 'eager',
        fetchpriority: 'high'
    }}
  {%- endif -%}

  {%- if mobile_logo != blank -%}
    {{
      mobile_logo
      | image_url: width: 400
      | image_tag:
        class: 'header-logo__image header-logo__image--mobile',
        alt: shop.name,
        loading: 'eager',
        fetchpriority: 'high'
    }}
  {%- endif -%}

  {%- if settings.logo == blank and settings.mobile_logo == blank -%}
    <span class="header-logo__text">{{ shop.name }}</span>
  {%- endif -%}
</a>
```

---

### Step 5: Responsive CSS Rules

Add the breakpoint logic in your header `<style>` block (around line 520 in [`theme/sections/header.liquid`](../../theme/sections/header.liquid)):

```css
.header-logo {
  display: inline-flex;
  align-items: center;
}

.header-logo img,
.header-logo svg {
  max-height: var(--header-logo-height);
  width: auto;
  object-fit: contain;
}

/* Mobile Screen Breakpoint (< 750px) */
@media screen and (max-width: 749px) {
  .header-logo img,
  .header-logo svg {
    max-height: var(--header-logo-height-mobile);
  }

  .header-logo__image--desktop {
    display: none !important;
  }

  .header-logo__image--mobile {
    display: block !important;
  }
}

/* Desktop Screen Breakpoint (>= 750px) */
@media screen and (min-width: 750px) {
  .header-logo__image--desktop {
    display: block !important;
  }

  .header-logo__image--mobile {
    display: none !important;
  }
}
```

---

## 4. Verification Checklist

- [ ] **Theme Customizer Display**: Navigate to **Online Store > Themes > Customize > Theme Settings > Logo and favicon**. Verify that **Mobile Logo** and **Mobile logo height** sliders are visible.
- [ ] **Fallback Verification**: If only a desktop logo is uploaded, verify the mobile view gracefully falls back to displaying the desktop logo scaled to `logo_height_mobile`.
- [ ] **LCP Performance Check**: Confirm both images include `loading: 'eager'` and `fetchpriority: 'high'` to prevent Largest Contentful Paint (LCP) delays.
- [ ] **Rich Snippet Test**: Test the homepage on Google's Rich Results Test tool to confirm valid JSON-LD `Organization` logo output.
