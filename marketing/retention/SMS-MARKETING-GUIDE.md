# SMS Marketing for Shopify: The Complete Guide

> A comprehensive, data-backed guide to SMS marketing for Shopify stores — covering business fundamentals, legal compliance, sender registration (Toll-Free, 10DLC, Short Codes), pricing structures, native vs. scaling apps, high-converting automation flows, and best practices. Grounded in official Shopify documentation, carrier registry standards, and creator benchmarks verified for **October 2026**.

---

## Table of Contents

1. [What Is SMS Marketing?](#what-is-sms-marketing)
2. [Why SMS Marketing Matters for Shopify](#why-sms-marketing-matters-for-shopify)
3. [How SMS Marketing Works on Shopify](#how-sms-marketing-works-on-shopify)
4. [Sender Number Types & Verification Process](#sender-number-types--verification-process)
   - [Toll-Free Number Verification (TFV)](#toll-free-number-verification-tfv)
   - [A2P 10DLC Registration](#a2p-10dlc-registration)
   - [Dedicated Short Codes](#dedicated-short-codes)
5. [SMS Marketing Tools & Platforms](#sms-marketing-tools--platforms)
   - [Tier 1: Built-In / Native Shopify Tools](#tier-1-built-in--native-shopify-tools)
   - [Tier 2: Dedicated Shopify SMS & Omnichannel Apps](#tier-2-dedicated-shopify-sms--omnichannel-apps)
   - [Tier 3: Specialized & Conversational SMS Tools](#tier-3-specialized--conversational-sms-tools)
6. [Pricing & Cost Breakdown (October 2026 Verified)](#pricing--cost-breakdown-october-2026-verified)
   - [Platform Fees & Monthly Subscriptions](#platform-fees--monthly-subscriptions)
   - [Per-Message & Carrier Pass-Through Rates](#per-message--carrier-pass-through-rates)
   - [Total Estimated Monthly Spend across Store Tiers](#total-estimated-monthly-spend-across-store-tiers)
7. [Setting Up Your First SMS Campaign](#setting-up-your-first-sms-campaign)
8. [Essential SMS Automation Flows](#essential-sms-automation-flows)
9. [Segmentation & List Growth Strategies](#segmentation--list-growth-strategies)
10. [SMS Copywriting & Technical Best Practices](#sms-copywriting--technical-best-practices)
11. [Legal Compliance & Carrier Regulations](#legal-compliance--carrier-regulations)
    - [TCPA, Quiet Hours & State Mini-TCPAs](#tcpa-quiet-hours--state-mini-tcpas)
    - [CTIA Guidelines & Prohibited SHAFT Content](#ctia-guidelines--prohibited-shaft-content)
    - [FCC Opt-Out & Revocation Mandates](#fcc-opt-out--revocation-mandates)
12. [Measuring Performance & ROI](#measuring-performance--roi)
13. [Advanced Strategies](#advanced-strategies)
14. [References & Sources](#references--sources)

---

## What Is SMS Marketing?

SMS (Short Message Service) marketing is the practice of sending permission-based, direct text messages to subscribers' mobile phones to share promotions, order updates, abandoned cart reminders, and conversational customer support. For ecommerce stores, it operates as a high-urgency, personal companion channel to email.

While email excels at long-form brand storytelling and visual merchandising, SMS commands instantaneous attention:
- **90%+ of text messages** are read within **3 minutes** of receipt.
- Nearly **one-third (32%)** of consumers view text alerts immediately upon delivery.
- Average response times hover around **90 seconds** compared to 90 minutes for email.

Unlike ad networks where platform algorithms govern reach and ad delivery costs fluctuate, an SMS subscriber list represents owned distribution. However, because text messaging enters a customer’s intimate mobile inbox, it requires explicit, legally compliant opt-in and strict message pacing.

### Core Message Architectures

| Message Type | Technical Specifications | Cost Multiplier | Best Use Case |
|---|---|---|---|
| **SMS (Plain Text)** | Standard GSM-7 encoding allows up to **160 characters** per segment. Messages with special characters or emojis switch to UCS-2 encoding (**70 characters** per segment). Concatenated texts consume 153 characters (GSM-7) or 67 characters (UCS-2) per segment. | 1× base rate | Time-sensitive flash alerts, cart recovery links, shipping confirmations, two-way conversational replies. |
| **MMS (Multimedia)** | Includes media attachments (images, GIFs, vCards) and allows up to **1,600 characters** in a single delivery payload. | 3× to 5× base SMS rate | Product drops, visual cart recovery, VIP lookbooks, seasonal holiday announcements. |
| **RCS (Rich Communication Services)** | Interactive cards, verified brand checkmarks, interactive action buttons, and high-res carousels over cellular data or Wi-Fi. Supported by modern Android devices and Apple iOS 18+. | Standard SMS or dedicated RCS rate | Rich brand experiences, direct two-way ordering, interactive product carousels. |

---

## Why SMS Marketing Matters for Shopify

### The Numbers Don't Lie

Data compiled from verified enterprise aggregate reports (Omnisend 2026 Ecommerce Report, Postscript Merchant Benchmarks across 17,000+ Shopify stores, and Klaviyo Marketing Benchmarks):

- **High Engagement CTR:** Automated SMS flows achieved an average **20.32% CTR** across ecommerce stores, compared to broad scheduled campaigns at **12.39% CTR** ([Omnisend 2026](https://www.omnisend.com/blog/sms-marketing-statistics/)).
- **Conversion Multiplier:** Automated SMS sequences convert at **0.77%–0.78% of all delivered messages** (over 6× higher than blast campaigns at 0.12%). Among shoppers who click an SMS automation link, click-to-conversion rates reach **3.81%** ([Omnisend 2026](https://www.omnisend.com/blog/sms-marketing-statistics/)).
- **Revenue Per Send:** Automated SMS delivers an average of **$0.74 to $0.98 in revenue per message** sent, with top-quartile Shopify brands exceeding **$2.13 per message** and 90th percentile stores generating **$4.54 per message** ([Postscript Benchmarks](https://postscript.io/pricing); [Omnisend 2026](https://www.omnisend.com/blog/sms-marketing-statistics/)).
- **Omnichannel Multiplier:** Ecommerce brands utilizing integrated SMS alongside email generated **202% more revenue** on average than stores relying exclusively on email ([Omnisend 2026](https://www.omnisend.com/blog/sms-marketing-statistics/)).
- **Cart Recovery Efficiency:** Klaviyo benchmark data shows SMS abandoned cart recovery flows drive a median **10.3% click rate** and an average of **$4.48 in revenue per recipient** ($8.69 for top 10% stores).

### Why SMS Complements Email for Shopify

```
┌──────────────────────────────────────────────────────────┐
│                      THE DUAL FUNNEL                     │
├────────────────────────────┬─────────────────────────────┤
│      EMAIL MARKETING       │        SMS MARKETING        │
├────────────────────────────┼─────────────────────────────┤
│ • Low marginal send cost   │ • Premium per-message cost  │
│ • Long-form brand stories  │ • 160-character immediacy   │
│ • Rich catalogs & visuals  │ • Direct, 90-second urgency │
│ • Nurturing & education    │ • High-intent triggers      │
│ • 15%–25% open rates       │ • 98% estimated read rates  │
└────────────────────────────┴─────────────────────────────┘
```

1. **Urgency & Exclusivity:** Flash sales, back-in-stock alerts, and VIP early access convert fastest when delivered straight to lock screens.
2. **Salvaging Cart Abandonment:** Shoppers distracted during checkout often miss emails until hours later. An SMS ping within 30 to 60 minutes captures real-time intent before momentum fades.
3. **Conversational Support:** Two-way SMS allows merchant agents or automated AI shopping assistants to answer sizing, shipping, or compatibility questions, resolving purchase hesitations instantly.

### Creator & Operator Insights

From top Shopify marketing strategists and agency leaders:

> *"Do not use SMS as a high-frequency newsletter channel. If you send nurture content over SMS, expect your unsubscribe rate to skyrocket to 3%–5%. SMS should be reserved for high-leverage, urgent events: product drops, back-in-stock notifications, VIP sales, and immediate recovery flows."*  
> — Max Sturtevant, Founder of Wellcopy ([YouTube Reference](https://www.youtube.com/watch?v=5avcX6rqjD8))

> *"Growing your SMS list is useless if you don't collect proper legal opt-in. A single non-compliant opt-in form can lead to devastating TCPA penalties. Compliance and clear expectations must lead every subscriber interaction."*  
> — Dylan, Lead Strategist at SlickText ([YouTube Reference](https://www.youtube.com/watch?v=GDVap6uWEr8))

---

## How SMS Marketing Works on Shopify

SMS marketing integrates directly with your Shopify store data via Shopify webhooks, APIs, and native checkout hooks.

```
1. Explicit Opt-In Collection
   → Shopify Checkout (pre-unchecked checkbox), On-site Popups, Two-Step Tap-to-Text
        ↓
2. Verification & Consent Ledger
   → Timestamped consent logged in Shopify Customers API / App Database
        ↓
3. Segmentation & Logic Filtering
   → Filtered by purchase recency, country, quiet-hours timezone, and engagement
        ↓
4. Message Execution (Toll-Free, 10DLC, or Short Code)
   → Routing through verified carrier gateways with mandatory opt-out syntax
        ↓
5. Direct Revenue Attribution
   → Tracked via UTM parameters, Shopify discount codes, and 24-hr click attribution windows
```

### Native Checkout Integration

Shopify natively captures SMS consent at checkout. When configured:
- Customers enter their mobile number during the shipping information step.
- A dedicated, **unchecked** checkbox asks for explicit marketing consent (e.g., *"Sign me up for exclusive mobile offers and updates via text"*).
- Shopify updates the customer record's `sms_marketing_consent` state (`subscribed`, `unsubscribed`, or `not_subscribed`) with legal opt-in timestamps.

---

## Sender Number Types & Verification Process

Sending application-to-person (A2P) commercial SMS messages in the United States and Canada requires identity verification. Unregistered numbers are strictly blocked by major wireless carriers (AT&T, Verizon, T-Mobile).

```
                      SENDER NUMBER HIERARCHY
┌────────────────────┬────────────────────┬────────────────────┐
│     TOLL-FREE      │      A2P 10DLC     │     SHORT CODE     │
│   (1-800, 1-888)   │   (Local 10-Digit) │    (5-6 Digits)    │
├────────────────────┼────────────────────┼────────────────────┤
│ • $2.15/mo lease   │ • $1.15/mo lease   │ • $1,000–$1,500/mo │
│ • 2–5 days approval│ • Brand + Campaign │ • 6–12 weeks setup │
│ • Best for SMBs &  │ • Best for local   │ • High volume      │
│   mid-sized brands │   trust & brands   │   (500k+ msgs/mo)  │
└────────────────────┴────────────────────┴────────────────────┘
```

---

### Toll-Free Number Verification (TFV)

A Toll-Free Number (TFN) starts with prefixes like 800, 888, 877, 866, 855, 844, or 833. It is the primary, standard sending number deployed by **Shopify Messaging, Postscript Starter/Growth, and Klaviyo**.

#### 1. Why Registration Is Mandatory
Since **January 31, 2024**, wireless carriers enforce full blocking on all unregistered toll-free messaging traffic. Unverified numbers receive error code 30032 and zero messages are delivered.

#### 2. Information Required for Submission
To submit a toll-free registration application via Shopify Messaging or third-party apps, you must provide:
- **Legal Business Details:** Official legal entity name, operating DBA, physical headquarters address, business website URL, and primary contact details.
- **Business Registration Identifier:** Employer Identification Number (**EIN**) for US entities, or Business Number (BN) for Canadian corporations.
- **Public Policy URLs:** Working, publicly accessible direct links to your store's **Privacy Policy** and **Terms of Service**.
- **Opt-In Demonstration:** A live, publicly viewable URL showing a screenshot of your exact opt-in mechanism (e.g., website popup, checkout checkbox, or in-store form) displaying full mandatory legal disclosures.
- **Sample Message Templates:** Verbatim text examples of promotional and transactional messages including store branding and opt-out instructions (e.g., *"BrandName: Hey [Name], your cart is waiting! Use code SAVE10: [Link]. Reply STOP to opt out, HELP for help."*).

#### 3. Approval Timeline & Costs
- **Approval Window:** 2 to 5 business days (standard submission).
- **Leasing Fee:** **$2.15 USD per month** billed directly on your Shopify or telecom platform invoice.
- **Resubmission Grace Period:** If an application is rejected due to missing disclosures or broken links, carriers typically permit priority resubmission within 7 days.

---

### A2P 10DLC Registration

Application-to-Person 10-Digit Long Code (10DLC) allows businesses to broadcast commercial texts using standard local telephone numbers (e.g., 212-XXX-XXXX, 312-XXX-XXXX). Registration is administered by **The Campaign Registry (TCR)**.

#### Fee Schedule (Verified 2026 TCR / Carrier Rates)

| Registration Phase | Cost (USD) | Frequency | Description |
|---|---|---|---|
| **Standard Brand Registration** | **$44.00** | One-time | Upfront identity vetting for registered corporate entities with an active EIN. |
| **Low-Volume Standard Brand** | **$4.00** | One-time | Available for smaller brands sending fewer than 6,000 message segments per day. |
| **Sole Proprietor Brand** | **$4.00** | One-time | Designed for unincorporated single operators without an EIN (capped at 1,000 msgs/day on T-Mobile). |
| **Campaign Vetting Fee** | **$15.00** | One-time | External vetting fee per approved use-case campaign. |
| **Monthly Campaign Maintenance** | **$1.50 – $10.00** | Monthly | Recurring monthly fee based on campaign type (standard marketing vs. 2FA/mixed). |
| **Local 10DLC Number Lease** | **$1.15** | Monthly per number | Monthly number reservation charge. |

*Timeline: Standard campaign approvals average 3 to 7 business days.*

---

### Dedicated Short Codes

Dedicated Short Codes are 5- to 6-digit numbers (e.g., `84421`, `72345`) tailored for large enterprise stores transmitting massive message volumes.

- **Random Short Code Lease:** **$1,000.00 USD per month** (billed quarterly in advance).
- **Vanity Short Code Lease:** **$1,500.00 USD per month** (custom memorable digits, billed quarterly).
- **One-Time Setup Fee:** Typically **$500 to $1,000** for carrier provisioning.
- **Provisioning Window:** **6 to 12 weeks** due to manual audit across AT&T, Verizon, and T-Mobile networks.
- **Throughput Advantage:** Delivers **100 to 500+ messages per second**, eliminating carrier queuing during high-stakes sales events like Black Friday / Cyber Monday (BFCM).

---

## SMS Marketing Tools & Platforms

### Tier 1: Built-In / Native Shopify Tools

| App | App Store Rating & Reviews | Best For | Number Type | Starting Monthly Price | Per-Message US Cost |
|---|---|---|---|---|---|
| **Shopify Messaging (Native SMS)** | **4.8★** (4,590+ reviews) | Beginners & lean stores seeking a built-in admin solution | Toll-Free (US/CA) or Alphanumeric Sender (UK/EU) | **$0 / month** (plus **$2.15/mo** toll-free number lease) | Pay-as-you-go usage (~$0.012/SMS); 25 free test messages/week |

#### Why Start with Shopify Messaging?
- **Zero Third-Party Apps:** Operates directly inside your Shopify Admin under **Marketing → Campaigns**.
- **Unified Billing:** Messaging fees appear alongside your standard Shopify subscription.
- **Pre-Built Store Sync:** Automatically links with Shopify Customer Segments and Shopify Flow automations.

---

### Tier 2: Dedicated Shopify SMS & Omnichannel Apps

| App | App Store Rating & Reviews | Best For | Number Type | Starting Monthly Price | Per-Message US Base Cost | Carrier Fees Included? |
|---|---|---|---|---|---|---|
| **Postscript** | **4.7★** (1,200+ reviews) | Shopify-focused brands prioritizing dedicated SMS and AI flows | Dedicated Toll-Free or Short Code | **Free to install** ($49/mo minimum spend; $100 free trial credits) | Starter: **$0.009 / SMS**, **$0.045 / MMS**; Growth: **$0.008 / SMS** ($100/mo); Pro: **$0.007 / SMS** ($500/mo) | No (+ pass-through fees) |
| **Klaviyo** | **4.7★** (3,350+ reviews) | Omnichannel stores pairing sophisticated email and SMS data | Toll-Free or Short Code | **Free tier** (up to 250 profiles, $5 monthly mobile credits); Paid SMS starts at **$15/mo** (up to 1,250 credits) | ~$0.012/credit on entry tiers; sliding volume rates | **Yes** (carrier fees bundled into rates) |
| **Omnisend** | **4.7★** (3,100+ reviews) | Integrated email, SMS, and push for international stores | Toll-Free & Global alphanumeric | Free email plan; SMS available on Pro plan (**$41.30/mo**) | **From $0.007 / SMS** (tiered by high-volume credits) | Bundled in credit tiers |
| **TxtCart AI** | **4.9★** (540+ reviews) | Conversational cart recovery powered by automated human/AI agents | Toll-Free & 10DLC | **Free to install** ($29/mo min spend; $500 free trial credits); Growth: **$79/mo**; Pro: **$399/mo** | Usage-based rates + carrier fees; **$0.99** per resolved AI cart order | No (+ pass-through fees) |
| **Yotpo SMS & Email** *(formerly SMSBump)* | **4.7★** (Shopify App Store) | Stores utilizing the unified Yotpo loyalty and review ecosystem | Toll-Free & Short Code | Free-to-install tier; Growth tiers from **$19–$29/mo** | **~$0.015 / SMS**, **~$0.045 / MMS** on entry tiers | No (+ pass-through fees) |

---

### Tier 3: Specialized & Conversational SMS Tools

| App | Best For | Starting Monthly Price | Key Features |
|---|---|---|---|
| **Attentive** | High-growth enterprise merchants ($10M+ ARR) | Custom pricing (~$300–$500/mo base; 6–12 mo contracts; $2k+ quarterly commitments) | Patented two-tap mobile sign-up units, concierge team, enterprise short-code throughput. |
| **Recart** | Fully managed SMS operations for mid-market merchants | **From $299 / month** | Dedicated SMS strategist, managed compliance, end-to-end campaign creation and revenue optimization. |
| **Emotive** | Conversational sales and two-way human agent texting | **From $100 / month** ($0.015/SMS; $0.025/MMS) | Live chat-style inbox, dedicated sales agents handling inbound product questions over text. |
| **Twilio API (Custom)** | Headless Shopify stores and custom enterprise tech stacks | Pay-as-you-go (**$0.0083 / SMS**, **$0.022 / MMS**, $2.15/mo TFN) | Full programmatic control, custom carrier routing, webhook-driven automations. |

---

## Pricing & Cost Breakdown (October 2026 Verified)

SMS marketing pricing contains three separate billing layers:
1. **Platform Subscription / Minimum Spend:** Monthly fee charged by the software provider.
2. **Base Per-Message Fee:** The rate charged per SMS segment or MMS image.
3. **Carrier Pass-Through Fees:** Non-negotiable surcharges levied directly by cellular networks (AT&T, Verizon, T-Mobile) and collected by your SMS app.

---

### Carrier Pass-Through Surcharges (US Carriers)

Verified carrier pass-through fees per outbound message segment across US networks:

| Wireless Carrier | Outbound Toll-Free SMS | Outbound Toll-Free MMS | Outbound 10DLC SMS | Outbound 10DLC MMS |
|---|---|---|---|---|
| **AT&T** | **$0.0035** | **$0.0090** | **$0.0035** | **$0.0090** |
| **T-Mobile** *(incl. Sprint)* | **$0.0045** | **$0.0100** | **$0.0045** | **$0.0100** |
| **Verizon Wireless** | **$0.0050** | **$0.0070** | **$0.0050** | **$0.0070** |
| **US Cellular** | **$0.0045** | **$0.0100** | **$0.0050** | **$0.0100** |
| **Other Regional Carriers** | **$0.0042** | **$0.0100** | **$0.0042** | **$0.0100** |

> [!NOTE]
> On average across a blended US subscriber base, carrier pass-through fees add approximately **$0.0042 to $0.0045 per SMS** and **$0.0085 to $0.0095 per MMS**. When comparing tools, check whether carrier surcharges are bundled (as in Klaviyo) or billed separately (as in Postscript and TxtCart).

---

### Total Estimated Monthly Spend across Store Tiers

```
ESTIMATED MONTHLY SMS BUDGETS (US MARKET)
┌─────────────────────────────────────────────────────────────┐
│ 1. New Store (<500 Subscribers, ~1,000 msgs/mo)            │
│    • App/Platform: $0 – $49/mo                              │
│    • Toll-Free Number: $2.15/mo                             │
│    • Messages + Carrier Fees: ~$13 – $15                    │
│    TOTAL: ~$15 to $50 / month                               │
├─────────────────────────────────────────────────────────────┤
│ 2. Growing Store (2,500 Subscribers, ~6,000 msgs/mo)        │
│    • App/Platform: $49 – $100/mo                            │
│    • Toll-Free Number: Included or $2.15/mo                 │
│    • Messages + Carrier Fees: ~$75 – $85                    │
│    TOTAL: ~$125 to $185 / month                             │
├─────────────────────────────────────────────────────────────┤
│ 3. Scaling Brand (10,000 Subscribers, ~25,000 msgs/mo)      │
│    • App/Platform: $100 – $250/mo                           │
│    • Number Maintenance: Included                           │
│    • Messages + Carrier Fees: ~$300 – $340                  │
│    TOTAL: ~$400 to $590 / month                             │
├─────────────────────────────────────────────────────────────┤
│ 4. High-Volume Brand (50,000 Subscribers, ~120,000 msgs/mo) │
│    • App/Platform: $500/mo (or Short Code: $1,000/mo)       │
│    • Messages + Carrier Fees: ~$1,400 – $1,600              │
│    TOTAL: ~$1,900 to $2,600 / month                         │
└─────────────────────────────────────────────────────────────┘
```

---

## Setting Up Your First SMS Campaign

### Step-by-Step Implementation Guide

```
Step 1: Install Selected SMS Application
  → Choose Shopify Messaging (lean/native) or Postscript / Klaviyo (dedicated flows).
Step 2: Submit Toll-Free Registration (TFV)
  → Complete business verification form; provide legal EIN, Privacy URL, and opt-in image.
Step 3: Activate Checkout Opt-In
  → In Shopify Admin: Settings → Checkout → Marketing Options → Check SMS marketing.
Step 4: Design Dual-Consent Website Popups
  → Configure on-site modal: Step 1 collects Email, Step 2 collects Mobile Phone.
Step 5: Configure TCPA & CTIA Required Disclosures
  → Ensure explicit opt-in text, message frequency notice, and STOP/HELP language appear.
Step 6: Build Your Initial Cart Recovery Automation
  → Activate a 30-to-60 minute post-abandonment SMS trigger.
Step 7: Execute a Test Broadcast
  → Send a test SMS to an internal device; confirm link tracking, quiet hours, and STOP response.
```

### Quick-Start Compliance Checklist

- [ ] Unchecked checkout consent checkbox enabled in Shopify admin.
- [ ] Direct Privacy Policy link and Terms of Service updated with mobile messaging disclosures.
- [ ] Toll-free number registration submitted and status confirmed as **Verified**.
- [ ] Automated quiet hours enabled (**9:00 AM to 8:00 PM** recipient local time).
- [ ] Automatic replies verified for mandatory keywords: **STOP**, **HELP**, **INFO**, **CANCEL**.
- [ ] Branded sender identification placed at the very start of message copy (e.g., `BrandName:`).

---

## Essential SMS Automation Flows

Automated flows generate **$0.74 to $0.98 per send** — nearly 5× to 6× the revenue per message of manual broadcast campaigns.

---

### 1. Welcome Flow (New Subscriber)

**Objective:** Acknowledge new subscribers immediately, deliver promised incentive codes, and encourage an initial order.

```
Trigger: Customer submits SMS opt-in form
Delay: Immediate (0–2 minutes)
```

- **Message Content:**  
  `[Brand]: Welcome to the inner circle! Use code WELCOME15 for 15% off your first purchase: [Shortened Link]. Reply HELP for help, STOP to opt out.`
- **Performance Targets:**  
  - Click-Through Rate: **25% – 35%**  
  - Conversion Rate: **4% – 8%**  
  - Revenue per Send: **$1.50 – $3.00**

---

### 2. Abandoned Checkout Recovery

**Objective:** Recapture high-intent shoppers who entered their shipping information but left before payment.

```
Sequence Schedule:
  • Message 1: 30–60 minutes after abandonment (Helpful nudge)
  • Message 2 (Optional): 24 hours later (Urgency / Social proof / Incentive)
```

| Step | Delay | Message Copy Example |
|---|---|---|
| **SMS 1** | 45 minutes | `[Brand]: Hey [First_Name], did life get in the way? Your cart is reserved and ready to ship here: [Cart_Link]. Text STOP to opt out.` |
| **SMS 2** | 24 hours | `[Brand]: Still thinking it over? Take 10% off your cart today with code TAKE10: [Cart_Link]. Offer expires at midnight. Text STOP to opt out.` |

> [!TIP]
> Keep your abandoned checkout flow to **at most two text messages**. Sending three or more SMS reminders for a single cart results in unsubscribe rates above 3% and carrier spam flags.

---

### 3. Browse Abandonment Flow

**Objective:** Target logged-in or cookied subscribers who viewed a specific product page 2+ times without adding items to their cart.

- **Delay:** 2 to 4 hours post-session.
- **Message Content:**  
  `[Brand]: Eyeing the [Product_Name]? It's one of our community favorites this week. Check details & sizing here: [Product_Link]. Text STOP to opt out.`
- **Strategy:** Never discount immediately on browse abandonment. Provide educational value, social proof, or sizing assistance first.

---

### 4. Post-Purchase & Shipping Confirmation

**Objective:** Reassure buyers with real-time transactional updates and prepare them for replenishment.

- **Trigger:** Fulfillment update from Shopify (`Order Fulfilled`).
- **Transactional Copy:**  
  `[Brand]: Great news! Your order #[Order_Number] is packed and on its way. Track tracking updates live: [Tracking_Link].`
- **Follow-Up (7–14 days post-delivery):**  
  `[Brand]: How are you enjoying your [Product_Name]? Tap here to drop a review and get 50 loyalty points: [Review_Link]. Text STOP to opt out.`

---

### 5. High-Value VIP & Back-In-Stock Alerts

**Objective:** Notify high-intent subscribers the moment sold-out inventory returns.

- **Performance Benchmarks:** Postscript merchant data reveals back-in-stock alerts achieve peak engagement with **36.7% to 58.7% CTR**.
- **Message Content:**  
  `[Brand]: Back in stock! The [Product_Name] you were waiting for is finally here, but quantities are limited: [Link]. Reply STOP to opt out.`

---

## Segmentation & List Growth Strategies

### High-Converting List Growth Tactics

```
┌────────────────────────────────────────────────────────┐
│              PROVEN LIST GROWTH PLAYBOOK               │
├────────────────────────────────────────────────────────┤
│ 1. Two-Step Popups (Desktop & Mobile)                  │
│    • Step 1: Collect Email (10% discount)              │
│    • Step 2: "Unlock Free Shipping" by entering SMS    │
│    • Converts 6%–12% of total store visitors           │
├────────────────────────────────────────────────────────┤
│ 2. Seamless Tap-to-Text (Mobile Web)                   │
│    • Single tap opens pre-filled SMS on customer phone │
│    • Customer sends pre-written keyword (e.g., "DEAL") │
│    • Eliminates phone number typing errors entirely    │
├────────────────────────────────────────────────────────┤
│ 3. Shopify Native Checkout Opt-In                      │
│    • Captures active buyers at peak purchase intent    │
│    • Requires pre-unchecked legal compliance box       │
└────────────────────────────────────────────────────────┘
```

### Essential Smart Segments

Avoid sending batch campaigns to your entire list. Segment by engagement and buyer history:

1. **Engaged VIPs:** Customers who have ordered 3+ times or spent over $250 in the last 180 days. Use for early product drop access.
2. **60-Day Active Non-Buyers:** Subscribers who joined within 60 days, click links, but have not yet purchased. Send time-limited incentive offers.
3. **Cart Abandoners with High Value:** Carts exceeding your average order value (AOV) by 25%+. Send rich MMS messages with direct customer care links.
4. **Sunset / Inactive Segment:** Subscribers who have received 10+ messages over 90 days without clicking a single link. Drop or suppress these profiles to protect deliverability and avoid wasted spend.

---

## SMS Copywriting & Technical Best Practices

### Message Formatting & Character Encodings

```
┌──────────────────────────────────────────────────────────┐
│                   CHARACTER LIMIT MATRIX                 │
├──────────────────────────┬───────────────────────────────┤
│ ENCODING STANDARD        │ MAX CHARACTERS PER SEGMENT    │
├──────────────────────────┼───────────────────────────────┤
│ GSM-7 (Standard Latin)   │ • Single segment: 160 chars   │
│                          │ • Concatenated: 153 chars/seg │
├──────────────────────────┼───────────────────────────────┤
│ UCS-2 (Unicode / Emojis) │ • Single segment: 70 chars    │
│                          │ • Concatenated: 67 chars/seg  │
└──────────────────────────┴───────────────────────────────┘
```

> [!WARNING]
> A single non-GSM character (such as curly quotes `“ ”`, accents, or emojis `🔥`) automatically switches your entire text to **UCS-2 encoding**. A 165-character message with one emoji is billed as **3 separate message segments** per recipient.

### Copywriting Rules of Thumb

1. **State Your Brand Name First:** Begin every message with your company name or acronym (e.g., `[Acme Co]:`). Subscribers should recognize the sender before reading the offer.
2. **One Clear Call-to-Action:** Never provide multiple links or competing actions. Use one branded, shortened URL.
3. **Include Legally Mandated Opt-Out Language:** Conclude promotional texts with standard opt-out text (`Reply STOP to opt out`).
4. **Use Punctuation Wisely:** Ensure links have spaces around them so mobile operating systems render URLs as clickable links.

---

## Legal Compliance & Carrier Regulations

Failure to adhere to SMS regulations can lead to substantial carrier fines, account suspension, or private class-action lawsuits.

---

### TCPA, Quiet Hours & State Mini-TCPAs

The **Telephone Consumer Protection Act (TCPA)** governs commercial telemarketing in the United States.

- **Statutory Penalties:** Statutory damages range from **$500 to $1,500 per unauthorized text message**.
- **Prior Express Written Consent:** Merchants must secure explicit, documented agreement before sending marketing messages. Purchased or rented phone lists are illegal.
- **Federal Quiet Hours:** Federal law restricts commercial marketing communications to **8:00 AM to 9:00 PM** recipient local time.
- **State "Mini-TCPA" Laws (Stricter Windows):**
  - **Florida (§ 501.059), Oklahoma, and Maryland:** Restrict sending hours to **8:00 AM to 8:00 PM** local time.
  - Furthermore, these states cap marketing texts to a maximum of **3 messages in a 24-hour period** regarding the same subject matter.
  - **Recommended Practice:** Configure platform sending schedules strictly between **9:00 AM and 8:00 PM** recipient local time.

---

### CTIA Guidelines & Prohibited SHAFT Content

The Cellular Telecommunications and Internet Association (CTIA) establishes carrier best practices.

- **Mandatory System Keywords:** Your messaging software must automatically intercept and process:
  - Opt-out commands: `STOP`, `END`, `CANCEL`, `UNSUBSCRIBE`, `QUIT`.
  - Information commands: `HELP`, `INFO`.
- **Prohibited SHAFT Categories:** Major mobile networks strictly ban messages promoting:
  - **S**ex (adult content, explicit services)
  - **H**ate speech (harassment, discrimination)
  - **A**lcohol (heavily restricted; requires strict carrier age-gating)
  - **F**irearms & weapons
  - **T**obacco, vape, cannabis, and CBD products
- Carrier audits of SHAFT violations can incur penalties up to **$10,000 per violation** and immediate number deactivation.

---

### FCC Opt-Out & Revocation Mandates

- **Revocation by Any Reasonable Means:** In effect since **April 11, 2025**, consumers may revoke consent through any reasonable verbal or written method (e.g., typing *"stop sending texts"* or *"leave me alone"*), not just exact keyword matches. Modern SMS apps deploy AI processing to recognize informal opt-out language.
- **10-Day Processing Window:** Opt-out requests must be honored without delay and no later than **10 business days**.
- **One-Time Confirmation Rule:** Senders are permitted to transmit exactly **one final text** confirming that the subscriber has been removed from the list.

---

## Measuring Performance & ROI

### Industry Benchmark Matrix

| Performance Metric | Broadcast Campaign Benchmark | Automated Flow Benchmark | Top 10% Best-in-Class |
|---|---|---|---|
| **Delivery Rate** | 97.0% – 99.0% | 98.5% – 99.8% | >99.5% |
| **Click-Through Rate (CTR)** | 2.5% – 8.0% | 15.0% – 25.0% | >35.0% |
| **Conversion Rate (per send)** | 0.10% – 0.25% | 0.70% – 1.20% | >2.50% |
| **Click-to-Conversion Rate** | 0.80% – 1.50% | 3.50% – 5.50% | >8.00% |
| **Revenue Per Message** | $0.10 – $0.25 | $0.70 – $1.20 | >$2.50 |
| **Unsubscribe Rate per Send** | 0.50% – 1.20% | 0.20% – 0.50% | <0.20% |

### True SMS ROI Calculation

To calculate true channel profitability, account for all operating costs:

$$\text{Net SMS ROI} = \frac{\text{Attributed Revenue} - (\text{Message Costs} + \text{Carrier Fees} + \text{Platform Subscriptions} + \text{Discounts Redeemed})}{\text{Message Costs} + \text{Carrier Fees} + \text{Platform Subscriptions}} \times 100$$

---

## Advanced Strategies

### 1. Unified Email + SMS Omnichannel Workflows

Prevent customer fatigue by orchestrating your channels together:
- **Condition-Based Routing:** For abandoned carts, send an email first at 15 minutes. If unopened after 45 minutes, send an SMS ping. If the email is clicked, cancel the SMS.
- **Cost Savings:** Avoid sending costly SMS segments to subscribers who engage actively with free or low-cost email.

### 2. Conversational Two-Way Concierge & AI Agents

Rather than one-way broadcasts, utilize AI agents (such as TxtCart AI or Postscript AI):
- Answer product sizing, material, and shipping inquiries directly inside the text thread.
- Automatically apply custom checkout discount links when users respond with objections.

### 3. Hyper-Targeted Location & Weather Triggers

Using Shopify Flow alongside SMS webhooks:
- Trigger localized flash promotions based on local weather conditions (e.g., promoting outerwear during sudden cold snaps).
- Deliver invitations to regional pop-ups or retail events based on recipient area codes.

---

## References & Sources

### Official Shopify Resources
1. **Shopify Messaging App Listing & Overview**  
   https://apps.shopify.com/shopify-email
2. **Shopify Help Center — SMS Marketing & Settings**  
   https://help.shopify.com/en/manual/promoting-marketing/create-marketing/shopify-messaging
3. **Shopify Help Center — Collecting Customer SMS Consent**  
   https://help.shopify.com/en/manual/customers/customer-consent

### Telecom Infrastructure & Regulatory Standards
4. **Twilio US SMS & Carrier Pass-Through Pricing Matrix (October 2026 Live Data)**  
   https://www.twilio.com/en-us/sms/pricing/us
5. **Twilio A2P 10DLC Fees & Registry Overview**  
   https://www.twilio.com/en-us/phone-numbers/a2p-10dlc
6. **Twilio Toll-Free Onboarding & Regulatory Verification Guide**  
   https://www.twilio.com/docs/messaging/compliance/toll-free/console-onboarding
7. **CTIA Messaging Principles and Best Practices**  
   https://www.ctia.org/the-wireless-industry/industry-commitments/messaging-interoperability-sms-mms

### Shopify App Platforms (Verified Pricing & Store Listings)
8. **Postscript: Official Pricing & Plans**  
   https://postscript.io/pricing  
   *(Shopify App Store: https://apps.shopify.com/postscript-sms-marketing)*
9. **Klaviyo: Official Plans & Mobile Messaging Pricing**  
   https://www.klaviyo.com/pricing  
   *(Shopify App Store: https://apps.shopify.com/klaviyo-email-marketing)*
10. **Omnisend: Pricing & Global SMS Tier Plans**  
    https://www.omnisend.com/pricing/
11. **TxtCart AI: Conversational SMS Marketing App Listing**  
    https://apps.shopify.com/txtcart-plus
12. **Attentive: Enterprise SMS & Email Listing**  
    https://apps.shopify.com/attentive
13. **Recart: Managed SMS Marketing & Plans**  
    https://www.recart.com/pricing

### Industry Data Reports & Creator References
14. **Omnisend 2026 SMS Marketing Statistics & Performance Benchmarks**  
    https://www.omnisend.com/blog/sms-marketing-statistics/
15. **"How To Set Up SMS Marketing On Shopify (2026) | SMS Settings" — ECOM KNTRL**  
    https://www.youtube.com/watch?v=GlNZFovgUl4
16. **"The Ultimate Guide to SMS Marketing for Shopify (Increase Sales in 2026)" — SlickText**  
    https://www.youtube.com/watch?v=GDVap6uWEr8
17. **"SMS Marketing Strategy For $10M Shopify Brands (Postscript/Klaviyo/Attentive)" — Max Sturtevant (Wellcopy)**  
    https://www.youtube.com/watch?v=5avcX6rqjD8
18. **"The Only Shopify SMS Marketing Tutorial You Will Ever Need!" — Antonio Williams**  
    https://www.youtube.com/watch?v=c9ndYzZCVJM
19. **"How To Setup SMS Marketing For Shopify (Tutorial for Beginners)" — Alexander Shenton**  
    https://www.youtube.com/watch?v=C1wAo83EzbQ

---

## Quick Reference: Getting Started

| Store Stage | Recommended Solution | Setup Priority |
|---|---|---|
| **New store, testing SMS (<500 subscribers)** | **Shopify Messaging** | Verify Toll-Free number ($2.15/mo), enable checkout opt-in, activate abandoned checkout automation. |
| **Growing store ($10k–$50k/mo revenue)** | **Postscript** or **Omnisend** | Set up 2-step desktop/mobile popups, welcome flow, and 2-step cart recovery flow. |
| **Established store with active email program** | **Klaviyo** | Unify email and SMS profiles, configure smart cross-channel delays, build VIP segments. |
| **High cart-abandonment & consultative products** | **TxtCart AI** | Deploy conversational AI agents to answer customer objections in real time. |
| **High-volume scale ($1M+/year)** | **Attentive** or **Dedicated Short Code** | Provision high-throughput sending numbers for flash sales and holiday shopping periods. |

---

*Last updated: October 2026*
