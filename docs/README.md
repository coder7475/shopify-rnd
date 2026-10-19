# Shopify Documentation Index

> The complete architectural reference, operational SOPs, marketing frameworks, and integration guides for the Naza Noor Shopify store.

This directory houses all research, guides, and strategic playbooks. Production Liquid theme overrides live in [`../theme/`](../theme).

---

## 🧭 Fast-Track Implementation Pathways

Find the exact guide you need based on your immediate objective:

```
                  ┌─────────────────────────────────────┐
                  │       WHAT ARE YOU BUILDING TODAY?  │
                  └──────────────────┬──────────────────┘
                                     │
         ┌───────────────────────────┼───────────────────────────┐
         ▼                           ▼                           ▼
┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│  Store Launch    │       │  Theme Overhaul  │       │ Growth & Scaling │
│  & Operations    │       │  & UX Tweaks     │       │ & AI Commerce    │
└────────┬─────────┘       └────────┬─────────┘       └────────┬─────────┘
         │                          │                          │
         ├─ Domain & Email Auth     ├─ Dual Desktop/Mobile     ├─ Must-Know Master
         │  (SPF, DKIM, DMARC)      │  Logos                   │  Strategy Framework
         ├─ Customer Accounts       ├─ Header Z-Index Fix      ├─ Agentic AI Store
         ├─ Search & Discovery      ├─ WhatsApp & Messenger    ├─ Unified Retention
         └─ POS & Payments          └─ New Arrivals Block      └─ Meta / Google Ads
```

### Path 1: Operational Store Setup (Launch-Ready Checklist)
Follow this sequence to take a new or migrating store live:
1. **[Professional Email & Domain Authentication](./guides/professional-email-setup.md)**: Configure DNS records (SPF, DKIM, DMARC) so order confirmations never land in spam.
2. **[Customer Account Domain](./guides/customer-account-domain.md)**: Route new or classic customer accounts to your custom domain.
3. **[Shopify Search & Discovery](./guides/search-and-discovery.md)**: Configure facets, visual filters, and product boost rules.
4. **[Manual QR Payments](./guides/manual-qr-payments.md)**: Enable regional mobile banking / QR scan checkout instructions.
5. **[EPS Payment Gateway](./payments/eps-payment-gateway.md)**: Set up direct merchant payment integrations.
6. **[Shopify POS Setup](./guides/shopify-pos.md)**: Connect retail hardware, barcode scanners, and register locations.
7. **[Image Sizes & Aspect Ratios](./guides/image-sizes.md)**: Ensure uploaded banners and product media adhere to standard dimensions.

### Path 2: Theme Customization & UX
Implement custom Liquid blocks and fixes without paid apps:
1. **[Theme File Map & Guide](../theme/README.md)**: Overview of sections, snippets, and blocks.
2. **[Mobile Logo Guide](./theme/mobile-logo-guide.md)**: Render a dedicated mobile logo without duplicating header sections.
3. **[Horizon Dual Logo Guide](./theme/horizon-dual-logo-guide.md)**: Desktop/mobile logo switching with configurable heights in theme settings.
4. **[Header Menu Z-Index Fix](./theme/header-menu-z-index.md)**: Prevent mega menus from clipping under floating chat widgets.
5. **[Multi-Channel Chat Apps & Widgets](./support/multi-channel-chat-apps.md)**: Embed WhatsApp and Messenger chat buttons and slide-out tabs.

### Path 3: Growth, AI Discovery & Retention
Deploy modern customer acquisition and retention engines:
1. **[Must-Know Marketing Strategy](./marketing/must-know-marketing-strategy.md)**: The 3-pillar framework — Search Everywhere (SEvO/GEO), native DM commerce, and point-of-decision social proof.
2. **[Shopify Agentic Storefronts](./features/shopify-agentic-storefronts.md)**: 2026 Spring Edition guide to ChatGPT, Perplexity, and AI agent checkout via Universal Commerce Protocol (UCP).
3. **[Shopify Omnichannel Marketing](./marketing/shopify-omnichannel-marketing-guide.md)**: Cohesive multi-channel customer journeys across web, social, and chat.
4. **[Unified Retention Marketing Guide](./marketing/retention/retention-marketing-guide.md)**: Lifecycle orchestration across Email, SMS, WhatsApp, and social DMs.
5. **[Meta Ads Master Playbook](./marketing/meta-ads-marketing-guide.md)**: Algorithmic targeting, creative frameworks (PROOF / QUEST), and personalized destinations.
6. **[Master Social Commerce Guide](./marketing/selling-via-shops/master-social-commerce-guide.md)**: Sell directly on Instagram, Facebook, and TikTok shops.

---

## 🗂️ Section Directory

| Section | Focus Area | Key Guides Included |
| :--- | :--- | :--- |
| **[`guides/`](./guides)** | Operational SOPs | Email setup, custom account domain, Search & Discovery, POS, QR payments, image sizing |
| **[`features/`](./features)** | Native Shopify Capabilities | Agentic Storefronts (Spring 2026), Collective, Inbox, Messaging, Shop App, Mobile App |
| **[`marketing/`](./marketing)** | Growth & Acquisition | Master strategy, Meta ads, Google ads, SEO/GEO, Omnichannel, Retention, Creator guide |
| **[`integrations/`](./integrations)** | Platform Channels | Meta connection, Business Suite configuration, Meta Growth Playbook |
| **[`reviews/`](./reviews)** | Social Proof | Native Metaobject review architecture vs third-party review apps (Trustoo) |
| **[`seo/`](./seo)** | Search & GEO | Technical SEO roadmap, AI meta title/description prompt templates |
| **[`payments/`](./payments)** | Checkout & Billing | Electronic Payment Systems (EPS) and manual payment gateway setup |
| **[`support/`](./support)** | Customer Messaging | Multi-channel chat snippets, Omega chat buttons evaluation |
| **[`theme/`](./theme)** | Theme Documentation | Logo switching, header z-index resolution, snippet integration notes |
| **[`archive/`](./archive)** | Reference Archive | Superseded research notes, early R&D drafts |
| **[`resources.md`](./resources.md)** | Resource Index | Curated external tools, documentation portals, and video tutorials |

---

## 📝 Documentation Conventions

To maintain consistency and accuracy across all documentation:
- **Tone & Perspective**: Written in the second person ("you"), active voice, and present tense.
- **Action-Oriented Headings**: Steps lead with verbs (e.g., "Step 1: Configure SPF DNS records").
- **Tested Code Examples**: Every Liquid snippet, curl command, or JSON schema is tested against standard Online Store 2.0 themes.
- **File Naming**: All files and directories use **kebab-case** (e.g., `manual-qr-payments.md`), with the exception of Shopify Liquid files which match their exact theme filename.
- **Deprecation Policy**: Never delete superseded technical documentation. Move it to [`archive/`](./archive/) and record the replacement link in [`archive/README.md`](./archive/README.md).
- **Relative Linking**: All inter-document links must use relative paths to ensure offline and multi-branch portability.
