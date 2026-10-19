# Simplified Mobile Logo Implementation (Horizon Theme)

Upload a separate **Mobile Logo** in theme settings. It shows only on mobile screens (`< 750px`), while the default logo shows only on desktop (`≥ 750px`).

---

## Files to Change

| File | Location in Theme | What to Do |
| :--- | :--- | :--- |
| `settings_schema.json` | `config/settings_schema.json` | Add `mobile_logo` image picker setting |
| `_header-logo.liquid` | `blocks/_header-logo.liquid` | Output both images with responsive classes |
| `header.liquid` | `sections/header.liquid` | Pass `mobile_logo` to block + add responsive CSS |

---

## 1. `settings_schema.json`

Under `"name": "t:names.logo_and_favicon"`, add the `mobile_logo` setting after the default logo:

```json
{
  "type": "image_picker",
  "id": "mobile_logo",
  "label": "Mobile Logo"
}
```

---

## 2. `blocks/_header-logo.liquid`

Replace the contents of this file with:

```liquid
{%- liquid
  assign mobile_logo = settings.mobile_logo | default: settings.logo
-%}

{%- if settings.logo != blank -%}
  {{
    settings.logo
    | image_url: width: 600
    | image_tag:
      class: 'header-logo__image header-logo--desktop',
      alt: shop.name,
      loading: 'eager'
  }}
{%- endif -%}

{%- if mobile_logo != blank -%}
  {{
    mobile_logo
    | image_url: width: 400
    | image_tag:
      class: 'header-logo__image header-logo--mobile',
      alt: shop.name,
      loading: 'eager'
  }}
{%- endif -%}

{%- if settings.logo == blank and settings.mobile_logo == blank -%}
  <span class="header-logo__text">{{ shop.name }}</span>
{%- endif -%}
```

**Key points:**
- `mobile_logo` falls back to `settings.logo` if no mobile logo is uploaded.
- Do NOT add a wrapping `<div>` or `<a>` — the theme already provides that.

---

## 3. `sections/header.liquid`

### 3a. Pass `mobile_logo` to the block (line ~82)

```liquid
capture logo
  content_for 'block', type: '_header-logo', id: 'header-logo', mobile_logo: settings.mobile_logo
endcapture
```

### 3b. Set CSS variable on `<header-component>` inline style (line ~379)

Inside the existing `style="..."` attribute, add:

```liquid
--header-logo-height: {{ settings.logo_height | default: 40 }}px;
```

### 3c. Add static CSS inside `{% stylesheet %}` (line ~515)

```css
.header-logo img,
.header-logo svg {
  height: auto;
  max-height: var(--header-logo-height, 40px);
  width: auto;
  max-width: 100%;
  object-fit: contain;
}

@media screen and (max-width: 749px) {
  .header-logo--desktop {
    display: none !important;
  }
  .header-logo--mobile {
    display: block !important;
  }
}

@media screen and (min-width: 750px) {
  .header-logo--desktop {
    display: block !important;
  }
  .header-logo--mobile {
    display: none !important;
  }
}
```

> **Important:** Do NOT use Liquid tags (`{{ }}`) inside `{% stylesheet %}`. Use the CSS variable `var(--header-logo-height)` instead — the actual value is set via the inline `style` attribute on `<header-component>`.

### 3d. JSON-LD fallback (line ~331)

```liquid
{% assign organization_logo = settings.logo | default: settings.mobile_logo %}
{% if organization_logo %}
  "logo": {{ organization_logo | image_url: width: 500 | prepend: "https:" | json }},
{% endif %}
```
