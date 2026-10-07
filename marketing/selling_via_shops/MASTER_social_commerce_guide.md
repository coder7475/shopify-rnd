# Selling via Social Shops: Complete Guide for Shopify Merchants

> **Scope:** End-to-end reference for selling on Facebook, Instagram, TikTok, and Pinterest via Shopify.
> **Last Updated:** October 2026
> **Individual Documents:** [Facebook Shop](./research/facebook-shop-research.md) · [Instagram Shop](./research/instagram-shop-research.md) · [Meta Ads](./research/meta-ads-research.md) · [TikTok Shop](./research/tiktok-shop-research.md) · [Pinterest Shop](./research/pinterest-shop-research.md) · [Product Tagging Guide](./product_tagging_guide.md) · [Resources](./research/video-resources.md)

---

## ⚠️ Critical 2026 Alerts — Read First

> [!CAUTION]
> **Shopify Additional Scripts Deprecated (August 26, 2026):** Any Meta, TikTok, or Pinterest pixel code pasted into "Additional Scripts" on the Thank You / Order Status pages stopped working on August 26, 2026. **Action Required:** Ensure you are using the official channel apps (Meta, TikTok, Pinterest), which use Shopify's Web Pixel framework. Verify under `Shopify Admin > Settings > Customer Events`.

> [!IMPORTANT]
> **Meta In-App Checkout Discontinued (Late 2025):** All Facebook and Instagram Shop purchases now redirect to your Shopify website. You must configure a valid checkout URL in Meta Commerce Manager > Shop Settings > General. Post-purchase management (refunds, returns) must be handled via Shopify, not Commerce Manager.

> [!IMPORTANT]
> **TikTok US Fully Operational (January 2026):** The US ban threat is resolved. TikTok USDS is now 80.1% American-owned (Oracle, Silver Lake, MGX). DOJ confirmed full legality in July 2026. TikTok Shop is a core, fully active US marketplace.

> [!IMPORTANT]
> **TikTok Ads: GMV Max Only (July 2025):** All legacy TikTok Shop ad formats (Video Shopping Ads, Product Shopping Ads, LIVE Shopping Ads) have been replaced by GMV Max as the sole ad format.

> [!NOTE]
> **Meta Muse AI Agent (September 2026):** Meta's autonomous shopping agent can browse, compare, and purchase products on users' behalf. Enable **Shop Pay** on your Shopify store to be compatible with Muse checkout. Keep your Commerce Manager catalog complete and keyword-rich to be included in Muse recommendations.

---

## Table of Contents

