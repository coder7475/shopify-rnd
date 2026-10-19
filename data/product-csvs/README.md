# Shopify Sample Product Catalogs & CSV Import Guide

> Production-ready, validated CSV datasets for seeding Shopify development and staging stores with multi-variant products, high-resolution imagery, and custom metafields.

---

## Why This Exists

Testing themes, search facets, collection layouts, and checkout logic requires realistic catalog data. Standard placeholder text ("Lorem Ipsum") and missing image dimensions fail to reveal responsive layout breaks, aspect ratio inconsistencies, or search filter bugs.

This directory provides three curated, ready-to-import CSV datasets tailored for testing distinct e-commerce product categories on Shopify Online Store 2.0.

---

## 📊 Available Datasets

| File | Category | Language | Key Attributes Tested |
| :--- | :--- | :--- | :--- |
| **[`apparel.csv`](./apparel.csv)** | Ethnic Wear & Sarees (Naza Noor) | Bilingual (Bengali & English) | Custom Metafields (`material`, `occasion`, `work_type`, `origin`, `season`), Google Shopping taxonomies, high-res Pexels CDN media. |
| **[`jewelry.csv`](./jewelry.csv)** | Bracelets & Jewelry | English | Multi-variant color options, `Variant Compare At Price` sale badge triggers, multiple variant image mappings. |
| **[`home-and-garden.csv`](./home-and-garden.csv)** | Home Decor & Planters | English | Sized option variants, weight units (`kg`), standard inventory policies, Burst CDN images. |

---

## ⚡ Quick Start: How to Import Products

Follow these steps to import any dataset into your Shopify store:

### Step 1: Set Up Custom Metafield Definitions (Apparel Only)
If you are importing `apparel.csv`, configure your product metafield definitions in Shopify Admin **before** importing so Shopify automatically maps the custom columns:

1. In Shopify Admin, navigate to **Settings** > **Custom data** > **Products**.
2. Click **Add definition** for each of the following keys:
   - **Material**: Namespace and key `custom.material` (Type: Single-line text or List of text)
   - **Occasion**: Namespace and key `custom.occasion` (Type: Single-line text or List of text)
   - **Work Type**: Namespace and key `custom.work_type` (Type: Single-line text)
   - **Origin**: Namespace and key `custom.origin` (Type: Single-line text)
   - **Season**: Namespace and key `custom.season` (Type: Single-line text)

> **Note**: If you skip this step, Shopify will skip the `Metafield: *` columns during import.

### Step 2: Import via Shopify Admin
1. Go to **Shopify Admin** > **Products**.
2. Click the **Import** button in the top right header.
3. Click **Add file** and select the desired CSV file (e.g., `apparel.csv`).
4. **Checkbox Options**:
   - Check *"Overwrite any current products that have the same handle"* if updating existing records.
   - Uncheck it if you want to avoid altering existing catalog items.
5. Click **Upload and continue**.
6. Review the import preview screen to confirm that column headers map accurately (Title, SKU, Price, Image Src).
7. Click **Import products**.

---

## 📑 CSV Schema & Field Breakdown

Each file adheres strictly to the official [Shopify Product CSV specification](https://help.shopify.com/manual/products/import-export/using-csv):

```
┌────────────────────────────────────────────────────────────────────────┐
│                        CORE CSV HEADER MAPPING                         │
├────────────────────┬────────────────────┬──────────────────────────────┤
│ Product Identity   │ Variant & Pricing  │ Media & Taxonomies           │
│                    │                    │                              │
│ • Handle           │ • Option1 Name/Val │ • Image Src                  │
│ • Title            │ • Variant SKU      │ • Image Position             │
│ • Body (HTML)      │ • Variant Price    │ • Image Alt Text             │
│ • Vendor           │ • Compare At Price │ • SEO Title / Description    │
│ • Type / Tags      │ • Inventory Policy │ • Google Shopping Category   │
└────────────────────┴────────────────────┴──────────────────────────────┘
```

### Critical Fields to Understand:
- **`Handle`**: Unique product identifier in the URL slug (`/products/traditional-silk-saree`). Multiple rows with the same handle represent additional variants or additional images for that product.
- **`Variant Inventory Policy`**: Set to `deny` to prevent backorders when stock hits 0, or `continue` to permit overselling.
- **`Variant Compare At Price`**: When set higher than `Variant Price`, Shopify automatically triggers the theme's "Sale" badge and strikethrough pricing display.
- **`Image Src`**: Must be a publicly accessible HTTP/HTTPS URL. During import, Shopify downloads the file and uploads it to Shopify's CDN (`cdn.shopify.com`).

---

## ⚠️ Common Import Pitfalls & Troubleshooting

### 1. "Image failed to download"
- **Cause**: The external image URL is blocked, behind authentication, or has an expired CDN token.
- **Fix**: All images in these CSVs are hosted on public CDNs (Burst and Pexels). If your store environment blocks external requests, verify internet egress or re-host images on an open bucket.

### 2. "Handle already exists"
- **Cause**: You imported a product with a handle that already exists in the store without checking the *Overwrite* checkbox.
- **Fix**: Either enable the overwrite option or rename the `Handle` column value in the CSV.

### 3. Missing Variant Images
- **Cause**: The `Variant Image` column must match one of the URLs declared in the `Image Src` column for that same product handle.
- **Fix**: Ensure that any image linked to a specific variant is first declared in the main image list for that product.

---

## 🔗 Related Resources

- [Official Shopify Product CSV Guide](https://help.shopify.com/manual/products/import-export/using-csv)
- [Shopify Dev Store Generated Data Tool](https://shopify.dev/docs/apps/tools/development-stores/generated-data)
- [Image Sizes & Aspect Ratio Guide](../../docs/guides/image-sizes.md)
- [Search & Discovery Facet Configuration](../../docs/guides/search-and-discovery.md)
