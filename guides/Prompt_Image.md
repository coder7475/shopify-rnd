# Shopify Image Prompt Guide

A reusable prompt template for generating, optimizing, and implementing responsive images in Shopify stores.

---

## Quick Prompt (Copy & Use)

```
Create/optimize a [IMAGE TYPE] image for a Shopify store.

Dimensions: [WIDTH] × [HEIGHT] px
Aspect Ratio: [RATIO]
Format: WebP (preferred) or JPEG at 75-85% quality
Max File Size: [TARGET] KB

Requirements:
- Keep critical content (text, product, CTA) in the central 60% of the canvas
- Use descriptive, hyphen-separated filename: [product-name]-[type]-[size].webp
- Optimized for both retina (2x) and standard displays
- Compress for web without visible quality loss

Deliver: Final optimized image file
```

---

## Image Type Specifications

### Product Image

**Prompt template:**

```
Create a product image for a Shopify store.

Product: [PRODUCT NAME/DESCRIPTION]
Dimensions: 2048 × 2048 px (square, 1:1)
Format: WebP, quality 80
Max file size: 200 KB

Requirements:
- Square 1:1 aspect ratio (Shopify default)
- Clean, white or neutral background
- High detail for zoom functionality (min 800×800 for zoom)
- Sharp on retina displays
- Filename: [product-name]-main-2048x2048.webp
```

### Hero / Banner Image

**Prompt template:**

```
Create a hero banner image for a Shopify store homepage.

Purpose: [HERO MESSAGE/PROMOTION]
Dimensions: 1920 × 1080 px (16:9)
Format: WebP, quality 80
Max file size: 500 KB

Requirements:
- Keep text, product, and CTA in the central 60% (edges get cropped on mobile)
- High visual impact, brand-consistent
- Compress aggressively (hero is the #1 LCP weight)
- Filename: hero-banner-1920x1080.webp
```

### Collection Image

**Prompt template:**

```
Create a collection/category image for a Shopify store.

Collection: [COLLECTION NAME]
Dimensions: 1024 × 1024 px (square, 1:1)
Format: WebP, quality 80
Max file size: 400 KB

Requirements:
- Square 1:1 (safest for center-crop themes)
- Clean, simple visual (reads well at thumbnail size)
- Consistent style across all collection images
- Filename: [collection-name]-cover-1024x1024.webp
```

### Blog Featured Image

**Prompt template:**

```
Create a blog post featured image for a Shopify store.

Topic: [BLOG POST TITLE/TOPIC]
Dimensions: 1200 × 628 px (1.91:1 — Open Graph standard)
Format: WebP, quality 80
Max file size: 300 KB

Requirements:
- 1.91:1 ratio (doubles as social sharing image)
- Clear, readable at small sizes
- Text-free (overlay text in CMS instead)
- Filename: [blog-slug]-featured-1200x628.webp
```

### Slideshow / Carousel Image

**Prompt template:**

```
Create a slideshow image for a Shopify store.

Slide purpose: [SLIDE MESSAGE]
Dimensions: 1920 × 1080 px (16:9)
Format: WebP, quality 80
Max file size: 500 KB

Requirements:
- All slides must use identical dimensions
- Keep key content centered (edges crop on mobile)
- Visual consistency across all slides in the set
- Filename: slide-[N]-1920x1080.webp
```

### Logo

**Prompt template:**

```
Create a logo for a Shopify store.

Brand: [BRAND NAME]
Dimensions: 400 × 200 px (2:1 or per design)
Format: PNG with transparency (or SVG)
Max file size: 50 KB

Requirements:
- Transparent background (PNG) or vector (SVG)
- Crisp at small sizes (header, footer, favicon)
- Filename: logo-[brand].png
```

### Favicon

**Prompt template:**