1. [Platform Overview & Quick Comparison](#1-platform-overview--quick-comparison)
2. [Shopify Infrastructure Setup (Shared Foundation)](#2-shopify-infrastructure-setup-shared-foundation)
3. [Facebook Shops](#3-facebook-shops)
4. [Instagram Shopping](#4-instagram-shopping)
5. [Meta Advertising (Facebook & Instagram Ads)](#5-meta-advertising-facebook--instagram-ads)
6. [Product Tagging — Instagram & Facebook](#6-product-tagging--instagram--facebook)
7. [TikTok Shop](#7-tiktok-shop)
8. [Pinterest Shopping](#8-pinterest-shopping)
9. [Cross-Platform Strategy](#9-cross-platform-strategy)
10. [Key Dates & Platform Timeline](#10-key-dates--platform-timeline)
11. [References & Resources](#11-references--resources)

---

## 1. Platform Overview & Quick Comparison

| Platform | User Base | Content Format | Checkout Model | Best For |
| :--- | :--- | :--- | :--- | :--- |
| **Facebook** | 3B+ MAU; broad demographics | Feed posts, Stories, video | Website (Shopify) | Brand awareness, retargeting, catalog ads |
| **Instagram** | 2B+ MAU; 18–35 skew | Reels, Feed posts, Stories | Website (Shopify) | Visual discovery, lifestyle brands, Reels virality |
| **TikTok** | 1.5B+ MAU; Gen Z/Millennial | Short-form video, LIVE | Native in-app (TikTok Shop) | Impulse buys, viral products, LIVE selling |
| **Pinterest** | 500M+ MAU; high-income, purchase intent | Static pins, video pins | Hosted Checkout (in-app, 2026) or website | Home, fashion, lifestyle, evergreen SEO traffic |

### Social Commerce Market Context (2026)
- US social commerce market projected to surpass **$100 billion** in 2026.
- TikTok Shop expected to generate **$20–23 billion** in US sales in 2026.
- ~51% of US social buyers expected to shop on TikTok in 2026 (conversion rate ~4.7%).
- Over 1 billion Instagram Reels views daily; ~⅓ of active users engage with shopping.
- Pinterest: 500M+ MAU with the highest purchase-intent of all social platforms.

---

## 2. Shopify Infrastructure Setup (Shared Foundation)

This section covers the essential Shopify setup required before activating any social commerce channel.

### 2.1 Core Requirements

Before connecting any social channel, verify the following:

- [ ] **Shopify Store:** Active store with products published and inventory > 0.
- [ ] **Shop Pay Enabled:** Required for Meta Muse compatibility and Shopify's agentic commerce (ChatGPT checkout, AI agents). Enable under `Shopify Admin > Settings > Payments`.
- [ ] **Product Catalog Quality:** Ensure all products have complete titles, descriptions, accurate attributes, and high-quality images. This data now powers AI discovery across Meta, TikTok, Pinterest, and AI agents (ChatGPT, Gemini, etc.).
- [ ] **Web Pixel Tracking (August 2026 mandatory):** Do NOT use Additional Scripts for tracking. Use official channel apps and/or Shopify's `Settings > Customer Events` for all platform pixels.
- [ ] **Shopify Sales Channel Apps Updated:** Ensure Meta, TikTok, and Pinterest apps are on the latest version in your Shopify admin.

### 2.2 Shopify Agentic Commerce (Spring 2026)

Shopify launched its "Everywhere" update in Spring 2026, enabling AI agents to purchase directly through Shopify stores:

- **Universal Commerce Protocol (UCP):** Open standard (co-developed with Google, supported by Meta, Microsoft, Amazon) enabling AI agents (ChatGPT, Copilot, Gemini, etc.) to interact with your store.
- **Checkout-in-Chat via Shop Pay:** AI agents complete purchases within chat interfaces without browser redirects.
- **Shopify Catalog:** Products optimized in your catalog convert at **2x the rate** in AI chats vs. non-optimized listings.
- **Agentic Storefront Dashboard:** Manage your AI surface presence from a single Shopify admin location.
- **Campaign Autopilot:** AI-powered ad tool managing campaigns across Facebook, Instagram, and Shop simultaneously with target ROAS guardrails.

---

## 3. Facebook Shops

*Full document:* [facebook-shop-research.md](./research/facebook-shop-research.md)

### 3.1 Executive Summary

A Facebook Shop requires two layers: (1) Meta Business authentication & authorization, and (2) customer-facing page visibility.

### 3.2 Authentication & Security (Required First)

| Requirement | Action |
| :--- | :--- |
| **Two-Factor Auth (2FA)** | Enforce for all Business Portfolio admins |
| **Business Verification** | Submit legal docs in Meta Business Suite > Security Center |
| **Domain Verification** | DNS TXT record or HTML tag in Brand Safety > Domains |
| **Full Control / Task Access** | Assign correct NPE permissions to operating account |
| **System Users** | Use for automated API integration (not personal tokens) |

### 3.3 New Pages Experience (NPE) — Current Standard

The Classic Pages interface is deprecated. The **New Pages Experience** is the universal standard as of 2026:

1. **Switch to Page Profile Mode:** Click profile icon > "Switch profile" > select your Page.
2. **Configure "View Shop" Action Button:** Click `...` next to "Manage" > "Edit Action Button" > "View Shop".
3. **Pin Shop Section to Top:** Scroll to sections > `...` > "Manage Sections" > Pin Shop to top.
4. **Configure Website Checkout URL:** Commerce Manager > Shop Settings > Checkout > enter Shopify store URL.

### 3.4 Commerce Manager Setup

- Manage product catalog, inventory sync, and shop visual identity from Commerce Manager.
- Configure a valid checkout URL (mandatory post-2025 transition).
- AI-Enhanced Catalogs (2026): Commerce Manager now auto-enhances product images and descriptions. Ensure catalog data is complete.
- **Privacy Controls (July 2026):** Meta restructured off-platform activity controls — audit your pixel/CAPI configuration.

### 3.5 2026 Key Updates

| Update | Impact |
| :--- | :--- |
| Mandatory website checkout | All purchases redirect to Shopify; configure checkout URL |
| Muse AI Agent (Sept 2026) | Autonomous shopping; enable Shop Pay; keep catalog complete |
| AI Mode in Facebook Search | AI-powered discovery bridging social content and shopping |
| NPE as universal standard | Classic Pages largely deprecated; use Task Access model |
| AI-automated chat support | AI agents handle Messenger/WhatsApp/IG DM customer inquiries |

---

## 4. Instagram Shopping

*Full document:* [instagram-shop-research.md](./research/instagram-shop-research.md)

### 4.1 Account Setup Workflow

```
Step 1: Switch to Professional Account (Business or Creator)
         ↓
Step 2: Connect Instagram to Facebook Page via Meta Accounts Center
         ↓
Step 3: Install Facebook & Instagram app on Shopify (Maximum Data Sharing)
         ↓
Step 4: Submit for Instagram Shopping Approval (24–48 hours)
         ↓
Result: "View Shop" profile button activated; product tagging unlocked
```

### 4.2 2026 Algorithm — What Drives Reach

| Signal | Weight | Strategy |
| :--- | :--- | :--- |
| **Sends per Reach (DM Shares)** | Highest | Create content shareable enough to DM to a friend |
| **Saves** | High | Educational carousels, product breakdowns, tutorials |
| **Watch Time / Loop Rate** | High (Reels) | Strong hooks, concise storytelling, loop-worthy endings |
| **Originality** | High | No TikTok watermarks; native original content only |
| **SEO Keywords** | Rising | Keyword-rich captions and alt text over generic hashtags |

### 4.3 Shoppable Content

| Format | Tag Method | Limit | Customer Experience |
| :--- | :--- | :--- | :--- |
| **Feed Posts** | Tag Products on share screen | 20 tags/post | Tap → product sheet → View on Website → Shopify |
| **Stories** | Product Sticker from Sticker tray | 1 sticker/slide | Tap sticker → product sheet → View on Website |
| **Reels** | Tag Products on final share screen | 30 products/collections | Shopping bag icon pinned during playback |
| **Affiliate Posts** | Creator Marketplace or direct partnership | Varies | Commission tracking integrated |

### 4.4 Key 2026 Features

- **Trial Reels:** A/B test content with non-follower audiences before permanent posting.
- **Collab Posts:** Share post with a partner to split engagement across both profiles.
- **Affiliate Tagging:** Creators tag affiliate products directly in posts/Reels with commission tracking.
- **SEO over Hashtags:** Keyword-rich captions drive search discovery more than hashtag stacking.

---

## 5. Meta Advertising (Facebook & Instagram Ads)

*Full document:* [meta-ads-research.md](./research/meta-ads-research.md)

### 5.1 The 2026 Ad Philosophy

Meta's ad engine has fully shifted from manual targeting to **AI creative-led targeting**:
- **Old:** Narrow interests, demographic filters, manual placements.
- **New:** Broad/Advantage+ targeting. The creative IS the targeting. Meta AI reads transcripts, audio, text, and visuals to match ads to buyers.

### 5.2 Infrastructure Setup

```
Meta Business Manager
├── Facebook Page & Instagram Professional Account
├── Meta Ad Account & Payment Method
└── Data Engine: Pixel + Conversions API (CAPI)
    └── Connected via Shopify Facebook & Instagram app (Maximum Data Sharing)
```

**Essential steps:**
1. Run ads from **Meta Business Manager** — never from personal ad accounts.
2. Set data sharing to **Maximum** in the Shopify Facebook & Instagram app.
3. Verify domain in Meta Business Settings (required for CAPI & aggregated event measurement).
4. **Audit CAPI after July 2026 privacy change** — Meta's restructured off-platform privacy controls may affect conversion signal flow.

### 5.3 Advantage+ Shopping Campaigns (ASC) — 2026 Structure

```
Campaign: Advantage+ Sales (ASC)
Objective: Sales → Purchase
Targeting: Broad/Automated (Advantage+ Audience)
Budget: Campaign-level (AI auto-allocates)
Placements: All (Feed, Reels, Stories, Search)
│
├── Existing Customer Budget Cap: 5–10%
└── Creatives: 15+ varied assets
    ├── UGC problem/solution
    ├── Founder story / unboxing
    ├── Feature showcase / demo
    ├── Social proof carousel
    └── Creator partnership ads
```

**2026 ASC Updates:**
- Learning phase threshold dropped to **25 conversions/week** (from 50).
- **Consolidated budget** at campaign level — AI allocates across placements/audiences automatically.
- **Opportunity Score:** New 0–100 diagnostic in Ads Manager.
- **Buy-Now button:** Reduces purchase friction for impulse/low-AOV products.
- AI now uses **Muse/chat intent signals** across WhatsApp, Messenger, IG, and Facebook.

### 5.4 Creative Strategy

| Format | Description | Key Metric |
| :--- | :--- | :--- |
| **UGC (User-Generated Content)** | Authentic smartphone review | Thumbstop Rate |
| **Feature Showcase/Demo** | High-contrast product demonstration | Hold Rate |
| **Social Proof Carousel** | Review quotes, press mentions | CTR |
| **Creator Partnership Ads** | Brand × creator collab via Creator Hub | ROAS |
| **Generative AI Variations** | Auto-generated by Meta Advantage+ Creative | Delivery efficiency |

### 5.5 Meta AI Tools (2026)

| Tool | Description |
| :--- | :--- |
| **Muse AI Agent** | Autonomous shopping agent (Sept 8, 2026); buys on users' behalf; supports Shop Pay |
| **Advantage+ Creative** | Auto-generates ad variations; enabled by default for new campaigns |
| **AI Product Summaries** | AI-aggregated review highlights shown when users click ads/brand pages |
| **AI Mode in Facebook Search** | Personalized discovery bridging search and shopping |
| **Muse for Small Business** | Connects to Shopify/Stripe to automate business tasks |
| **AI Chat Support Agents** | Automated customer support across Messenger, WhatsApp, IG DMs |

### 5.6 Performance Benchmarks

| Metric | Target | Interpretation |
| :--- | :--- | :--- |
| **ROAS** | > 2.5x (break-even) | Core profitability metric |
| **CPA** | < allowable CAC | Tells if scaling is sustainable |
| **Outbound CTR** | > 1.2%–2.0% | Below 1% = fatigued creative |
| **Thumbstop Rate** | > 25%–35% | Hook strength (first 3 seconds) |
| **Hold Rate** | > 20%–30% | Story/editing quality (ThruPlays / 3-sec views) |
| **Store Conversion Rate** | > 2.0%–3.5% | Landing page/PDP friction indicator |

---

## 6. Product Tagging — Instagram & Facebook

*Full document:* [product_tagging_guide.md](./product_tagging_guide.md)

### 6.1 Prerequisites Checklist

- [ ] Instagram Professional Account (Business or Creator)
- [ ] Facebook Page linked via Meta Accounts Center
- [ ] Shopify Facebook & Instagram app installed (Maximum Data Sharing)
- [ ] Products published to Facebook & Instagram sales channel in Shopify
- [ ] Domain verified in Meta Business Settings
- [ ] Checkout URL configured in Commerce Manager (mandatory, 2025)
- [ ] Web Pixel tracking active via official app (not Additional Scripts)

### 6.2 Platform Limits Summary

| Surface | Tag Limit | Notes |
| :--- | :--- | :--- |
| Feed Post (single image) | 20 product tags | — |
| Carousel Post | 20 product tags total | Shared across all cards |
| Reels | 30 products or collections | Shopping bag icon shown during playback |
| Stories | 1 Product Sticker per slide | — |
| Daily tagged posts | 25 per 24 hours | API/scheduling anti-spam limit |

### 6.3 Quick Tagging Steps

**Instagram Feed Post:** Create Post → Add Photo → Next → Tag Products → Tap product location → Search catalog → Select → Done → Share.

**Instagram Stories:** New Story → Sticker Tray → Product sticker → Search catalog → Resize & position → Share.

**Instagram Reels:** Record/Upload → Edit → Final screen → Tag Products → Select up to 30 → Share.

**Meta Business Suite (cross-post to both):** Create Post → Select Facebook + Instagram → Upload media → Tag Photo icon → Click product on image → Search catalog → Save → Publish/Schedule.

### 6.4 Troubleshooting

| Issue | Fix |
| :--- | :--- |
| "Tag Products" missing | Confirm Business/Creator account; check Shopping approval status |
| Product not in search | Enable Facebook & Instagram in Shopify product Sales Channels; check inventory > 0 |
| "Product Unavailable" on tap | Check Commerce Manager for catalog policy rejections or missing checkout URL |
| Tag covers face/key detail | Drag tags to corners/edges |
| Conversion tracking broken (post Aug 26) | Migrate from Additional Scripts to Web Pixels via official Meta app |

---

## 7. TikTok Shop

*Full document:* [tiktok-shop-research.md](./research/tiktok-shop-research.md)

### 7.1 US Regulatory Status

**Fully resolved.** TikTok USDS (US Data Security) joint venture finalized January 22, 2026 — 80.1% American-owned. DOJ confirmed legality in July 2026. TikTok Shop operates as a core, fully active US marketplace. US social commerce market share projected at $20–23B in 2026.

### 7.2 Dual-Pillar Strategy

```
TikTok Video Content
├── → TikTok Shop (In-App Cart Tag)
│     • 1-click native checkout
│     • Platform-funded discounts
│     • ~4.7% conversion rate
│     • Commission + fees apply
│
└── → Shopify Store (Bio Link / Ads / Search)
      • Owned customer data (email/phone/history)
      • Full margins
      • Email/SMS retention funnels
      • 100% merchant-controlled
```

### 7.3 Setup Workflow

1. **Register:** seller.tiktok.com → submit business entity details → set shipping profiles.
2. **Shopify:** Install official TikTok app → Connect TikTok for Business + Shop + Ad Account.
3. **Catalog:** Map SKUs to TikTok category tree; add weights/dimensions; configure brand.
4. **Link Account:** Seller Center > Linked Accounts > Link Official Account (QR scan).

### 7.4 Fee Structure (Verify in Seller Center)

| Fee | Rate | Notes |
| :--- | :--- | :--- |
| Platform Commission | ~8% (many categories) | Up from 5–6%; EU at ~9% since Jan 2026 |
| Payment Processing | ~2–2.9% + ~$0.30 | May be bundled |
| Affiliate Commissions | 5–20% | Seller-set; often needed for visibility |
| Refund Admin | ~20% of referral fee (capped ~$5) | Per returned order |
| Fulfilled by TikTok | $3–4+ per unit + storage | If using TikTok logistics |

**Model your true cost** = Commission + Processing + Affiliate + Avg Ad Spend per sale.

### 7.5 Advertising: GMV Max (Only Format)

> [!IMPORTANT]
> All legacy ad formats deprecated July 2025. GMV Max is the only TikTok Shop ad format.

```
GMV Max Campaign
├── Set: Daily Budget + Target ROI
├── Attribution: Paid + Organic + Affiliate (unified)
├── AI Handles: Creative selection, audience, placement
├── Creative Types: Video-to-LIVE, LIVE-to-LIVE, standard product video
└── Best Practices:
    ├── 15–50+ active videos in content library
    ├── Launch 5–7 days before major LIVE events
    └── ROI Protection: Credits if <90% daily target (20+ orders/day)
```

### 7.6 LIVE Shopping

- **60–70%** of US TikTok Shop GMV is affiliate-driven.
- LIVE events: **30–40% higher conversion** than standard video.
- Recommended cadence: **3+ LIVE sessions per week**.
- Run GMV Max LIVE-to-LIVE campaigns during active LIVE sessions.

### 7.7 Affiliate Program

| Type | Description |
| :--- | :--- |
| Open Collaboration | Any eligible creator (5K+ followers, 18+) can promote your products |
| Targeted Collaboration | Direct brand invitation at higher commission rates |
| Affiliate Creatives for Ads | Authorize affiliate content for TikTok Shop Ads with direct attribution |

### 7.8 Listing Policy Compliance (Active Enforcement June 2026)

- **Prohibited:** Absolute pricing claims, unsubstantiated medical/clinical claims, AI-fabricated product effects, AI-modified deceptive product images.
- **Required:** Brand Authorization via Qualification Center for trademarked products.
- **Enforcement:** Listing removal, demotion, or account freeze for violations.

---

## 8. Pinterest Shopping

*Full document:* [pinterest-shop-research.md](./research/pinterest-shop-research.md)

### 8.1 Why Pinterest Is Different

| Characteristic | Pinterest | Other Platforms |
| :--- | :--- | :--- |
| **User Mindset** | Active purchase planning & research | Passive entertainment |
| **Content Lifespan** | 4–12+ months (evergreen) | 24 hours to 7 days |
| **Discovery** | Keyword search + Visual Lens | Algorithmic feed |
| **Checkout** | Hosted Checkout (in-app, 2026) or Shopify direct | Varies |
| **Creator requirement** | No face camera; product/lifestyle imagery | Often requires on-camera presence |

### 8.2 Setup Requirements

- Pinterest Business Account at `business.pinterest.com`
- Claimed Shopify domain (DNS/HTML verification)
- Rich Pins activated (pulls live price/stock from Shopify)
- Official Pinterest app installed from Shopify App Store (handles Conversions API automatically)

### 8.3 Shopify Integration (Recommended: Official App)

The official Pinterest Shopify app (2026 capabilities):
- **Hosted Checkout:** Full in-app purchase without leaving Pinterest (April 2026). Orders auto-pushed to Shopify. Boosted organic distribution for participating pins.
- **Up to 20 product feeds:** Multiple markets, sub-brands, seasonal catalogs.
- **Near real-time sync:** Price and stock updates in minutes.
- **One-click Performance+ launch:** Start AI-powered ad campaigns from within the app.
- **Conversions API:** Server-side tracking handled automatically.

### 8.4 Pin Optimization

```
Optimized Pin Structure:
├── Image: 2:3 vertical (1000 × 1500 px) — strictly required
├── Visual: High-contrast product in lifestyle context + text overlay hook
├── Title: Primary keyword phrase + product name
├── Description: 200–300 words with natural keyword phrases
│   └── Find keywords via: Pinterest search bar predictions + Trends Tool
└── URL: Direct Shopify PDP with UTM tracking (not homepage)

Multi-Pin Strategy: Create 3–5 distinct visual angles per product.
Board Strategy: Specific niche boards (not broad categories).
```

### 8.5 2026 Platform Updates

| Update | Launch | Details |
| :--- | :--- | :--- |
| **Hosted Checkout** | April 2026 | In-app purchase; 3.9% lift in purchase propensity; boosts organic distribution |
| **20 Product Feeds** | April 2026 | Multi-market/sub-brand catalog support |
| **Visual Search Ads** | Sept 2026 | Ads in search results and Pin close-ups |
| **Performance+ NCA** | 2026 | New Customer Acquisition targeting; 64% avg increase in new-customer conversions |
| **Priority Products** | 2026 | AI prioritizes specific products within Performance+ |
| **Business Assistant** | Mid-2026 | AI tool in Ads Manager with data-backed campaign recommendations |
| **International Shopping** | June 2026 | Multi-country ads with auto-translation & currency conversion |
| **Top of Search Ads** | 2026 | First 10 search results; 45% of clicks |

### 8.6 Performance+ Advertising

```
Pinterest Performance+ Shopping Campaign
├── Launch: 1-click from Shopify-Pinterest app
├── AI Automates: Targeting, bidding, creative delivery, ad variation testing
├── Controls: Budget, ROAS target, Priority Products, NCA value rules
└── Best Practice: 
    ├── Quality CAPI signals (via official app)
    ├── Keyword-rich catalog = better AI targeting
    └── Organic pinning cadence builds algorithmic trust for paid performance
```

---

## 9. Cross-Platform Strategy

### 9.1 Channel Role Matrix

| Objective | Best Channel(s) | Why |
| :--- | :--- | :--- |
| **Viral product discovery** | TikTok, Instagram Reels | Algorithm-driven mass reach |
| **High-intent, evergreen traffic** | Pinterest | Search-intent visitors planning purchases |
| **Retargeting past visitors** | Meta (Facebook & Instagram) | Strongest retargeting capabilities |
| **Impulse purchases, LIVE selling** | TikTok Shop | Native in-app checkout, frictionless |
| **Brand storytelling, community** | Instagram, Facebook | Long-form carousel, Stories, community |
| **AI-driven product discovery** | All platforms + AI agents (via Shop Pay) | Shopify UCP + Muse AI |

### 9.2 Owned vs. Rented Audience — The Core Tension

```
RENTED (Platform-Controlled)         OWNED (Merchant-Controlled)
├── TikTok Shop in-app buyers        ├── Shopify email subscribers
├── Instagram followers              ├── SMS list
├── Facebook Page followers          ├── Direct Shopify customers
└── Pinterest followers              └── Loyalty program members

Bridging Strategy:
└── Platform purchase → Post-purchase packaging → Drive to Shopify
    → Capture email/SMS → Owned customer for life
```

### 9.3 Tracking & Data Setup Priority

Ensure server-side tracking is active across all channels (required after August 2026 Additional Scripts deprecation):

| Platform | Tracking Method | Setup |
| :--- | :--- | :--- |
| Meta (Facebook/Instagram) | Meta Pixel + Conversions API | Official Facebook & Instagram app (Maximum Data Sharing) |
| TikTok | TikTok Pixel + Events API | Official TikTok app (Web Pixel framework) |
| Pinterest | Pinterest Tag + Conversions API | Official Pinterest app (auto-configured) |

### 9.4 Content Repurposing Framework

```
Original Shopify Product
       │
       ├── TikTok: Raw, authentic video demo (organic first)
       │          └── → High performer? → Authorize for GMV Max
       │
       ├── Instagram: Polished lifestyle Reel (with product tag)
       │          └── → High performer? → Boost via Meta Ads Manager
       │
       ├── Pinterest: 3–5 static/video pins (lifestyle + detail shots)
       │          └── → Catalog entry drives evergreen search traffic
       │
       └── Facebook: Cross-post from Meta Business Suite (IG + FB)
                  └── → Add to ASC campaign as creative asset
```

---

## 10. Key Dates & Platform Timeline

| Date | Platform | Change |
| :--- | :--- | :--- |
| July 2025 | TikTok | GMV Max replaces all legacy ad formats |
| September 2025 | Meta | In-app checkout deprecated; website checkout mandatory |
| January 22, 2026 | TikTok | US ban resolved via ByteDance/USDS joint venture (80.1% US-owned) |
| January 2026 | TikTok | EU commission rates rise to ~9% for multiple categories |
| April 2026 | Pinterest | Hosted Checkout launched; 20 product feed limit |
| Early 2026 | Meta | Advantage+ Creative enabled by default; AI product summaries launched |
| Spring 2026 | Shopify | Agentic Commerce ("Everywhere") launch; UCP protocol open |
| June 2026 | Pinterest | International Shopping Ads (multi-country, auto-translation) |
| June 2026 | TikTok | Stricter listing policy enforcement begins (active, not passive) |
| July 2026 | TikTok | DOJ confirms US federal ban threat eliminated |
| July 2026 | Meta | Privacy control consolidation affecting off-platform data use |
| Mid-2026 | Pinterest | Pinterest Business Assistant AI launched in Ads Manager |
| Spring–Summer 2026 | Shopify | Additional Scripts deprecation warning period |
| August 26, 2026 | Shopify | Additional Scripts hard deprecated; Web Pixels mandatory |
| September 2026 | Pinterest | Visual Search Ads launched |
| September 8, 2026 | Meta | Muse AI Agent launched |
| September 23, 2026 | Meta | Meta Connect 2026: Muse + Ray-Ban glasses integration announced |
| October 30, 2026 | Meta | Consolidated commercial terms (Product Catalog + GenAI terms merge) |

---

## 11. References & Resources

### Video Resources
| Platform | Video | Link |
|----------|-------|------|
| Meta | The COMPLETE Meta Tutorial (Updated 2026) | https://www.youtube.com/watch?v=OE4WimLYVGE |
| Meta | The COMPLETE Meta Tutorial (Original) | https://www.youtube.com/watch?v=lIl6zNPyIEw |
| Instagram | How To SELL On Instagram in 2026 | https://www.youtube.com/watch?v=C4eyDXVorEo |
| Instagram | The Complete Instagram For Business Tutorial 2026 | https://www.youtube.com/watch?v=JkMhBKi12q4 |
| Instagram | How To Advertise on Instagram | https://www.youtube.com/watch?v=6VXC8N9wDVw |
| Instagram | Instagram Changed Everything Again: 2026 Updates | https://www.youtube.com/watch?v=dU_U1Pmmu5c |
| Facebook | Getting Facebook Shops Seen On Facebook Pages | https://www.youtube.com/watch?v=bo5ivXjEoek |
| Instagram | How to tag Shopify products on Instagram (Shorts) | https://www.youtube.com/shorts/vhZ-nuHKIzI |
| Instagram | Facebook & Instagram Shoppable Posts Made EASY | https://www.youtube.com/watch?v=Vj_cylLEPII |
| TikTok | How to Sell On TikTok Shop (Using Shopify) | https://www.youtube.com/watch?v=u4Su02rfokI |
| TikTok | Beyond TikTok Shop: How to Use TikTok to Drive Sales | https://www.youtube.com/watch?v=nIOn_726Rxk |
| TikTok | The Complete TikTok for Business Tutorial 2026 | https://www.youtube.com/watch?v=B8P9ErHGpxU |
| Pinterest | BEST way to use Pinterest to Get Sales on Shopify | https://www.youtube.com/watch?v=s_Ew0tXw8i4 |
| Pinterest | Automate Shopify to Pinterest | https://www.youtube.com/watch?v=e6oyxysXGwA |

### Official Platform Documentation
| Platform | Resource | URL |
|----------|----------|-----|
| Meta | Commerce Manager | https://www.facebook.com/commerce_manager |
| Meta | Business Suite | https://business.facebook.com |
| Meta | Advantage+ Shopping Campaigns | https://www.facebook.com/business/help/521329645890727 |
| Meta | Conversions API Setup | https://www.facebook.com/business/help/2041148702652965 |
| Meta | Commerce Platform (Developers) | https://developers.facebook.com/docs/commerce-platform |
| Meta | Commerce Eligibility Requirements | https://www.facebook.com/policies/commerce/requirements |
| Instagram | Set Up Instagram Shopping | https://help.instagram.com/1187859655048322 |
| Instagram | Tag Products | https://help.instagram.com/191462054687226 |
| TikTok | Seller Center | https://seller.tiktok.com |
| TikTok | GMV Max Help | https://ads.tiktok.com/help |
| TikTok | Affiliate Program | https://affiliate.tiktok.com |
| Pinterest | Business Hub | https://business.pinterest.com |
| Pinterest | Performance+ Documentation | https://help.pinterest.com/en/business/article/performance-plus |
| Pinterest | Hosted Checkout Blog Post | https://business.pinterest.com/en/blog/hosted-checkout |
| Pinterest | Claim Your Website | https://help.pinterest.com/en/business/article/claim-your-website |
| Shopify | Facebook & Instagram Sales Channel | https://help.shopify.com/en/manual/online-sales-channels/facebook-instagram |
| Shopify | TikTok Sales Channel | https://help.shopify.com/en/manual/online-sales-channels/tiktok |
| Shopify | Pinterest Sales Channel | https://apps.shopify.com/pinterest |
| Shopify | Customer Events (Web Pixels) | https://help.shopify.com/en/manual/promoting-marketing/pixels/overview |
| Shopify | Publishing to Sales Channels | https://help.shopify.com/en/manual/products/details/publishing |
