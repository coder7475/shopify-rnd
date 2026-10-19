# Theme Code

Shopify Liquid customizations for the Naza Noor store, organized to mirror a Shopify theme's directory layout.

```
theme/
├── blocks/
│   └── new_arrivals.liquid       # "New arrivals" product carousel block
├── config/
│   └── settings_schema.json      # Theme settings (mobile logo, logo height, etc.)
├── sections/
│   └── header.liquid             # Header section (desktop/mobile logo logic)
└── snippets/
    ├── _header-logo.liquid       # Header logo snippet
    ├── _header_menu.liquid       # Header navigation / mega menu
    ├── logo.liquid               # Logo rendering snippet
    ├── order_on_whatsapp.liquid  # WhatsApp order button
    ├── add-messenger-button/     # Custom Liquid block: Messenger buy button
    ├── add-whatsapp-button/      # Custom Liquid block: WhatsApp buy button
    ├── messenger-widget/         # Messenger chat widget + side tab
    └── whatsapp-widget/          # WhatsApp chat widget + side tab
```

> **Note:** These are the customization files, not a complete theme. File names are kept identical to the theme so they can be copied in without changing `{% render %}` or `{% section %}` references.

---

## Documentation

| File | Description |
| :--- | :--- |
| [Mobile Logo Guide](../docs/theme/mobile-logo-guide.md) | Add a separate mobile logo via theme settings |
| [Horizon Dual Logo Guide](../docs/theme/horizon-dual-logo-guide.md) | Full desktop/mobile dual-logo implementation |
| [Header Menu Z-Index Fix](../docs/theme/header-menu-z-index.md) | Keep header menus above floating chat tabs |

---

## Related

- [Root README](../README.md)
- [Documentation index](../docs/README.md)
