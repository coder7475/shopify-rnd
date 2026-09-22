# Shopify Search & Discovery — RND

> **App:** [Shopify Search & Discovery](https://apps.shopify.com/search-and-discovery)
> **Cost:** Free (native first-party app by Shopify)
> **Access:** Shopify Admin → Apps → Search & Discovery
> **Shop App Integration:** Custom filters automatically sync to your **Shop Store** in the Shop sales channel

---

## Overview

The **Shopify Search & Discovery** app is Shopify's native tool that allows merchants to customize and optimize how customers find products across storefront search, collections, and recommendations. It replaces standard keyword matching and basic collection listings with a configurable merchandising engine — including **Product Boosts**, **Synonyms**, **Semantic Search**, **Faceted Filtering** (with metafields & metaobjects), and **Automated/Curated Recommendations**.

> [!NOTE]
> Because it is built directly into the Shopify platform, search queries and filter rendering occur server-side, maintaining fast page speeds and avoiding client-side layout shifts caused by external JavaScript apps.

---

## Why It Matters

| Metric / Stat | Grounded Insight |
|---|---|
| **2–3× higher conversion** | Shoppers who use storefront search convert at double to triple the rate of casual browsers. |
| **17–33% abandonment** (down from 67–90%) | Structured, intuitive faceted filtering drastically lowers drop-off on collection and search pages. |
| **Zero-result revenue loss** | Searches returning zero results represent instant bounce points; synonyms and boosts reclaim this lost traffic. |
| **Native Shop App Sync** | Filters configured in Search & Discovery automatically sync to your branded Shop app storefront. |

---

## Core Features

### 1. 🔍 Search Customization

The search engine can be fine-tuned using **Product Boosts**, **Synonyms**, and native **Semantic Understanding**.

#### 1a. Product Boosts

Manually promote specific products to the top of search results for designated customer queries.

**How it works:**
- Assign up to **10 search terms** per product boost.
- When a customer searches any of those exact terms, the boosted products display above standard algorithmic results.
- **Availability rule:** A product's position is boosted **only if it is available for sale**. Out-of-stock products are automatically placed at the end of results.
- Does **not** affect external search engines (e.g., Google or Bing).
- Does **not** apply when a customer query uses [search syntax](https://help.shopify.com/en/manual/online-store/storefront-search) (e.g., Boolean operators like `AND`, `OR`, `NOT`, or field prefixes like `tag:`).

**Steps to create a Product Boost:**
1. In Shopify Admin, navigate to **Apps → Search & Discovery**.
2. Go to **Search → Product boosts**.
3. Click **Create product boost**.
4. Select the products you want to feature.
5. In the **Search terms** field, type the keyword/phrase and click **Add** (up to 10 terms).
6. Click **Save**.

**Bulk editing via Metafields & Flow:**
- Boosts can be viewed and edited in bulk via the Shopify Bulk Editor using the `Search product boosts` metafield.
- Workflows in **Shopify Flow** can automate boost assignment based on inventory levels, tags, or promotional campaigns.

**Best Practices & Use Cases:**
- **Promote sparingly:** Boost only 1 to 3 hero SKUs per search term to avoid pushing relevant organic results down.
- **Do not boost typos or plurals:** Shopify's built-in typo tolerance and stemming already handle typos and singular/plural variations.
- **Use cases:**
  - *Product launches:* Boost "cold brew" to feature newly launched ready-to-drink cans.
  - *Seasonal merchandising:* Boost "gift guide" or "holiday" to surface holiday gift boxes.
  - *Inventory clearance:* Boost "summer dress" to promote end-of-season overstock.

---

#### 1b. Synonyms

Ensure customers find products even when they search with different regional terms, slang, or terminology than what is written in your product titles.

**How it works:**
- Create **synonym groups** containing interchangeable words or phrases.
- When a customer searches any term in a group, products containing any other term in the group are returned.
- Multi-word terms (e.g., `"belt bag"`) are evaluated as **phrase searches** (exact sequence match).
- Searching `sling` matches products with `sling` and products with the phrase `belt bag`.
- Searching `belt bag` matches products with `belt` + `bag` and products with `sling`.

**System Specifications & Limits:**
- **Word count:** Each synonym can contain 1 to 5 words.
- **Group limit:** Maximum **20 synonyms per synonym group**.
- **Store-wide limit:** Maximum **1,000 synonyms across the entire store**.
- **Uniqueness:** Each synonym must be unique across the entire store (the same word cannot exist in two different groups).
- **Exceptions:** Synonyms do not match against `SKU` or `barcode` fields, nor do they apply when queries include search syntax.

**Steps to create a Synonym Group:**
1. Navigate to **Apps → Search & Discovery → Search → Synonyms**.
2. Click **Create synonym group**.
3. Enter each term and click **Add**.
4. Enter a descriptive **Synonym group title** (used for internal admin display only).
5. Click **Save**.

**Best Practices & Use Cases:**
- Map terms identified in your **"Searches with no results"** analytics report.
- Include compound word variations (e.g., `"cross body"`, `"crossbody"`, `"cross-body"`).
- Keep groups tightly aligned to true equivalents (e.g., `sneakers` ↔ `trainers` ↔ `tennis shoes`); avoid broad groupings like `pants` ↔ `shorts`.

---

#### 1c. Semantic Understanding (AI-Powered)

Shopify's AI-driven semantic search interprets searcher intent and conceptual context rather than relying solely on literal keyword matches.

**How it works:**
- Analyzes product titles, descriptions, categories, and image data (including image colors and text within product images).
- Associates conceptual relationships (e.g., query: `christmas party shoes` → associates `christmas` with colors `red` and `green`, and `party shoes` with `pumps` or `heels`).
- Automatically enabled when your store meets eligibility requirements — **no manual activation required**.

**Eligibility Requirements:**
- Total store catalog has **fewer than 200,000 products**.
- Store plan is on **Shopify Grow, Advanced, or Shopify Plus**.
- Supported locales only (not supported for Japanese storefronts).
- Applies to **full storefront search**; does not apply to predictive search.

---

#### 1d. Search Result Types & Display Configuration

Merchants can control what content appears on search result pages and in predictive search dropdowns.

**Settings configurable in App Settings:**
- **Search Results Page:** Select whether to return **Products**, **Pages**, and/or **Blog posts** (default: all three).
- **Predictive Search Results:** Select whether the search bar dropdown requests **Products**, **Pages**, **Blog posts**, **Collections**, and/or **Query suggestions** (default: queries, products, collections, pages).
- **Out-of-stock products:** Configure unavailable products to be:
  - *Displayed at the end* of results (default)
  - *Displayed normally*
  - *Hidden completely*
- **Combined Listings display:** For stores using Shopify Combined Listings, choose to display:
  - *Only child products* (default)
  - *Only parent products*
  - *Both parent and child products*

> [!WARNING]
> If your theme sends an explicit `type` query parameter (e.g., `?type=product`) to the `/search` or `/search/suggest` endpoints, the theme parameter overrides the app settings.

---

### 2. 🎛️ Storefront Filtering

Faceted filtering allows shoppers to refine collection pages and search result pages by product attributes.

**Supported Filter Types:**
- **Product availability** (In stock / Out of stock)
- **Primary price** (Price range slider or ranges)
- **Product type**
- **Vendor / Brand**
- **Product options / Variant options** (e.g., Size, Color, Material)
- **Metafields** & **Metaobjects** (Custom data attributes)

**Filter System Limits & Specifications:**
- **Maximum filters per store:** **25 filters total** (including standard attributes and custom metafield filters).
- **Values displayed per filter:** A maximum of **100 filter values** can be displayed to shoppers at one time on the storefront.
- **Unique values per group:** Maximum **200 unique filter values** per filter group.
- **Store filter groups:** Maximum **1,000 filter groups** store-wide.

**Metafield & Metaobject Requirements:**
1. Metafields must have an active definition created in **Settings → Custom data**.
2. The definition must have the **Storefront filtering** checkbox enabled.
3. Supported metafield types: *Single-line text*, *Single-line text (list)*, *Integer number*, *Decimal number*, *True or false*, *Rating*, and *Metaobject references*.

**Context-Aware Dynamic Visibility (Sparse Data Rule):**
The app automatically hides filters that have no matching products in the currently viewed collection or active search result, preventing dead-end queries.

**Best Practices:**
- Maintain standardized values in metafields to avoid splitting filters into duplicates (e.g., stick strictly to `Navy` instead of mixing `Navy Blue` and `Dark Navy`).
- Keep storefront filters focused between 5 and 10 relevant facets per category to avoid cognitive overload.
- Utilize Metaobjects for visual swatch filtering (e.g., color swatches or pattern previews).

---

### 3. 🤝 Product Recommendations

Merchants can customize cross-sells and upsells across product detail pages (PDP) and cart surfaces.

| Type | Generation Method | Placement & Purpose |
|---|---|---|
| **Related Products** | Algorithmic (Shopify recommendation engine based on collections, purchase patterns, descriptions) | PDP ("You may also like") to encourage product exploration. |
| **Complementary Products** | Curated manually by the merchant in Search & Discovery | PDP & Cart ("Pairs well with", add-on accessories, refills) to boost AOV. |

**Steps to configure Complementary Recommendations:**
1. In Search & Discovery, click **Recommendations**.
2. Select the target product.
3. In the **Complementary products** block, click **Browse** and select up to 10 complementary items.
4. Set intent (e.g., cross-sell, bundle, replacement accessory).
5. Click **Save**.

---

### 4. 📊 Analytics & Optimization Framework

The app provides dedicated reporting in **Search & Discovery → Analytics**, supported by Shopify's core Behavior reports.

**Core Metrics Tracked:**
- **Top search terms:** Most frequently typed keywords.
- **Searches with no results:** Terms typed that returned zero products (critical for synonym and catalog gap analysis).
- **Search conversion rate:** Percentage of search sessions leading to an order.
- **Filter engagement:** Which filters are applied most frequently vs. ignored.

**Merchant Action Framework:**

| Analytics Finding | Root Cause | Recommended Action |
|---|---|---|
| Frequent search term with 0 results | Vocabulary mismatch | Add term to a **Synonym Group** or tag existing products. |
| High search volume, 0 conversions | Poor product relevancy or out-of-stock items | Add a **Product Boost** for high-performing alternative products; check inventory. |
| Filter never clicked | Obsolete attribute or too deep in list | Remove or reorder the filter in **Filters** section. |
| High exit rate on specific collection | Missing granular filters | Add relevant **Metafield filters** (e.g., Compatibility, Material). |

---

## Technical Specifications & Limitations

- **Theme Requirement:** Requires an Online Store 2.0 theme supporting JSON templates and standard facet filter liquid blocks (`filter.values`).
- **Boost Limits:** Max 10 search terms per product; applies strictly to in-stock items.
- **Synonym Limits:** Max 20 terms per group; max 1,000 synonyms store-wide; terms must be unique store-wide.
- **Filter Limits:** Max 25 filters per store; max 100 values displayed per filter.
- **Search Syntax Exclusion:** Queries containing operators (`AND`, `OR`, `NOT`, `-`, `tag:`) bypass manual boosts and synonyms.
- **Semantic Search Eligibility:** Requires Shopify Grow, Advanced, or Plus plans with fewer than 200,000 products; English/supported locales (non-Japanese).

---

## Official References

- [Shopify Help: Search & Discovery Overview](https://help.shopify.com/en/manual/online-store/search-and-discovery)
- [Shopify Help: Modifying Search Results](https://help.shopify.com/en/manual/online-store/storefront-search/search-and-discovery-modify-search)
- [Shopify Help: Customizing Storefront Filters](https://help.shopify.com/en/manual/online-store/search-and-discovery/filters)
- [Shopify Help: Product Recommendations](https://help.shopify.com/en/manual/online-store/search-and-discovery/recommendations)
- [Shopify Dev: Storefront Filtering Architecture & Limits](https://shopify.dev/docs/themes/navigation-search/filtering)