```
Create a favicon for a Shopify store.

Brand: [BRAND NAME]
Dimensions: 32 × 32 px
Format: PNG or ICO
Max file size: 10 KB

Requirements:
- Simple, recognizable at 32×32
- Filename: favicon-32x32.png
```

---

## Responsive Image Prompts

### Product Card Grid

```
Generate a responsive Liquid snippet for a product card image in a 4-column grid.

Image: product.featured_image
Layout: 4 columns desktop, 2 columns tablet, 1 column mobile
Max source width: 600
```

### LCP Hero Image (Above Fold)

### Collection Grid

```
Generate a responsive Liquid snippet for a collection card in a 3-column grid.

Image: collection.image
Layout: 3 columns desktop, 2 columns tablet, 1 column mobile
Max source width: 800
```

---

## `sizes` Attribute Quick Reference

| Layout | `sizes` Value |
| --- | --- |
| Full-width hero/banner | `100vw` |
| 2-column grid | `(min-width: 768px) 50vw, 100vw` |
| 3-column grid | `(min-width: 990px) 33vw, (min-width: 750px) 50vw, 100vw` |
| 4-column grid | `(min-width: 1200px) 25vw, (min-width: 768px) 50vw, 100vw` |
| Product page main | `(min-width: 768px) 50vw, 100vw` |
| Sidebar + main content | `(min-width: 1000px) 60vw, 100vw` |
| Lazy images (any layout) | `auto` |

---

## srcset Width Presets

| Image Type | Recommended srcset Widths |
| --- | --- |
| Hero / banner | `800, 1200, 1600, 2000, 2400` |
| Product card | `200, 300, 400, 600` |
| Collection card | `300, 400, 600, 800` |
| Blog featured | `400, 600, 800, 1200` |
| Slideshow | `800, 1200, 1600` |

---

## Optimization Checklist

Before finalizing any Shopify image:

- [ ] **Dimensions** match the recommended size for the image type
- [ ] **Aspect ratio** is correct (1:1 for products, 16:9 for heroes, 1.91:1 for blog)
- [ ] **File format** is WebP (preferred) or JPEG at 75-85% quality
- [ ] **File size** is under the target (see table below)
- [ ] **Filename** is descriptive, lowercase, hyphen-separated
- [ ] **Critical content** is centered (within 60% of canvas)
- [ ] **`image_tag`** is used (not manual CDN URLs)
- [ ] **`sizes`** attribute matches the CSS layout
- [ ] **`srcset`** has 4-6 widths max
- [ ] **LCP image** uses `loading="eager"` + `fetchpriority="high"`
- [ ] **Below-fold images** use `loading="lazy"`
- [ ] **`width`/`height`** attributes are present (auto via `image_tag`)

### Target File Sizes

| Image Type | Max File Size |
| --- | --- |
| Product image | 200 KB |
| Hero / banner | 500 KB |
| Collection image | 400 KB |
| Blog featured | 300 KB |
| Logo | 50 KB |
| Favicon | 10 KB |

---

## References

- [SHOPIFY-IMAGE-SIZES-GUIDE.md](./SHOPIFY-IMAGE-SIZES-GUIDE.md) — Full reference guide
- [Video: What's a good image size for Shopify?](https://www.youtube.com/watch?v=ZaAmV0vk20w)
- [Figma: Image Banner Testing](https://www.figma.com/design/UEzciqYeY7jfII3twrh2IU/Image-Banner-Testing?node-id=0-1&p=f)
- [Shopify Docs: Responsive Images](https://shopify.dev/docs/storefronts/themes/best-practices/performance/use-responsive-images)
- [Shopify Docs: image_tag filter](https://shopify.dev/docs/api/liquid/filters/image_tag)
- [Shopify Docs: image_url filter](https://shopify.dev/docs/api/liquid/filters/image_url)
- [Responsive Image Linter (Chrome Extension)](https://chromewebstore.google.com/detail/responsive-image-linter/mnddginionlghpbkfadlgdoaoemnahga)
