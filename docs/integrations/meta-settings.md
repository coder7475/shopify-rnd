# Meta (Facebook & Instagram) App for Shopify: Complete Settings & Marketing Guide

A comprehensive, option-by-option reference guide to all settings, configurations, marketing tools, and ad creation capabilities available in the official **Facebook & Instagram by Meta** sales channel on Shopify.

---

## Table of Contents
1. [Overview & Channel Navigation](#1-overview--channel-navigation)
2. [Connection & Account Assets](#2-connection--account-assets)
3. [Data Sharing & Tracking Settings (Pixel & CAPI)](#3-data-sharing--tracking-settings-pixel--capi)
4. [Checkout & Selling Options (Facebook & Instagram Shop)](#4-checkout--selling-options-facebook--instagram-shop)
5. [Product Catalog & Feed Management](#5-product-catalog--feed-management)
6. [Marketing & Ad Campaign Tools Inside Shopify](#6-marketing--ad-campaign-tools-inside-shopify)
7. [Meta Business Suite & Ads Manager Advanced Controls](#7-meta-business-suite--ads-manager-advanced-controls)
8. [Troubleshooting Common Settings & Sync Issues](#8-troubleshooting-common-settings--sync-issues)

---

## 1. Overview & Channel Navigation

The **Facebook & Instagram by Meta** application is installed as a **Sales Channel** (located under `Shopify Admin > Sales channels > Facebook & Instagram`).

Unlike standard Shopify apps that only run within their own window, this integration acts as a system bridge connecting three environments:
1. **Your Shopify Store Admin:** Controls which products are published, data sharing levels, and simplified marketing campaigns.
2. **Meta Commerce Manager:** Manages social storefront layouts, product collections, and checkout settings.
3. **Meta Ads Manager & Events Manager:** Receives server/browser tracking events, manages custom audiences, and runs automated ad campaigns.

---

## 2. Connection & Account Assets

When opening the channel settings (`Sales channels > Facebook & Instagram > Settings`), the following account assets must be connected:

### 2.1 Meta Account (Personal Profile)
* **What it is:** The personal Facebook account used for login verification.
* **Requirements:** This account must hold **Full Control (Admin)** permissions in your Meta Business Portfolio (Business Manager).

### 2.2 Meta Business Portfolio (Business Manager)
* **What it is:** The central organizational hub that owns all your brand's digital assets.
* **Setting Action:** Select your active Business Portfolio from the dropdown list.
* **Important:** If your Business Portfolio is unverified, Meta may restrict catalog publishing or ad spending limits until you complete business verification.

### 2.3 Facebook Business Page
* **What it is:** The public Facebook page representing your store.
* **Setting Action:** Connect your verified brand page.
* **Result:** Enables the "View Shop" button on your Facebook page and allows Facebook dynamic ads to run under your brand identity.

### 2.4 Instagram Professional Account
* **What it is:** Your brand's Instagram Business or Creator account.
* **Requirements:**
  * Must be connected to your Facebook Page in Instagram account settings (`Settings > Account > Linked Accounts`).
  * Personal Instagram profiles are not supported; you must convert to a Professional account.
* **Result:** Unlocks product tagging in Instagram Feed posts, Stories, and Reels, as well as an Instagram Shop tab on your profile.

---

## 3. Data Sharing & Tracking Settings (Pixel & CAPI)

Found under: `Settings > Data Sharing`

This is the most critical technical setting in the entire app. It controls how visitor tracking data is transmitted to Meta's machine learning engine.

### 3.1 Data Sharing Tiers

Meta provides three levels of customer data tracking:

| Data Sharing Level | Technology Used | How It Operates | Recommended For |
| :--- | :--- | :--- | :--- |
| **Standard** | Browser-Only Meta Pixel | Uses third-party browser cookies only. Frequently blocked by AdBlockers, Safari ITP, and iOS 14.5+ privacy protections. | Not recommended (misses 30%+ of conversions). |
| **Enhanced** | Browser Pixel + Advanced Matching | Uses the browser pixel plus basic hashed personal data (name, email) sent from browser forms. | Basic stores without technical requirements. |
| **Maximum (Recommended)** | Conversions API (CAPI) + Browser Pixel | Sends encrypted server-to-server events directly from Shopify's cloud edge in parallel with the browser pixel. | **All stores.** Essential for maximizing ad return on spend and tracking accuracy. |

### 3.2 Key Features Active Under "Maximum":
* **Conversions API (CAPI):** Server-side event transmission that cannot be blocked by browser extensions or browser-level cookie restrictions.
* **Automated Event Deduplication:** Both server and browser send matching `event_id` tokens so Meta never counts duplicate orders.
* **Advanced Customer Matching:** Shopify automatically hashes and sends customer parameters (`em` for email, `ph` for phone, `fn`/`ln` for first/last name, city, and zip code) to match purchases with Meta profiles.
* **Target Metric:** Aim for an **Event Match Quality (EMQ)** score of **8.0 or higher out of 10** in Meta Events Manager.

---

## 4. Where is the "Checkout & Selling Option"? (Why You Can't Find It in Shopify)

If you are looking inside your **Shopify Admin** under `Sales channels > Facebook & Instagram > Settings` and **cannot find a "Checkout Method" setting**, here is exactly why:

### 4.1 The Setting Lives in Meta Commerce Manager (Not Inside Shopify)
* Inside the Shopify channel settings, you will only see:
  * **Account connection** (Meta account, Business Portfolio, Page, Instagram).
  * **Data sharing** (Standard, Enhanced, Maximum).
  * **Terms and Conditions**.
* **Checkout destination is managed on Meta's end**, not on Shopify. You can find and view it in **[Meta Commerce Manager](https://commerce.facebook.com)**:
  1. Log into [Meta Commerce Manager](https://commerce.facebook.com).
  2. Select your Commerce Account.
  3. Click **Settings** (the gear icon at the bottom of the left sidebar).
  4. Click **Checkout Method**.
  5. It will show: **"Checkout on another website"** (pointing to your Shopify domain).

### 4.2 Why There is No Option to Switch Anymore
* Previously, US merchants could choose between "Checkout on Facebook/Instagram" (Meta Pay) and "Checkout on Website".
* Meta has phased out in-app checkout and transitioned shops back to **Website Checkout**.
* **How it works now:** When a customer taps your product tag on Instagram or Facebook, they tap **"View on website"** and are automatically sent to your Shopify store to finish the order.

### 4.3 Where You Actually Customize Your Checkout Experience
Because every shopper from Facebook and Instagram completes their order on your Shopify store, all your actual checkout options are controlled inside Shopify:
* **Shopify Admin > Settings (bottom left) > Checkout:** Manage email vs. phone signups, shipping address requirements, tipping, and discount boxes.
* **Shopify Admin > Settings (bottom left) > Payments:** Manage 1-click **Shop Pay**, credit cards, and PayPal.

---

## 5. Product Catalog & Feed Management

Found under: `Sales channels > Facebook & Instagram > Catalog` (and `Shopify Admin > Products`)

The app automatically syncs a single master catalog from Shopify to Meta Commerce Manager.

### 5.1 Publishing Products to Meta
* **Individual Product Control:** Open any item in `Shopify Admin > Products`. On the right sidebar under **Publishing / Sales Channels**, check or uncheck **Facebook & Instagram**.
* **Bulk Publishing:** In the product list, select multiple items, click **Include in sales channels**, and choose **Facebook & Instagram**.

### 5.2 Product Statuses in the Catalog
* **Approved / Published:** Ready to be tagged in posts and used in dynamic ad campaigns.
* **In Review:** Meta's automated moderation is scanning the product against Meta Commerce Policies (typically 24–48 hours).
* **Not Approved / Rejected:** Item violates Meta policy or lacks critical metadata. Common reasons:
  * Missing Google Product Category (GPC).
  * Missing image or image resolution under 500x500px.
  * Prohibited terms (health claims, adult items, weapons, tobacco, trademarks).

### 5.3 Google Product Category (GPC) Field
Meta requires every physical product to map to a standardized taxonomy:
* Open `Products > Bulk Editor`.
* Ensure each product has a valid category assigned (e.g., `Apparel & Accessories > Clothing > Dresses`).

---

## 6. Marketing & Ad Campaign Tools Inside Shopify

Shopify allows you to create and monitor Facebook & Instagram advertising campaigns directly within the Shopify Admin (`Shopify Admin > Marketing > Campaigns`).

### 6.1 Campaign Types Available in Shopify

#### A. Facebook Dynamic Retargeting Ads
* **What it does:** Automatically shows personalized ads to people who visited your online store, viewed specific items, or added products to their cart without purchasing.
* **How it works:** Uses the synced product catalog. If a customer looked at a green jacket, Meta automatically serves them an ad featuring that exact green jacket.
* **Setup Fields:**
  * **Campaign Name:** Name of your marketing activity.
  * **Budget:** Daily budget (e.g., $10/day to $50/day).
  * **Target Audience:** Automatically targets visitors from the last 14–30 days.
  * **Ad Text / Primary Copy:** The text displayed above the ad (e.g., *"Still thinking about it? Take 10% off your order today with code WELCOME10."*).

#### B. Facebook Carousel / Product Feature Ads
* **What it does:** Creates a scrollable card carousel showcasing 3 to 5 featured products or collections to prospective shoppers.
* **Audience Targeting Options Inside Shopify:**
  * **Location:** Countries or regions where you ship.
  * **Interests:** Select broad interest categories relevant to your brand (e.g., fashion, home decor, fitness).
  * **Age & Gender:** Define your target demographic range.

### 6.2 Marketing Analytics in Shopify
When campaigns are launched, performance metrics appear under `Marketing > Performance`:
* **Impressions:** How many times the ad appeared in feeds/stories.
* **Clicks:** Total link clicks to your online store.
* **Conversions & Orders:** Number of completed purchases directly attributed to the ad.
* **Sales & Return on Ad Spend (ROAS):** Total revenue generated divided by ad spend.

---

## 7. Meta Business Suite & Ads Manager Advanced Controls

While simple campaigns can be created inside Shopify, advanced scaling is done inside **Meta Ads Manager** (`adsmanager.facebook.com`) using the assets connected via Shopify.

### 7.1 Advantage+ Shopping Campaigns (ASC)
* **What it is:** Meta's premier artificial intelligence ad format for e-commerce.
* **How to use with Shopify:**
  1. Open Meta Ads Manager and click **Create Campaign**.
  2. Select **Sales** as the objective.
  3. Choose **Advantage+ Shopping Campaign**.
  4. Select your Shopify-synced Meta Catalog.
  5. Set an **Existing Customer Budget Cap** (recommended: 5%–10%) to ensure Meta spends 90%+ of your budget acquiring brand-new customers.
  6. Upload a creative mix of video Reels, customer unboxing, and static lifestyle images.

### 7.2 Custom & Lookalike Audiences
Because your Conversions API is active with Maximum data sharing, Meta automatically builds high-value custom audiences:
* **Website Custom Audience (WCA):** All visitors in the last 30, 60, or 180 days.
* **Purchaser List:** Past buyers automatically synced from Shopify orders.
* **Lookalike Audiences (LAL):** Meta identifies top 1% of users who share demographic and behavioral patterns with your highest-spending Shopify customers.

### 7.3 Organic Product Tagging (Instagram & Facebook)
Once the catalog is connected, tagging is performed directly inside the Instagram mobile app:
1. Create a new **Post, Story, or Reel**.
2. Tap **Tag Products**.
3. Search for the product title or SKU from your Shopify store.
4. Place the tag over the item and publish.

---

## 8. Troubleshooting Common Settings & Sync Issues

| Problem | Where to Check | Solution |
| :--- | :--- | :--- |
| **Catalog Not Syncing to Meta** | `Sales channels > Facebook & Instagram > Settings > Product Status` | Ensure products are set to **Active** status and the **Facebook & Instagram** checkbox is checked under Publishing in Shopify. |
| **"Account Restricted" or "Commerce Account Inactive"** | Meta Business Suite (`business.facebook.com`) | Complete **Business Verification** under `Business Settings > Security Center`. Verify your custom store domain via DNS TXT record. |
| **Low Event Match Quality (< 6.0)** | Meta Events Manager (`eventsmanager.facebook.com`) | Verify Data Sharing in Shopify is set to **Maximum**. Ensure customer telephone numbers and postal codes are collected during checkout. |
| **Products Rejected for Missing Price or Currency** | `Shopify Admin > Settings > Markets` | Confirm product pricing is assigned in your primary currency and items are available in the target market. |
| **Instagram Product Tagging Unavailable** | Instagram App (`Settings > Business > Shopping`) | Ensure your Instagram account is approved for shopping and connected to the exact Meta Catalog created by Shopify. |

---

## Summary of Best Practices for Beginners
1. **Always choose "Maximum" Data Sharing** to ensure server-side tracking works reliably on mobile devices.
2. **Assign Google Product Categories** to all products using Shopify's bulk editor to avoid catalog rejections.
3. **Keep product titles and descriptions clean** and free from prohibited claims.
4. **Use Shopify Marketing for quick retargeting**, and use **Meta Ads Manager** when you are ready to scale with Advantage+ Shopping Campaigns.
