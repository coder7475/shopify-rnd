# Shopify R&D and Customization Hub

> Production-ready Liquid theme overrides, operational SOPs, marketing frameworks, and omnichannel integrations for the [Naza Noor](https://nazanoor.com) Shopify store.

[![Shopify](https://img.shields.io/badge/Shopify-Online_Store_2.0-95BF47?logo=shopify&logoColor=white)](https://shopify.dev)
[![Liquid](https://img.shields.io/badge/Theme_Engine-Liquid-4A90E2)](https://shopify.dev/docs/api/liquid)
[![Edition](https://img.shields.io/badge/Shopify_Edition-Spring_2026_%22Everywhere%22-green)](https://shopify.dev)
[![Documentation](https://img.shields.io/badge/Docs-Structured_Guides-blue)](./docs/README.md)

---

## Why This Exists

Scaling a Shopify store requires solving technical, operational, and commercial challenges simultaneously. This repository is the single source of truth for:

1. **Production Theme Snippets**: Drop-in Liquid code and settings schemas for dual logos, floating social widgets, and conversion blocks without third-party app bloat.
2. **Operational SOPs**: Step-by-step documentation for domain verification, SPF/DKIM/DMARC email authentication, POS, and localized payment gateways.
3. **Omnichannel Growth Playbooks**: Data-backed strategies spanning SEO/GEO, Meta Ads, Google Ads, native DM commerce, and Spring 2026 Agentic Storefronts.
4. **Verified Sample Data**: Ready-to-import product datasets with pre-configured variants, image CDN references, and custom metafield mappings.

---

## ⚡ Quick Start: Choose Your Path

```
┌────────────────────────────────────────────────────────────────────────┐
│                          WHERE DO YOU WANT TO START?                   │
├────────────────────┬────────────────────┬──────────────────────────────┤
│ 🎨 Theme Dev       │ 🏬 Store Ops       │ 📈 Growth & Marketing        │
│                    │                    │                              │
│ • Inspect snippets │ • Setup email/DNS  │ • Master strategy playbook   │
│ • Wire dual logo   │ • Configure domain │ • Set up retention flows     │
│ • Test widgets     │ • Import CSV data  │ • Connect Meta / Ads         │
│                    │                    │                              │
│ ➔ Jump to Theme    │ ➔ Jump to Ops      │ ➔ Jump to Growth             │
└────────────────────┴────────────────────┴──────────────────────────────┘
```

### 1. For Theme Developers
Deploy custom Liquid components directly into your Online Store 2.0 theme:
```bash
# Clone the repository
git clone https://github.com/your-org/shopify.git
cd shopify

# Preview custom theme snippets and blocks
ls theme/snippets theme/blocks theme/sections
```
* See [Theme Code README](./theme/README.md) for integration instructions, Liquid render calls, and settings schema keys.

### 2. For Store Operators
Prepare your store for live transactions and order fulfillment:
1. **Email & Domain**: Authenticate your sender domain with SPF, DKIM, and DMARC ([Email Setup Guide](./docs/guides/professional-email-setup.md)).
2. **Customer Accounts**: Configure your headless or customized login flow ([Customer Account Domain](./docs/guides/customer-account-domain.md)).
3. **Catalog Seeding**: Import tested product catalogs with custom metafields ([Product CSV Guide](./data/product-csvs/README.md)).
4. **Local Payments**: Set up QR codes or regional gateways ([Manual QR Payments](./docs/guides/manual-qr-payments.md) · [EPS Gateway](./docs/payments/eps-payment-gateway.md)).

### 3. For Growth & Marketing Teams
Launch campaigns and conversational commerce funnels:
1. **Foundational Strategy**: Read the 3-pillar framework in [Must-Know Marketing Strategy](./docs/marketing/must-know-marketing-strategy.md).
2. **Omnichannel & AI Discovery**: Configure [Omnichannel Marketing](./docs/marketing/shopify-omnichannel-marketing-guide.md) and [Agentic Storefronts](./docs/features/shopify-agentic-storefronts.md).
3. **Retention Engine**: Deploy unified email, SMS, and WhatsApp automations ([Retention Marketing Guide](./docs/marketing/retention/retention-marketing-guide.md)).
4. **Paid Media**: Scale high-ROAS creative with [Meta Ads Guide](./docs/marketing/meta-ads-marketing-guide.md) and [Google Ads Guide](./docs/marketing/google-ads-marketing-guide.md).

---

## 📂 Repository Structure

| Directory | Scope & Purpose |
| :--- | :--- |
| [`theme/`](./theme) | Production Liquid theme overrides: sections, snippets, blocks, and schema |
| [`docs/`](./docs) | Full documentation index across setup, features, marketing, and SEO |
| [`docs/guides/`](./docs/guides) | Operational guides: POS, image specifications, domain auth, free apps |
| [`docs/features/`](./docs/features) | Native Shopify features: Agentic Storefronts, Collective, Inbox, Messaging |
| [`docs/integrations/`](./docs/integrations) | Meta (Facebook & Instagram) channel setup and marketing playbooks |
| [`docs/marketing/`](./docs/marketing) | Comprehensive marketing playbooks, retention engines, masterclasses |
| [`docs/reviews/`](./docs/reviews) | Customer review architecture: native Metaobjects vs app solutions |
| [`docs/seo/`](./docs/seo) | Organic search strategy, GEO (Generative Engine Optimization), AI prompts |
| [`docs/payments/`](./docs/payments) | Payment gateway setups (manual QR, EPS, regional providers) |
| [`docs/support/`](./docs/support) | Customer chat applications and omnichannel support research |
| [`docs/theme/`](./docs/theme) | Implementation docs for theme customizations (logos, z-index fixes) |
| [`docs/archive/`](./docs/archive) | Superseded research notes and legacy drafts kept for historical context |
| [`data/product-csvs/`](./data/product-csvs) | Tested CSV datasets (Apparel with Metafields, Jewelry, Home & Garden) |
| [`assets/brand/logos/`](./assets/brand/logos) | Vector SVG and raster PNG brand assets for Naza Noor |
| [`docs/resources.md`](./docs/resources.md) | Curated developer tools, official documentation links, and media resources |

---

## 🛠️ Theme Customizations

| Customization | Code Location | Documentation |
| :--- | :--- | :--- |
| **Desktop / Mobile Dual Logo** | [`theme/sections/header.liquid`](./theme/sections/header.liquid)<br>[`theme/snippets/_header-logo.liquid`](./theme/snippets/_header-logo.liquid) | [Mobile Logo Guide](./docs/theme/mobile-logo-guide.md)<br>[Horizon Dual Logo Guide](./docs/theme/horizon-dual-logo-guide.md) |
| **Theme Settings Schema** | [`theme/config/settings_schema.json`](./theme/config/settings_schema.json) | [Theme README](./theme/README.md) |
| **Header Navigation & Z-Index** | [`theme/snippets/_header_menu.liquid`](./theme/snippets/_header_menu.liquid) | [Header Z-Index Fix](./docs/theme/header-menu-z-index.md) |
| **New Arrivals Carousel** | [`theme/blocks/new_arrivals.liquid`](./theme/blocks/new_arrivals.liquid) | [Theme README](./theme/README.md) |
| **Floating Chat Widgets** | [`theme/snippets/messenger-widget/`](./theme/snippets/messenger-widget)<br>[`theme/snippets/whatsapp-widget/`](./theme/snippets/whatsapp-widget) | [Multi-Channel Chat Apps](./docs/support/multi-channel-chat-apps.md) |
| **Product Page Buy Buttons** | [`theme/snippets/add-messenger-button/`](./theme/snippets/add-messenger-button)<br>[`theme/snippets/add-whatsapp-button/`](./theme/snippets/add-whatsapp-button)<br>[`theme/snippets/order_on_whatsapp.liquid`](./theme/snippets/order_on_whatsapp.liquid) | [Multi-Channel Chat Apps](./docs/support/multi-channel-chat-apps.md) |

For complete Liquid code snippets, integration examples, and settings schemas, see [`theme/README.md`](./theme/README.md).

---

## 📚 Core Documentation Directory

### 🚀 Store Setup & Operations
- [Professional Email & Domain Authentication](./docs/guides/professional-email-setup.md) — SPF, DKIM, DMARC, and custom sender address setup.
- [Customer Account Domain](./docs/guides/customer-account-domain.md) — Custom domain routing for new vs classic customer accounts.
- [Shopify Search & Discovery](./docs/guides/search-and-discovery.md) — Custom filters, product boosts, and synonym configuration.
- [Manual QR Payments](./docs/guides/manual-qr-payments.md) — Seamless mobile banking / QR payment flows at checkout.
- [Shopify POS Setup](./docs/guides/shopify-pos.md) — Hardware, location settings, and in-person retail sync.
- [Image Sizes & Ratio Guide](./docs/guides/image-sizes.md) — Standardized aspect ratios for banners, collections, and products.
- [AI Image Prompting Guide](./docs/guides/image-prompt-guide.md) — Midjourney/Gemini prompts for commercial e-commerce product imagery.
- [Free Shopify Apps](./docs/guides/shopify-free-apps.md) — Curated zero-cost apps that replace paid subscriptions.

### 🤖 2026 Features & Sales Channels
- [Shopify Agentic Storefronts](./docs/features/shopify-agentic-storefronts.md) — Complete guide to Spring 2026 "Everywhere" AI agent discovery & UCP purchases.
- [Sales Channels Overview](./docs/features/sales-channels.md) — Native Shopify sales channel comparison and rollout guide.
- [Shopify Collective](./docs/features/shopify-collective.md) — B2B dropshipping and inventory sharing across Shopify brands.
- [Shopify Inbox & Customer Chat](./docs/features/shopify-inbox.md) — Native live chat, instant answers, and cart-building automations.
- [Shopify Messaging](./docs/features/shopify-messaging.md) — Centralized merchant messaging infrastructure.
- [Shop App Optimization](./docs/features/shopify-shop-app.md) — Maximizing discovery and repeat conversions in the Shop App.
- [Shopify Mobile App](./docs/features/shopify-mobile-app.md) — Store management workflows on iOS and Android.

### 📈 Marketing, Channels & Retention
- **Master Strategy**: [Must-Know Marketing Strategy](./docs/marketing/must-know-marketing-strategy.md) · [Omnichannel Marketing Guide](./docs/marketing/shopify-omnichannel-marketing-guide.md) · [SEO & Content Marketing](./docs/marketing/seo-content-marketing-guide.md)
- **Marketing Masterclass**: [01: Digital Marketing 101](./docs/marketing/masterclass/01-digital-marketing-101.md) · [02: Pricing](./docs/marketing/masterclass/02-pricing-strategies.md) · [03: Distribution](./docs/marketing/masterclass/03-distribution-strategies.md) · [04: Promotion](./docs/marketing/masterclass/04-promotion-strategies.md)
- **Paid Media**: [Meta Ads Guide](./docs/marketing/meta-ads-marketing-guide.md) · [Google Ads Guide](./docs/marketing/google-ads-marketing-guide.md) · [Paid Social Overview](./docs/marketing/paid-social-marketing-guide.md)
- **Retention**: [Unified Retention Playbook](./docs/marketing/retention/retention-marketing-guide.md) · [Email](./docs/marketing/retention/email-marketing-guide.md) · [SMS](./docs/marketing/retention/sms-marketing-guide.md) · [WhatsApp](./docs/marketing/retention/whatsapp-marketing-guide.md) · [Social Messenger](./docs/marketing/retention/social-messenger-marketing-guide.md)
- **Social Commerce**: [Master Social Commerce Guide](./docs/marketing/selling-via-shops/master-social-commerce-guide.md) · [Paid Ads for Shops](./docs/marketing/selling-via-shops/paid-ads-guide.md) · [Product Tagging](./docs/marketing/selling-via-shops/product-tagging-guide.md)
- **Creator Economy**: [Complete Content Creator's Guide (2026)](./docs/marketing/content-creator-guide/README.md)

### 🔌 Integrations, Reviews & Support
- **Meta Platform**: [Meta Connection](./docs/integrations/meta-connect.md) · [Meta Settings](./docs/integrations/meta-settings.md) · [Meta Growth Playbook](./docs/integrations/meta-growth-playbook.md)
- **Reviews**: [Review System Architecture](./docs/reviews/review-system-guide.md) · [Native Metaobject Reviews](./docs/reviews/custom-metaobject-reviews.md) · [Trustoo Reviews App](./docs/reviews/trustoo-reviews.md)
- **Payments**: [EPS Payment Gateway](./docs/payments/eps-payment-gateway.md)
- **Customer Support**: [Multi-Channel Chat Apps](./docs/support/multi-channel-chat-apps.md) · [Omega Chat Buttons R&D](./docs/support/facebook-chat-app-rnd.md)
- **SEO & Prompts**: [SEO Roadmap](./docs/seo/overview.md) · [Meta Title & Description AI Prompts](./docs/seo/prompts/meta-title-description.md)

---

## 💻 Tech Stack & Compatibility

| Component | Standard / Technology | Notes |
| :--- | :--- | :--- |
| **Theme Engine** | Liquid 5.x / Online Store 2.0 | Section rendering API and JSON templates |
| **Catalog Architecture** | Shopify Metafields & Metaobjects | Native schema modeling without heavy third-party app databases |
| **Analytics & Pixels** | Shopify Web Pixels API | Compliant with 2026 deprecation of legacy `additional_scripts` |
| **AI Integration** | Universal Commerce Protocol (UCP) | Compatible with ChatGPT, Perplexity, Claude, and Gemini shopping agents |

---

## 🤝 Contributing & Documentation Standards

When adding or updating content in this repository:
- **Code snippets must be verified**: Test all Liquid snippets in a preview theme before opening a PR.
- **Audience-first structure**: Every document must clearly define its target audience, prerequisites, and actionable outcomes.
- **Preserve history**: Move superseded research or early R&D drafts to [`docs/archive/`](./docs/archive/) rather than deleting them.
- **Consistent naming**: Use `kebab-case` for markdown files and folders; keep theme files named exactly as they appear in Shopify themes.

---

## 📄 License

Internal documentation and proprietary theme assets for **Naza Noor**. All rights reserved. Code snippets may be adapted for Shopify development within organization projects.
