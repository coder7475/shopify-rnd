# 🏬 Shopify POS (Point of Sale): Complete In-Person Selling & Pricing Guide

> **Document Type:** Technical, Operational & Pricing Reference  
> **Target Audience:** Shopify Merchants, Boutique Owners, Pop-Up Vendors (e.g., Naza Noor Events)  
> **Supported Plans:** Starter, **Basic ($39/mo)**, Shopify ($105/mo), Advanced ($399/mo), Plus  
> **Verification Status:** Verified via official Shopify Retail & POS Documentation (2026)

---

## 📑 Table of Contents
1. [Executive Summary & What is Shopify POS?](#1-executive-summary--what-is-shopify-pos)
2. [Core Architecture: Unified Omnichannel Sync](#2-core-architecture-unified-omnichannel-sync)
3. [Shopify POS Lite vs. POS Pro (Feature Breakdown)](#3-shopify-pos-lite-vs-pos-pro-feature-breakdown)
4. [2026 Pricing, Subscription & Transaction Rates](#4-2026-pricing-subscription--transaction-rates)
5. [Hardware Ecosystem: From Zero-Cost to Full Countertop](#5-hardware-ecosystem-from-zero-cost-to-full-countertop)
6. [Primary Use Cases & Real-World Scenarios](#6-primary-use-cases--real-world-scenarios)
7. [Offline Selling Mode: Capabilities & Limitations](#7-offline-selling-mode-capabilities--limitations)
8. [Tactical Playbook for Pop-Up Shops (Naza Noor Context)](#8-tactical-playbook-for-pop-up-shops-naza-noor-context)
9. [Step-by-Step Setup Checklist for Basic Plan Merchants](#9-step-by-step-setup-checklist-for-basic-plan-merchants)

---

## 1. Executive Summary & What is Shopify POS?

**Shopify POS (Point of Sale)** is an iOS and Android mobile application that enables businesses to sell products physically in person—at retail stores, pop-up events, weekend markets, trunk shows, craft fairs, and exhibitions—while staying **100% unified with their online Shopify store**.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       SHOPIFY UNIFIED COMMERCE ENGINE                       │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │
            ┌──────────────────────────┴──────────────────────────┐
            ▼                                                     ▼
┌───────────────────────────────┐             ┌───────────────────────────────┐
│     Online Channels           │             │     Physical Channels (POS)   │
├───────────────────────────────┤             ├───────────────────────────────┤
│ • Online Web Store (Themes)   │             │ • Pop-Up Booths & Fairs       │
│ • Shop App Mobile Marketplace │◄───────────►│ • Retail Boutiques & Stores   │
│ • Meta (Instagram / Facebook) │  REAL-TIME  │ • Trunk Shows & Exhibitions   │
│ • Google / TikTok / Pinterest │  INVENTORY  │ • Wholesale / Studio Pop-ups  │
└───────────────────────────────┘             └───────────────────────────────┘
```

### Why Unified Commerce Matters
Traditional retail required separate systems: one software for physical cash registers and another for online e-commerce, leading to painful manual inventory reconciliation, overselling, and fragmented customer data. 

With Shopify POS:
* When an item is sold at a physical pop-up booth, online inventory decrements **instantaneously**.
* Customers created at a pop-up booth immediately join your central customer CRM for email/SMS marketing.
* Gift cards, store credits, and promo discount codes work interchangeably online and in person.

---

## 2. Core Architecture: Unified Omnichannel Sync

When you activate the Point of Sale channel in your Shopify admin, the POS app communicates directly with your core Shopify backend:

1. **Inventory Pooling:** Stock can be assigned to specific physical "Locations" (e.g., *Main Warehouse*, *Downtown Pop-Up Booth*, *Retail Store*), or deducted from a unified pool.
2. **Centralized Customer Database:** Cashiers can search existing customers by name, phone, or email to attach past order history or create new customer profiles on the spot.
3. **Unified Checkout Engine:** The POS app processes payments, applies promotional discount codes, calculates localized sales tax automatically, and generates electronic (SMS/Email) or paper receipts.
4. **Order Reporting:** In-person orders appear immediately inside your standard `Shopify Admin > Orders` list alongside website orders, tagged with the channel `Point of Sale`.

---

## 3. Shopify POS Lite vs. POS Pro (Feature Breakdown)

Shopify structures its retail software into two tiers: **POS Lite** (included free on all plans) and **POS Pro** (paid add-on per physical location).

| Feature / Capability | POS Lite (Included on Basic) | POS Pro ($89/mo per location) |
| :--- | :--- | :--- |
| **Monthly Cost** | **$0 / month (Free)** | **$89 / month per location** |
| **Ideal For** | Pop-ups, markets, temporary booths, small shops | Permanent retail stores, multi-staff boutiques |
| **Cart & Payment Processing** | Yes (Cards, Cash, Gift Cards, Split tenders) | Yes (All payment methods + Custom tenders) |
| **Real-Time Inventory Sync** | Yes (Across all assigned locations) | Yes (Plus stock transfers & purchase orders) |
| **Customer Profiles & History** | Yes (Create, lookup, attach to orders) | Yes (Lifetime spend, loyalty integrations) |
| **Staff Logins & PINs** | Basic (Shared login with unlimited PINs) | Advanced custom staff roles & granular permissions |
| **Discounts & Price Overrides** | Manual discount codes & percentage overrides | Automatic in-store promotional discount tiers |
| **Receipts** | Email, SMS, or Printed (via AirPrint/BT) | Fully customizable printed receipt templates |
| **Omnichannel Fulfillment** | Standard order fulfillment | **BOPIS** (Buy Online, Pick Up In Store), Ship from store |
| **Exchanges & Returns** | Return online items in-store (standard refund) | Full exchanges (swap sizes without separate transactions)|
| **Inventory Counting** | Manual via Admin | In-app barcode inventory cycle counts |
| **Daily Register Closing** | Basic register shift summary | Daily register balance shift audits & cash tracking |

> [!TIP]
> **Basic Plan Verdict:** If you are running pop-up shops, weekend markets, or seasonal retail events (such as **Naza Noor** pop-ups), **POS Lite is 100% sufficient**. You do **not** need POS Pro until you open a permanent physical storefront with multiple hourly shift employees.

---

## 4. 2026 Pricing, Subscription & Transaction Rates

### A. Software Subscription Pricing
* **POS Lite:** **$0.00 / month**. Included automatically on Shopify Starter, **Basic ($39/mo)**, Shopify ($105/mo), Advanced ($399/mo), and Plus.
* **POS Pro:** **$89.00 USD / month per location** (billed annually or monthly). *Note: Shopify Plus includes POS Pro for up to 20 locations at no extra charge.*

---

### B. In-Person Card Processing Rates (Shopify Payments)
In-person credit card transactions are physically swiped, dipped (chip), or tapped (contactless). Because physical card presence has a lower fraud risk than online transactions, **Shopify’s in-person transaction rates are significantly lower than online rates**:

| Shopify Plan | In-Person Card Rate (Shopify Payments) | Online Card Rate (For Comparison) |
| :--- | :--- | :--- |
| **Shopify Basic ($39/mo)** | **2.6% + 10¢ USD** | 2.9% + 30¢ USD |
| **Shopify Plan ($105/mo)** | **2.5% + 10¢ USD** | 2.7% + 30¢ USD |
| **Shopify Advanced ($399/mo)** | **2.4% + 10¢ USD** | 2.5% + 30¢ USD |
| **Shopify Plus** | **~2.15% + 10¢ USD** (custom) | ~2.15% + 30¢ USD |

*Note: If you choose to use an external merchant card terminal (third-party payment gateway) rather than Shopify Payments, Shopify charges an additional platform fee (2.0% on Basic, 1.0% on Shopify, 0.5% on Advanced).*

---

## 5. Hardware Ecosystem: From Zero-Cost to Full Countertop

Shopify POS supports a spectrum of hardware depending on your mobility and budget:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          SHOPIFY POS HARDWARE TIERS                         │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │
     ┌─────────────────────────────────┼─────────────────────────────────┐
     ▼                                 ▼                                 ▼
┌─────────────────────────┐ ┌─────────────────────────┐ ┌─────────────────────────┐
│     TIER 1: ZERO-COST   │ │   TIER 2: MOBILE PRO    │ │  TIER 3: FULL RETAIL    │
│   (Smartphone Only)     │ │  (Phone/Tablet + Reader)│ │ (iPad Countertop Setup) │
├─────────────────────────┤ ├─────────────────────────┤ ├─────────────────────────┤
│ • iPhone or Android     │ │ • iPad or Tablet        │ │ • iPad + Retail Stand   │
│ • Tap to Pay on Phone   │ │ • WisePad 3 / Chipper   │ │ • Bluetooth Card Reader │
│ • Digital SMS Receipts  │ │ • Mobile Barcode Scanner│ │ • Star Micronics Printer│
│ • Total Hardware: $0    │ │ • Total Hardware: ~$49  │ │ • Cash Drawer ($300-$700)│
└─────────────────────────┘ └─────────────────────────┘ └─────────────────────────┘
```

### 1. Tier 1: Zero-Hardware Setup ("Tap to Pay")
* **How it Works:** Use your existing smartphone running the free Shopify POS app.
* **Tap to Pay on iPhone & Tap to Pay on Android:** Turns your smartphone directly into a secure contactless payment terminal using its internal NFC chip.
* **Customer Payment Experience:** Customers tap their contactless credit card, Apple Pay, Google Pay, or smart watch directly against the back of your phone.
* **Supported Regions:** US, UK, Canada, Australia, Netherlands, Germany, and select European/APAC markets.
* **Cost:** **$0.00 in hardware purchases**.

### 2. Tier 2: Mobile Bluetooth Card Readers
* **WisePad 3 / Shopify Tap & Chip Reader (~$49 USD):** Pocket-sized card reader that connects to your iPad or smartphone via Bluetooth. Accepts EMV chip insertion and contactless taps. Ideal for pop-up booths where customers prefer physical chip insertion.

### 3. Tier 3: Complete Countertop Retail Setup
* **Tablet Enclosure:** Shopify Retail Stand for iPad (swivels for customer tipping & signature).
* **Thermal Receipt Printer:** Star Micronics TSP143III (Bluetooth, LAN, or USB).
* **Barcode Scanner:** Socket Mobile S700 / Zebra 1D/2D Bluetooth barcode reader.
* **Cash Drawer:** APG or Star Micronics heavy-duty 13" or 16" cash drawer (plugs directly into the receipt printer RJ12 port to trigger automatic opening on cash sales).

---

## 6. Primary Use Cases & Real-World Scenarios

### Use Case A: Pop-Up Shops & Weekend Markets (Boutique Fashion / Naza Noor)
* **The Scenario:** Setting up a temporary booth at an apparel expo, designer market, or community festival.
* **The Advantage:** Zero heavy equipment. Use an iPad or iPhone with Tap to Pay. Every dress, scarf, or accessory sold instantly decrements your website inventory, preventing accidental online overselling while you are at the booth.

### Use Case B: Permanent Brick-and-Mortar Boutique
* **The Scenario:** Operating a storefront open 6 days a week with multiple staff members.
* **The Advantage:** Fast barcode scanning at checkout, automatic receipt printing, integrated cash management, and seamless processing of online store gift cards.

### Use Case C: In-Person Warehouse & Studio Sales
* **The Scenario:** Hosting an exclusive VIP sample sale or studio clearance event.
* **The Advantage:** Cashiers can scan tags using the phone camera as a built-in barcode scanner and apply quick 20% or 40% cart discounts without changing online prices.

---

## 7. Offline Selling Mode: Capabilities & Limitations

Outdoor markets and convention halls often have spotty cellular service or unreliable Wi-Fi. Shopify POS includes built-in offline safeguards:

### What Works While Offline:
* ✅ Browsing your synchronized product catalog.
* ✅ Adding products to the cart.
* ✅ Applying manual percentage or flat dollar discounts.
* ✅ **Accepting Cash Payments** (recorded locally on the device).
* ✅ Issuing pending email receipts (queued to send once reconnected).

### What Requires an Active Internet Connection:
* ⚠️ **Live Credit Card Processing:** Contactless and chip card readers require internet access to communicate with payment networks. (Tip: Use your smartphone’s personal cellular hotspot if venue Wi-Fi drops).
* ⚠️ **Real-Time Cross-Channel Stock Sync:** Inventory sold offline will queue locally and sync to the cloud once connectivity is restored.
* ⚠️ **Gift Card Balance Lookups:** Cannot verify live balances of pre-loaded digital gift cards without an internet connection.

---

## 8. Tactical Playbook for Pop-Up Shops (Naza Noor Context)

For a growing fashion, modest wear, or lifestyle brand like **Naza Noor**, pop-up events are high-leverage marketing drivers. Follow these practical operational tactics:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        POP-UP HIGH-CONVERSION TACTICS                       │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │
     ┌─────────────────────────────────┼─────────────────────────────────┐
     ▼                                 ▼                                 ▼
┌─────────────────────────┐ ┌─────────────────────────┐ ┌─────────────────────────┐
│ 1. LEAD CAPTURE         │ │ 2. INVENTORY SEPARATION │ │ 3. "SHIP TO ME" FALLBACK│
├─────────────────────────┤ ├─────────────────────────┤ ├─────────────────────────┤
│ Ask every customer:     │ │ Create a distinct       │ │ If a popular size sells │
│ "Can I email or text    │ │ "Pop-up Location" in    │ │ out at the booth, take  │
│ you your receipt?"      │ │ Admin to allocate only  │ │ payment on POS and      │
│ Builds your newsletter  │ │ booth stock without     │ │ fulfill from main       │
│ list on autopilot.      │ │ depleting web reserves. │ │ warehouse to their home.│
└─────────────────────────┘ └─────────────────────────┘ └─────────────────────────┘
```

1. **Turn Every In-Person Buyer into an Online Repeat Customer:**
   * Always ask for their phone number or email to send an SMS/Email receipt.
   * This links their physical purchase to their customer profile. After the event, you can send automated post-purchase welcome flows via Shopify Inbox or Klaviyo.

2. **Use Camera Barcode Scanning:**
   * You don't need a $250 laser scanner. In the Shopify POS app, tap the barcode icon to turn your iPhone or iPad camera into an instant scanner for product hangtags.

3. **Save Carts for Hesitant Shoppers:**
   * If a customer is trying on an outfit but wants to explore the rest of the market first, use the **"Email Cart"** feature in Shopify POS. This sends them an interactive link containing their exact cart items with Shop Pay checkout ready.

---

## 9. Step-by-Step Setup Checklist for Basic Plan Merchants

Follow this 15-minute setup checklist to activate Shopify POS for your store:

- [ ] **Step 1: Add POS Sales Channel**
  - Go to `Shopify Admin > Sales channels > Add channels > Point of Sale`.
- [ ] **Step 2: Define Your Physical Location**
  - Navigate to `Settings > Locations`.
  - Ensure your pop-up booth or showroom is listed (e.g., "Main Boutique" or "Weekend Market").
- [ ] **Step 3: Download the App**
  - Install the **Shopify POS** app from the [Apple App Store](https://apps.apple.com) or [Google Play Store](https://play.google.com) on your smartphone or iPad.
- [ ] **Step 4: Create Staff PINs**
  - In Shopify Admin, navigate to `Point of Sale > Staff`.
  - Assign a 4-digit PIN for yourself and any team members helping at the booth.
- [ ] **Step 5: Enable Tap to Pay or Pair Card Reader**
  - Open the POS app on your phone, log in, go to `Settings > Hardware > Set up hardware`.
  - Toggle on **Tap to Pay on iPhone / Android**, or pair your Bluetooth card reader (WisePad 3).
- [ ] **Step 6: Run a $1.00 Test Transaction**
  - Add any test product to the cart, select card payment, complete the tap transaction, and email yourself the receipt.
  - Immediately refund the order in `Orders` to verify full two-way payment sync.

---

## 10. Summary & Strategic Recommendation

* **Zero Financial Barrier:** On the **Basic Plan ($39/mo)**, Shopify POS Lite costs **$0 extra per month**.
* **Lower Transaction Fees:** Physical in-person rates (**2.6% + 10¢**) are cheaper than online rates (**2.9% + 30¢**).
* **Zero Hardware Cost to Start:** Using **Tap to Pay on iPhone or Android**, you can take contactless payments anywhere without buying a physical card reader.
* **Unified Intelligence:** Inventory, customer emails, gift cards, and sales data stay synchronized with your online store without spreadsheet reconciliations.
