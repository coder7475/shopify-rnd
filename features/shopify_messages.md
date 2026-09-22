# Shopify Messaging — RND

> **App / System:** [Shopify Messaging](https://apps.shopify.com/email) *(formerly Shopify Email)*
> **Channels Supported:** Email, SMS, and WhatsApp
> **Cost:** Free monthly allowance for email (10,000 free/mo) + usage-based pricing; pay-per-message for SMS/WhatsApp
> **Access:** Shopify Admin → Marketing → Shopify Messaging (and Marketing → Automations)

---

## Overview

**Shopify Messaging** (the unified evolution and rebranding of **Shopify Email**) is Shopify's native multi-channel outbound marketing application. Built directly into the core Shopify admin, it enables merchants to create, automate, and track marketing campaigns across **Email**, **SMS**, and **WhatsApp** without exporting customer data to third-party tools.

Effective **March 24, 2026**, Shopify completed a structural consolidation:
- Native marketing automations built with Shopify Messaging emails live directly within the **Shopify Messaging app**.
- Complex, custom automations or workflows requiring third-party app actions are managed through **Shopify Flow**.

> [!NOTE]
> **Key Architectural Distinction:**
> - **Shopify Inbox:** Inbound, real-time, synchronous 1-on-1 customer chat and pre-purchase support on storefront and Shop app.
> - **Shopify Messaging:** Outbound, asynchronous, broadcast marketing campaigns and lifecycle trigger automations across Email, SMS, and WhatsApp.

---

## Multi-Channel Capabilities

| Channel | Core Use Case | Technical Infrastructure | Pricing Model |
|---|---|---|---|
| **Email** | Newsletters, product launches, editorial promotions, visual campaigns. | Native Shopify mail infrastructure; custom domain verification (DKIM/SPF/DMARC). | First **10,000 emails/month free**; ~$1 per 1,000 additional emails. |
| **SMS** | High-urgency flash sales, VIP early access, time-sensitive drops. | Carrier-compliant toll-free / 10DLC routing; requires separate explicit SMS consent. | Billed per message segment based on recipient destination & carrier fees. |
| **WhatsApp** | Conversational broadcast campaigns, high-touch regional outreach. | Meta Cloud API integration for authorized commercial templates. | Per-conversation / message pricing based on Meta regional rate cards. |

---

## Core Features & Mechanics

### 1. 📧 Email Marketing & Liquid Customization

- **Template Builder:** Drag-and-drop section builder with responsive previews for mobile and desktop screens.
- **Dynamic Store Integration:** Directly insert product cards, collection grids, discount badges, and store policies without manual copy-pasting of URLs or product imagery.
- **Liquid Code Support:** Advanced developers and merchants can insert **Liquid syntax directly into email templates**, allowing dynamic conditional blocks (e.g., displaying custom customer metafields, loyalty tiers, or localized content).
- **Domain Authentication:** Direct setup of SPF, DKIM, and DMARC records in **Settings → Notifications** ensures high inbox deliverability and reduces spam placement.

---

### 2. 📱 SMS Marketing Architecture & Compliance

- **Dedicated Toll-Free Numbers:** In the US and Canada, SMS marketing operates via registered toll-free numbers, ensuring carrier compliance under CTIA/TCPA regulations.
- **Independent Consent Capture:** Customers must provide explicit, separate opt-in for SMS marketing. Email consent does not cover SMS.
- **Opt-Out Handling:** Automated `STOP` keyword processing for instant subscriber unsubscription, maintaining strict regulatory compliance.
- **Single-Click Checkout Links:** SMS messages automatically generate shortened, tracked checkout links with pre-applied promotional codes.

---

### 3. ⚙️ Native Marketing Automations

Shopify Messaging includes pre-configured automation recipes triggered by real-time customer and checkout events.

```
Trigger Event (e.g., Checkout Abandoned)
        ↓
Wait Delay (e.g., 1 Hour)
        ↓
Condition Check (e.g., Has customer completed order?)
   ├── YES ──> [Terminate Flow]
   └── NO  ──> Send Shopify Messaging Email / SMS with dynamic cart link
```

**Standard Native Automations:**
- **Abandoned Checkout Recovery:** Reclaims lost carts by sending automatic reminders with a persistent cart link.
  - > [!IMPORTANT]
    > **Abandoned checkout emails are 100% FREE** and do not count against your 10,000 monthly email quota.
- **Welcome Series:** Triggered when a new subscriber signs up via storefront forms or checkout marketing opt-in.
- **First-Purchase Upsell / Post-Purchase Thank You:** Triggered upon order fulfillment to introduce complementary products or collect feedback.
- **Customer Win-Back:** Re-engages customers who have not placed an order in 60, 90, or 120 days.
- **Browse Abandonment:** Sends reminders to subscribed customers who viewed specific products but did not initiate checkout.

---

### 4. 🎯 Customer Segmentation & Smart Delivery

Campaigns leverage Shopify's native **Customer Segmentation engine** (`Customers → Segments`):

**Grounded Segmentation Criteria:**
- **Purchase Behavior:** Number of orders (`orders_count >= 3`), total spend (`total_spent > 150`), specific product purchased, last order date.
- **Engagement History:** Subscribers who opened or clicked an email in the last 30/60/90 days.
- **Geographic Location:** Target by country, province/state, or language locale.
- **Customer Tags & Metafields:** Filter by custom wholesale tags, VIP designations, or loyalty club tiers.

**Smart Delivery Optimization:**
Shopify Messaging includes algorithmic send prioritization:
- Intelligently paces delivery and optimizes dispatch times.
- Filters out inactive or invalid addresses, reducing bounce rates and preserving sender domain reputation.

---

### 5. 📝 List Building Integration with Shopify Forms

Shopify Messaging connects seamlessly with **Shopify Forms** (the native lead generation tool):
- Deploy floating popups, sticky banners, or embedded newsletter signup forms.
- Form submissions automatically apply subscriber tags and route subscribers directly into targeted segments for immediate welcome automations.

---

## Pricing & Plan Quotas

### Email Pricing (2025/2026 Structure)

| Monthly Email Volume | Cost |
|---|---|
| **First 10,000 emails / calendar month** | **$0.00 (Free across all paid plans)** |
| 10,001 – 300,000 emails | **$1.00 per 1,000 additional emails** |
| 300,001 – 750,000 emails | **$0.65 per 1,000 additional emails** |
| 750,001+ emails | **$0.55 per 1,000 additional emails** |

*Notes:*
- Unused free emails do not roll over to subsequent months.
- Abandoned checkout recovery emails are exempt from the quota.
- Overages are automatically billed to your monthly Shopify subscription invoice.

### SMS & WhatsApp Pricing
- Billed per sent message segment based on recipient country rates and carrier fees.
- US/Canada merchants incur standard monthly fees for dedicated toll-free marketing numbers.
- Detailed real-time rate cards are displayed in **Settings → Billing**.

---

## Analytics & Attribution Reporting

The **Email Performance Report** and **Campaign Summary** provide closed-loop attribution based on first-party store data:

**Core Metrics Tracked:**
- **Delivery Rate & Bounces:** Percentage of messages successfully accepted by recipient mail servers.
- **Open Rate:** Unique opens / delivered messages (subject to Apple Mail Privacy Protection adjustments).
- **Click-Through Rate (CTR):** Percentage of recipients clicking embedded product and CTA links.
- **Conversion Rate & Attributed Revenue:** Tracks direct orders and revenue generated within the attribution window following a message click.
- **Unsubscribe Rate & Spam Complaints:** Real-time health metrics to safeguard domain reputation.

**Performance Diagnostics:**

| Metric Pattern | Diagnosis | Recommended Remedy |
|---|---|---|
| Open rate < 18% | Weak subject lines or deliverability issues | Test curiosity/benefit subject lines; verify SPF/DKIM/DMARC in DNS settings. |
| High open rate, low CTR (< 1.5%) | Offer disconnect or weak CTA | Improve CTA button contrast; add direct product cards; reduce body length. |
| High unsubscribe rate (> 0.4%) | Over-messaging or list fatigue | Adjust send frequency; segment by recent engagement (opened in last 60 days). |
| High bounce rate | Outdated/stale list | Clean customer list; verify that double opt-in is active on forms. |

---

## Native Shopify Messaging vs. Third-Party Platforms

| Feature / Metric | Shopify Messaging | Klaviyo / Omnisend |
|---|---|---|
| **Cost** | 10,000 free emails/mo; ~$1/1k overage | Paid tiered pricing ($20 – $1,500+/mo based on list size) |
| **Setup & Integration** | Zero setup; 100% native database integration | Requires script installation, webhook sync, and API keys |
| **Catalog Sync** | Real-time, instant product data and pricing | Periodic API sync |
| **Complex Branching** | Handled natively or escalated to Shopify Flow | Multi-conditional visual flow builders with split branching |
| **Liquid Support** | ✅ Direct Liquid coding in templates | ⚠️ Proprietary template syntax |
| **Predictive Analytics** | Basic RFM segmentation | Predictive CLV, churn risk, and expected date of next order |
| **Best For** | Early to mid-tier merchants seeking simplicity, low cost, and unified admin | High-volume merchants requiring advanced predictive retention workflows |

---

## Official References

- [Shopify Help: Shopify Messaging Overview](https://help.shopify.com/en/manual/promoting-marketing/create-marketing/shopify-email)
- [Shopify Help: Pricing and Billing for Shopify Email/Messaging](https://help.shopify.com/en/manual/promoting-marketing/create-marketing/shopify-email/email-pricing)
- [Shopify Help: Marketing Automations](https://help.shopify.com/en/manual/promoting-marketing/marketing-automations)
- [Shopify Help: Setting Up SMS Marketing](https://help.shopify.com/en/manual/promoting-marketing/create-marketing/sms-marketing)
- [Shopify Help: Customer Segmentation Engine](https://help.shopify.com/en/manual/customers/customer-segmentation)
