# Shopify Collective — RND

> **App / Sales Channel:** [Shopify Collective](https://apps.shopify.com/collective)
> **Cost:** Free (no platform subscription fee; standard Shopify transaction and payment processing fees apply)
> **Access:** Shopify Admin → Apps → Shopify Collective (or Sales channels → Collective)

---

## Overview

**Shopify Collective** is Shopify's native B2B collaborative commerce platform. It enables Shopify merchants to partner directly with other verified Shopify brands to sell each other's products without purchasing upfront inventory, managing warehouse logistics, or manually exchanging invoices.

Unlike traditional dropshipping networks (which rely on third-party overseas suppliers or unvetted marketplaces), Shopify Collective operates as a **verified, direct merchant-to-merchant network**. Retailers expand their catalogs with complementary products from established brands, while suppliers gain scalable wholesale distribution across third-party storefronts.

```
+-----------------------------------------------------------------------------------+
|                            Shopify Collective Ecosystem                           |
|                                                                                   |
|   +-----------------------+                         +-------------------------+   |
|   |       SUPPLIER        |                         |        RETAILER         |   |
|   |  - Creates Price List |   Real-Time Sync        |  - Imports Products     |   |
|   |  - Sets Shipping Rules| ======================> |  - Sets Retail Markup   |   |
|   |  - Holds Inventory    |                         |  - Markets to Customers |   |
|   +-----------------------+                         +-------------------------+   |
|               ^                                                  |                |
|               |              Order Placed by Customer            |                |
|               +--------------------------------------------------+                |
|                                                                                   |
|   +---------------------------------------------------------------------------+   |
|   |                    Shopify Native Platform Layer                          |   |
|   |  1. Splits multi-brand orders at checkout                                 |   |
|   |  2. Routes supplier line items directly to Supplier admin                 |   |
|   |  3. Deducts wholesale cost via Shopify Payments & credits Supplier        |   |
|   |  4. Syncs tracking numbers from Supplier to Retailer & End Consumer       |   |
|   +---------------------------------------------------------------------------+   |
+-----------------------------------------------------------------------------------+
```

---

## Key Roles & Architectural Concepts

| Entity / Concept | Role & Functionality |
|---|---|
| **Supplier** | The brand holding physical inventory. Creates price lists, defines shipping rates, approves retailer partnerships, and fulfills orders directly to end customers. |
| **Retailer** | The merchant listing supplier products. Merchandises imported items on their storefront, defines customer retail prices, drives traffic, and earns margin. |
| **Price List** | A supplier-defined catalog specifying wholesale costs and shipping options. Can be **Public** (open to network) or **Custom** (invite-only). |
| **Collective Shipping Profile** | A dedicated shipping profile automatically created in the retailer's store where all imported Collective products reside. |
| **Automated Payout Split** | Real-time debit and credit handled via **Shopify Payments** upon order fulfillment. |

---

## Core Features & Mechanics

### 1. 🛍️ Catalog Import & Real-Time Syncing

- **Product Data Sync:** When a retailer imports products from a supplier's price list, Shopify continuously synchronizes product titles, descriptions, photography, variants (sizes, colors, SKUs), and live inventory levels.
- **Inventory Protection:** Stock levels sync in real time. If a supplier sells out of an item through their own DTC channel, the inventory drops to zero on all connected retailers' storefronts simultaneously, preventing overselling.
- **Retailer Merchandising:** Retailers cannot alter the underlying supplier product details (title, imagery, description), but they can categorize them into their own custom collections, assign store tags, and position them strategically on navigation menus and landing pages.

---

### 2. 💰 Price Lists, Margins & Payments

Suppliers retain complete authority over wholesale pricing and partner margins.

**Price List Formats:**
- **Public Price Lists:** Published to the Collective supplier discovery directory, allowing any eligible retailer in the region to request connection and import products.
- **Custom Price Lists:** Private, invite-only lists configured with specific margin structures or exclusive product lines for designated retail partners.

**Margin & Settlement Mechanics:**
1. **Retail Pricing:** The retailer sets the customer-facing retail price (must meet or exceed the supplier's wholesale cost).
2. **Checkout:** The customer purchases the product on the retailer's storefront, paying full retail price + applicable taxes and shipping.
3. **Automated Settlement:**
   - Once the supplier marks the order as fulfilled, Shopify automatically debits the wholesale product cost (and agreed shipping fee) from the retailer's Shopify Payments balance.
   - The funds are transferred directly into the supplier's Shopify Payments payout.
   - The retailer retains the margin difference (`Retail Price – Supplier Cost = Net Profit`).
   - No manual invoicing, credit terms, or third-party bank wires are required.

---

### 3. 🚚 Shipping Architecture & Zone Configurations

Shipping rules are established by the supplier inside each **Price List** and passed to the retailer's checkout.

**Supplier Shipping Options (per geographic zone):**
- **Calculated at checkout (Default):** Dynamically applies the supplier's own shipping rules (weight-based, dimension-based, or location-based) directly at the retailer's checkout.
- **Flat rate:** The supplier charges a fixed shipping amount per order. On the retailer's storefront checkout, this rate appears labeled as **"Standard Shipping"**.
- **Manually invoice retailer:** The supplier invoices shipping costs offline/separately.
- **Don't ship to this zone:** Restricts products from being purchased in specific geographic zones.

**Retailer Shipping Profile Integration:**
- Imported products are automatically assigned to the **"Shopify Collective"** shipping profile in the retailer's admin (**Settings → Shipping and delivery**).
- Retailers can adjust transit time descriptions or customize rules if combining Collective products with native warehouse inventory.

---

### 4. 📦 Automated Order Routing & Fulfillment Flow

When an order containing Collective items is placed on a retailer's store:

1. **Order Splitting:** Shopify automatically splits the order. Line items belonging to the supplier are cloned into a new order in the supplier's Shopify admin.
2. **Supplier Notification:** The supplier fulfills the order like any normal DTC order, printing packing slips and applying their standard carrier labels.
3. **Tracking Synchronization:** When the supplier inputs the carrier tracking number and marks the order fulfilled, tracking data instantly syncs back to the retailer's order admin.
4. **Customer Communication:** The retailer's storefront sends standard shipping confirmation and tracking emails to the customer under the retailer's brand.

---

### 5. 🤝 Partner Discovery & Connection Modes

- **In-App Discovery Directory:** Retailers can browse vetted Shopify brands categorized by industry (Apparel, Beauty, Home, Food & Beverage) and request direct partnerships.
- **Direct Link / QR Invitation:** Brands with pre-existing wholesale or influencer relationships can generate direct invite links to connect instantly.

---

## Eligibility Requirements (Current 2025/2026 Standards)

To participate in Shopify Collective, merchants must satisfy the following criteria:

| Requirement | Specification |
|---|---|
| **Shopify Plan** | Must be on an active, paid Shopify plan (Basic, Shopify, Advanced, or Plus). |
| **Sales Revenue Threshold** | **Eliminated.** (The legacy requirement of $50,000 USD annual revenue was officially removed in late 2025; early-stage stores are eligible). |
| **Payment Gateway** | Must have **Shopify Payments** fully activated with active payouts enabled. |
| **Currency & Location Matching** | Retailer and supplier must reside in the **same country/region** and transact in the **same currency** (e.g., US store to US store in USD, Canadian store to Canadian store in CAD). Cross-border Collective trading is restricted. |
| **Geographic Availability** | Available in the **United States, Canada, United Kingdom, and 36+ additional countries**. |
| **Tax Compliance** | UK, Canadian, and EU merchants must utilize Shopify Tax, Basic Tax, or an approved tax calculation app with valid tax registration (e.g., VAT/GST). |

---

## Retailer vs. Supplier Tactical Use Cases

### For Retailers
- **Zero-Capital Catalog Expansion:** A luxury bedding brand sells designer throw pillows and sleep masks from partner brands without holding inventory.
- **Pre-Validation of New Categories:** Test consumer demand for a new product category before investing in large manufacturing minimum order quantities (MOQs).
- **AOV / Cross-Sell Bundling:** An artisanal coffee roaster features handmade ceramic mugs and pour-over kettles from independent ceramic brands.

### For Suppliers
- **Incremental Wholesale Distribution:** Reach thousands of new consumers through established niche storefronts without paying upfront ad acquisition costs.
- **Controlled Brand Presence:** Select which retailers can feature products; set wholesale margins and minimum retail prices.
- **Automated Fulfillment Operations:** Incoming partner orders merge seamlessly into standard warehouse fulfillment queues alongside DTC orders.

---

## Shopify Collective vs. Traditional Dropshipping

| Dimension | Shopify Collective | Traditional Dropshipping (e.g., AliExpress, DSers) |
|---|---|---|
| **Supplier Vetting** | Verified, legitimate Shopify brand owners | Anonymous third-party trading entities |
| **Product Quality** | Premium, branded consumer goods | High variability; unbranded/generic items |
| **Inventory Reliability** | Native, real-time sync with zero manual lag | Periodic sync; high cancellation/out-of-stock risk |
| **Shipping Speed** | Domestic ground shipping (typically 2–5 business days) | Often international ePacket (10–25 business days) |
| **Financial Settlement** | Native payout debits via Shopify Payments | Manual payment per order or external credit lines |
| **Software Fees** | **Free** native app (standard credit card processing rates) | Monthly app subscriptions + software transaction markups |

---

## Limitations & Operational Considerations

- **Strict Shopify Payments Dependency:** Both parties must use Shopify Payments. Stores relying on third-party processors (e.g., Authorize.Net, PayPal standalone) cannot use Collective.
- **Domestic-Only Partnerships:** Cross-border transactions (e.g., US retailer selling UK supplier goods) are not currently supported due to multi-currency and international customs/tax handling.
- **No Product Description Customization:** Retailers cannot customize product copy, titles, or variant photography; imported data reflects supplier listings verbatim.
- **Combined Shipping on Multi-Brand Orders:** If a customer purchases native products and Collective supplier products in one checkout, shipping costs may compound. Merchants should monitor cart abandonment and adjust shipping profiles accordingly.
- **Returns & Exchanges:** Retailers must establish clear return routing agreements with suppliers; returns must generally be received and inspected by the original supplier.

---

## Official References

- [Shopify Help: Shopify Collective Overview](https://help.shopify.com/en/manual/sell-online/collective)
- [Shopify Help: Collective Eligibility Requirements](https://help.shopify.com/en/manual/sell-online/collective/eligibility)
- [Shopify Help: Collective for Suppliers (Price Lists & Shipping)](https://help.shopify.com/en/manual/sell-online/collective/suppliers)
- [Shopify Help: Collective for Retailers (Importing & Selling)](https://help.shopify.com/en/manual/sell-online/collective/retailers)
- [Shopify App Store: Shopify Collective](https://apps.shopify.com/collective)
