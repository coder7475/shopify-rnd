# 🛍️ Connecting Shopify to Meta (Facebook & Instagram Shop)

> **Brand Context:** Naza Noor / Shopify E-Commerce Store  
> **Channel:** Meta (Facebook & Instagram Shopping)  
> **Official Integration:** **Shopify Facebook & Instagram Sales Channel (Meta app)**

---

## 📌 1. WHAT is the Meta (Facebook & Instagram) Shopify Connection?

The **Shopify Facebook & Instagram integration** is Shopify's official sales channel application built in direct partnership with Meta. 

It creates a synchronized, bidirectional bridge connecting:
* **Your Shopify Store:** Products, variants, inventory, pricing, collections, and orders.
* **Meta Business Suite:** Meta Commerce Manager, Facebook Page, Instagram Professional/Business Account, Meta Pixel, and Conversions API (CAPI).

### Core Components Activated:
1. **Instagram Shop & Facebook Shop (Storefronts):** An in-app shopping experience on Instagram and Facebook displaying your Shopify product catalog natively with links/checkouts.
2. **Product Tagging (Shoppable Posts & Reels):** The ability to tag products directly in Instagram posts, stories, reels, live streams, and ads. Tapping the tag reveals title, price, images, and a direct checkout link.
3. **Meta Pixel & Conversions API (CAPI):** Server-side and browser tracking that accurately measures customer journeys, events (ViewContent, AddToCart, Purchase), and powers Facebook/Instagram ad targeting (Retargeting, Lookalikes).
4. **Automated Catalog Sync:** Automatic background synchronization of inventory counts, price adjustments, and product additions/removals between Shopify and Meta.

---

## 💡 2. WHY Connect Shopify to Facebook & Instagram Shop?

Connecting your Shopify store to Meta is essential for fashion, luxury, and D2C brands:

### 1. Frictionless In-App Discovery to Purchase
* Consumers discover fashion products through Instagram Reels and Stories. With product tags, customers don't have to navigate to your bio link or search your store manually—one tap takes them directly to the product or checkout.

### 2. Higher Conversion Rates & Average Order Value (AOV)
* Eliminating drop-off steps between discovering an item on social media and landing on the checkout page significantly increases conversion rates.

### 3. Server-Side Data Accuracy (Conversions API - CAPI)
* Ever since iOS 14.5+ and privacy changes (App Tracking Transparency), traditional browser cookies miss 20%–40% of conversion data.
* Shopify’s native Meta integration delivers **Maximum Tracking (Conversions API)**, sending encrypted server-to-server events directly to Meta’s ad engine for superior ad attribution and lower Cost Per Acquisition (CPA).

### 4. Dynamic Retargeting & Lookalike Ad Campaigns
* Meta Ads can automatically showcase the exact products or collections a user browsed or added to cart on Shopify using Meta Catalog Sales campaigns (Dynamic Product Ads).

### 5. Automated Catalog & Inventory Accuracy
* Out-of-stock items automatically hide or update across Instagram and Facebook in real-time, preventing unhappy customers from attempting to purchase sold-out items.

---

## ⚙️ 3. HOW to Connect Shopify to Facebook & Instagram (Step-by-Step)

```
┌────────────────────────┐      ┌────────────────────────┐      ┌────────────────────────┐
│ 1. Prerequisites Check │ ───> │ 2. Install & Connect   │ ───> │ 3. Meta Asset Mapping  │
│ Business Accounts, BM  │      │ Meta App in Shopify    │      │ Page, IG, Pixel, CAPI  │
└────────────────────────┘      └────────────────────────┘      └────────────────────────┘
                                                                             │
┌────────────────────────┐      ┌────────────────────────┐                   │
│ 5. Tagging & Go-Live   │ <─── │ 4. Commerce Review     │ <─────────────────┘
│ Tag Reels, Posts, Ads  │      │ Meta Catalog Approval  │
└────────────────────────┘      └────────────────────────┘
```

---

### Step 1: Pre-requisites & Account Verification
Before opening Shopify, ensure your social media accounts are properly structured:

