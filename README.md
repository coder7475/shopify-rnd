# Shopify R&D and Customization Hub

A repository dedicated to Shopify research, theme customizations, operational guides, marketing playbooks, and channel integrations for the Naza Noor store.

---

## 📂 Repository Structure

| Directory | Description |
| :--- | :--- |
| [`theme/`](./theme) | Shopify theme code — sections, snippets, and config schema |
| [`docs/`](./docs) | All research, guides, and playbooks (see the [docs index](./docs/README.md)) |
| [`docs/guides/`](./docs/guides) | Operational how-to guides (POS, image sizes, email, payments, apps) |
| [`docs/features/`](./docs/features) | Native Shopify capabilities (Collective, Inbox, Messaging, Shop App, Mobile App) |
| [`docs/integrations/`](./docs/integrations) | Meta (Facebook & Instagram) channel setup and marketing playbooks |
| [`docs/marketing/`](./docs/marketing) | Marketing strategy, channel guides, creator strategy, and social commerce |
| [`docs/reviews/`](./docs/reviews) | Product review systems (apps and native Metaobjects) |
| [`docs/seo/`](./docs/seo) | SEO strategy, execution guides, and reusable prompts |
| [`docs/payments/`](./docs/payments) | Payment gateway integration guides (e.g., EPS) |
| [`docs/support/`](./docs/support) | Customer chat applications and multi-channel support research |
| [`docs/theme/`](./docs/theme) | Theme customization documentation (logos, header menu) |
| [`docs/archive/`](./docs/archive) | Superseded drafts, kept for reference |
| [`data/product-csvs/`](./data/product-csvs) | Sample product import datasets (Apparel, Jewelry, Home & Garden) |
| [`assets/brand/logos/`](./assets/brand/logos) | Naza Noor brand logos (PNG and SVG) |
| [`resources.md`](./docs/resources.md) | Curated external tools, references, and platform documentation |

---

## 🛠️ Theme Customizations

| Customization | Code | Documentation |
| :--- | :--- | :--- |
| Header (desktop/mobile logos) | [`theme/sections/header.liquid`](./theme/sections/header.liquid) | [Mobile logo guide](./docs/theme/mobile-logo-guide.md) · [Dual logo guide](./docs/theme/horizon-dual-logo-guide.md) |
| Theme settings schema | [`theme/config/settings_schema.json`](./theme/config/settings_schema.json) | — |
| Header navigation | [`theme/snippets/_header_menu.liquid`](./theme/snippets/_header_menu.liquid) | [Z-index fix](./docs/theme/header-menu-z-index.md) |
| New arrivals carousel | [`theme/blocks/new_arrivals.liquid`](./theme/blocks/new_arrivals.liquid) | — |
| WhatsApp & Messenger widgets | [`theme/snippets/messenger-widget/`](./theme/snippets/messenger-widget) · [`theme/snippets/whatsapp-widget/`](./theme/snippets/whatsapp-widget) | [Multi-channel chat apps](./docs/support/multi-channel-chat-apps.md) |

See [`theme/README.md`](./theme/README.md) for the full theme file map.

---

## 📚 Key Guides & Documentation

### Marketing
- **Masterclass**: [Digital Marketing 101](./docs/marketing/masterclass/01-digital-marketing-101.md) · [Pricing](./docs/marketing/masterclass/02-pricing-strategies.md) · [Distribution](./docs/marketing/masterclass/03-distribution-strategies.md) · [Promotion](./docs/marketing/masterclass/04-promotion-strategies.md)
- **Strategy**: [Must-Know Marketing Strategy](./docs/marketing/must-know-marketing-strategy.md) · [Omnichannel Marketing](./docs/marketing/shopify-omnichannel-marketing-guide.md) · [SEO & Content](./docs/marketing/seo-content-marketing-guide.md)
- **Paid media**: [Paid Social](./docs/marketing/paid-social-marketing-guide.md) · [Meta Ads](./docs/marketing/meta-ads-marketing-guide.md) · [Google Ads](./docs/marketing/google-ads-marketing-guide.md)
- **Retention**: [Unified Retention Guide](./docs/marketing/retention/retention-marketing-guide.md) · [Email](./docs/marketing/retention/email-marketing-guide.md) · [SMS](./docs/marketing/retention/sms-marketing-guide.md) · [WhatsApp](./docs/marketing/retention/whatsapp-marketing-guide.md) · [Social Messenger](./docs/marketing/retention/social-messenger-marketing-guide.md)
- **Social commerce**: [Master Social Commerce Guide](./docs/marketing/selling-via-shops/master-social-commerce-guide.md) · [Paid Ads Guide](./docs/marketing/selling-via-shops/paid-ads-guide.md)
- **Creator strategy**: [Content Creator Guide](./docs/marketing/content-creator-guide/README.md)

### Store Setup & Operations
- [Professional Email & Domain Authentication](./docs/guides/professional-email-setup.md)
- [Customer Account Domain](./docs/guides/customer-account-domain.md)
- [Manual QR Payments](./docs/guides/manual-qr-payments.md)
- [Shopify POS](./docs/guides/shopify-pos.md)
- [Shopify Image Sizes](./docs/guides/image-sizes.md)
- [Image Prompt Guide](./docs/guides/image-prompt-guide.md)
- [Search & Discovery](./docs/guides/search-and-discovery.md)
- [Free Shopify Apps](./docs/guides/shopify-free-apps.md)

### Features, Channels & Reviews
- [Sales Channels](./docs/features/sales-channels.md) · [Shopify Collective](./docs/features/shopify-collective.md) · [Shopify Inbox](./docs/features/shopify-inbox.md) · [Shopify Messaging](./docs/features/shopify-messaging.md) · [Shop App](./docs/features/shopify-shop-app.md) · [Mobile App](./docs/features/shopify-mobile-app.md)
- [Meta Connection](./docs/integrations/meta-connect.md) · [Meta Settings](./docs/integrations/meta-settings.md) · [Meta Growth Playbook](./docs/integrations/meta-growth-playbook.md)
- [Product Review System](./docs/reviews/review-system-guide.md) · [Custom Metaobject Reviews](./docs/reviews/custom-metaobject-reviews.md) · [Trustoo Reviews](./docs/reviews/trustoo-reviews.md)
- [EPS Payment Gateway](./docs/payments/eps-payment-gateway.md)
- [SEO Overview](./docs/seo/overview.md) · [Meta Title & Description Prompt](./docs/seo/prompts/meta-title-description.md)