1. **Meta Business Portfolio (Business Manager):**
   * Must have an active Meta Business Manager account ([business.facebook.com](https://business.facebook.com)) with **Admin** access.
2. **Facebook Page:**
   * A Facebook Business Page representing the brand (Admin permission).
3. **Instagram Business/Creator Account:**
   * Convert your Instagram account to a **Professional (Business or Creator)** account in Instagram settings.
   * Connect your Instagram account to your Facebook Page in Instagram Settings (`Settings > Business > Connect a Facebook Page`).
4. **Commerce Eligibility:**
   * Your store must sell eligible physical goods (complies with Meta's Commerce Eligibility Requirements).
   * Your domain must be verified in Meta Business Manager (`Brand Safety and Suitability > Domains`).

---

### Step 2: Install the Facebook & Instagram App in Shopify

1. In your **Shopify Admin**, navigate to **Settings > Apps and sales channels** (or search in the top search bar).
2. Click **Shopify App Store** and search for:  
   👉 `Facebook & Instagram` (developed by Meta).
3. Click **Install**.
4. In the Shopify sidebar, you will now see **Facebook & Instagram** under **Sales Channels**.

---

### Step 3: Connect Meta Assets (Account Mapping)

1. Click **Get Started** inside the Facebook & Instagram channel in Shopify.
2. **Connect Meta Account:**
   * Log in with your personal Facebook account that holds Admin access to the brand’s Meta Business Manager.
3. **Select Your Business Portfolio (Business Manager):**
   * Select your official brand Business Portfolio.
4. **Connect Facebook Page & Instagram Profile:**
   * Choose your brand’s Facebook Page and linked Instagram Professional account.
5. **Set Data Sharing Preference (Crucial for Tracking):**
   * Choose **Maximum** data sharing level.
   * This activates **Conversions API (CAPI)** in tandem with Meta Pixel, sharing customer browser and server-side conversion data for optimal ad performance.
6. **Connect or Create a Meta Pixel:**
   * Select your existing active Pixel or click create a new one.
7. **Accept Meta Terms & Conditions:**
   * Read and agree to Meta's Seller Terms and Merchant Agreement.
8. Click **Submit for Review**.

---

### Step 4: Catalog Synchronization & Commerce Account Review

1. Once connected, Shopify automatically exports your active products into **Meta Commerce Manager**.
2. **Review Timeline:**
   * Meta typically reviews and approves the catalog and shop setup within **24 to 72 hours**.
   * You can check status directly in Shopify Admin (`Sales Channels > Facebook & Instagram`) or in [Meta Commerce Manager](https://business.facebook.com/commerce).
3. **Ensuring Fast Approval:**
   * Products must have high-resolution images, accurate descriptions, prices, shipping policies, and refund policies visible on your Shopify storefront.

---

### Step 5: Activate Instagram Shopping & Shoppable Tagging

Once Meta approves your Commerce Account:
1. Open the **Instagram App** on your mobile device.
2. Go to **Profile > Settings > Business > Set Up Instagram Shopping**.
3. Confirm the connected catalog synced from Shopify.
4. Once verified, you can begin tagging products:
   * **Feed Posts & Carousels:** Tap *Tag Products*, click on the product image, search the catalog item, and publish.
   * **Reels:** Select *Tag Products* in the pre-publish screen before posting.
   * **Stories:** Use the *Product Sticker* to tag direct links to your items.

---

## ⚠️ Common Pitfalls & Troubleshooting

| Issue | Root Cause | Solution |
| :--- | :--- | :--- |
| **"Account Ineligible for Commerce"** | Facebook Page or Instagram lacks sufficient account activity or domain verification is missing. | Verify your domain in Meta Business Manager (`Domains > DNS verification`). Ensure store has clear shipping & return policy pages on the Shopify website. |
| **Products Not Syncing to Catalog** | Missing barcode (GTIN), invalid product handle, or policy violation. | Check Shopify `Products > Sales channels` and verify "Facebook & Instagram" is checked. Check Meta Commerce Manager for specific catalog rejection flags. |
| **Instagram Not Showing "Shopping" Setting** | Personal Instagram profile or account not linked to the verified Facebook Page. | Switch Instagram to Business Account and re-link Facebook Page inside Instagram account settings. |
| **Pixel Tracking Missing Purchases** | Data sharing set to Standard (browser only) with ad blockers enabled on customer browsers. | In Shopify's Facebook channel settings, change data sharing mode to **Maximum** to leverage Conversions API (CAPI). |

---

## 🎯 Summary Checklist for Naza Noor

- [ ] Ensure Meta Business Portfolio admin access is ready.
- [ ] Connect Instagram Professional Account with Facebook Page.
- [ ] Install official **Facebook & Instagram** app in Shopify Admin.
- [ ] Enable **Maximum Data Sharing** (Pixel + Conversions API).
- [ ] Verify custom domain (`nazanoor.com`) in Meta Business Manager.
- [ ] Wait for Meta Commerce approval (24–48 hrs).
- [ ] Enable Shoppable Product Tagging on Instagram Feed & Reels.
