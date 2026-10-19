# Custom Shopify Product Reviews Section (Metaobjects & Liquid Guide)

> A complete, step-by-step implementation guide to building an app-free, zero-subscription custom product review section on Shopify using native **Metaobjects**, **Metafields**, and **Liquid**.

**Primary References:**
- **Video Tutorial:** [Shopify Metaobjects Product Reviews Section Tutorial](https://www.youtube.com/watch?v=tuOGmwScKNo&list=PLso98fHIIDeYkjCBBE9eHYUYtBdVZmd7r&index=22) by Nick Drishinski
- **Source Code Repository:** [ndrishinski/blogs - product-reviews.liquid](https://github.com/ndrishinski/blogs/blob/master/product-reviews/sections/product-reviews.liquid)

---

## Table of Contents

1. [Architecture & Why Build a Custom Review Section](#1-architecture--why-build-a-custom-review-section)
2. [Data Model: Metaobject & Metafield Definitions](#2-data-model-metaobject--metafield-definitions)
   - [Step 1: Create the `product_reviews` Metaobject](#step-1-create-the-product_reviews-metaobject)
   - [Step 2: Create the Product Metafield Reference](#step-2-create-the-product-metafield-reference)
3. [Populating Review Data in Shopify Admin](#3-populating-review-data-in-shopify-admin)
4. [The Liquid Code Implementation](#4-the-liquid-code-implementation)
5. [Code Deep-Dive & Key Mechanics](#5-code-deep-dive--key-mechanics)
   - [Dynamic Rating Summary & Calculations](#dynamic-rating-summary--calculations)
   - [Half-Star SVG Gradient Fill](#half-star-svg-gradient-fill)
   - [Progress Bar Percentages](#progress-bar-percentages)
   - [Initials Fallback for Avatars](#initials-fallback-for-avatars)
   - [Client-Side Pagination (Load More / Show Less)](#client-side-pagination-load-more--show-less)
6. [Theme Customizer Setup & Product Template Placement](#6-theme-customizer-setup--product-template-placement)
7. [Enhancements & Production Considerations](#7-enhancements--production-considerations)
   - [Fixing Metafield Key Mismatch](#fixing-metafield-key-mismatch)
   - [SEO Schema (AggregateRating & Review JSON-LD)](#seo-schema-aggregaterating--review-json-ld)
   - [Float Division & Star Accuracy](#float-division--star-accuracy)
   - [Automated Collection via Flow or Custom Form](#automated-collection-via-flow-or-custom-form)
8. [App vs. Custom Metaobject Comparison](#8-app-vs-custom-metaobject-comparison)

---

## 1. Architecture & Why Build a Custom Review Section

After Shopify deprecated the official **Shopify Product Reviews (SPR)** app in May 2024, many store owners were forced into 3rd-party recurring subscriptions (Judge.me, Loox, Yotpo, Okendo) or bloated external JavaScript bundles.

Using Shopify's native **Metaobjects** and **Metafields**, you can build a native review system that lives directly inside your theme:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        DATA ARCHITECTURE                               │
│                                                                        │
│   Metaobject Definition ("product_reviews")                            │
│   ├── customer_name   (Single line text)                              │
│   ├── customer_image  (File: Image)                                   │
│   ├── date            (Date)                                           │
│   ├── stars           (Integer: 1 to 5)                                │
│   └── review          (Multi-line text)                                │
│                            ▲                                           │
│                            │ Referenced by                             │
│   Product Metafield (`custom.da_stuff` or `custom.product_reviews`)    │
│   └── Type: List of Metaobjects (Reference -> product_reviews)         │
│                            ▲                                           │
│                            │ Queried by                                │
│   Liquid Section (`sections/product-reviews.liquid`)                   │
│   ├── Calculates Average Rating & Score Breakdown                     │
│   ├── Renders Half-Star SVGs & Percentage Progress Bars                │
│   └── Handles Pagination (Load More / Show Less)                      │
└────────────────────────────────────────────────────────────────────────┘
```

### Key Advantages:
- **Zero Ongoing Subscription Fees**: 100% free forever without tiered limits.
- **Superior Page Speed & Core Web Vitals**: No external tracking scripts, no third-party HTTP requests, no iframes, no layout shift (CLS).
- **Native Theme Styling**: Matches store typography, colors, and design seamlessly.
- **Complete Editorial Control**: Native moderation directly in Shopify Admin without 3rd-party dashboards.

---

## 2. Data Model: Metaobject & Metafield Definitions

To set this up, you configure two Shopify schema components in your Shopify admin.

### Step 1: Create the `product_reviews` Metaobject

1. In Shopify Admin, navigate to **Settings** > **Custom data**.
2. Under **Metaobjects**, click **Add definition**.
3. Fill in the definition details:
   - **Name**: `Product Review`
   - **Type / Handle**: `product_reviews`
4. Add the following fields:

| Field Name | Type | Key / Handle | Settings / Validation |
| :--- | :--- | :--- | :--- |
| **Customer Name** | Single line text | `customer_name` | Required |
| **Customer Image** | File | `customer_image` | Image only (optional) |
| **Date** | Date | `date` | Optional |
| **Stars** | Integer (Number) | `stars` | Minimum: `1`, Maximum: `5` |
| **Review** | Multi-line text | `review` | Optional (stores review comment) |

5. Click **Save**.

---

### Step 2: Create the Product Metafield Reference

Now attach the list of reviews to your products:

1. In Shopify Admin, navigate to **Settings** > **Custom data** > **Products**.
2. Click **Add definition**.
3. Configure the metafield:
   - **Name**: `Product Reviews`
   - **Namespace and key**: 
     - *Code default from tutorial:* `custom.da_stuff`
     - *Recommended production key:* `custom.product_reviews` (update the liquid assignment accordingly)
   - **Select type**: Choose **Metaobject**.
   - **Reference type**: Select `Product Review` (`product_reviews`).
   - **List option**: Select **List of values** (this allows one product to link to multiple reviews).
4. Click **Save**.

---

## 3. Populating Review Data in Shopify Admin

### Method A: Creating Review Entries First

1. Go to **Content** > **Metaobjects** in Shopify Admin.
2. Select **Product Review** (`product_reviews`).
3. Click **Add entry**.
4. Populate:
   - **Customer Name**: e.g., `Jane Doe`
   - **Customer Image**: Upload an avatar image (or leave blank to use the initials fallback)
   - **Date**: e.g., `2024-04-15`
   - **Stars**: e.g., `5`
   - **Review**: e.g., `Absolutely love this product! The quality exceeded my expectations.`
5. Click **Save**.

### Method B: Assigning Reviews to a Product

1. Navigate to **Products** and click your desired product.
2. Scroll down to the bottom **Metafields** card.
3. Locate **Product Reviews** (or `da_stuff`).
4. Click into the field and select the review metaobject entries you wish to link to this product.
5. Drag to reorder if desired, then click **Save**.

---

## 4. The Liquid Code Implementation

Create a new file in your theme code: `sections/product-reviews.liquid`.

```liquid
{% comment %}
  Product Reviews Section - Using Metaobjects
  - Uses a metafield 'custom.da_stuff' which is a list of metaobject references
    (Change to 'custom.product_reviews' if using standard naming)
  - Each metaobject is of type 'product_reviews' with fields:
    - product_reviews.customer_name
    - product_reviews.customer_image
    - product_reviews.date
    - product_reviews.stars
    - product_reviews.review
  - Only displays if reviews exist for the current product
{% endcomment %}

{% assign reviews_references = product.metafields.custom.da_stuff.value %}
{% assign total_reviews = 0 %}
{% assign total_stars = 0 %}
{% assign five_star_count = 0 %}
{% assign four_star_count = 0 %}
{% assign three_star_count = 0 %}
{% assign two_star_count = 0 %}
{% assign one_star_count = 0 %}

{% assign list_thing = "" %}
{% for piece in reviews_references %}
  {% assign dog = piece | json %}
  {% assign list_thing = list_thing | append: dog | append: '&&' %}
{% endfor %}

{% assign total_reviews = list_thing | split: '&&' %}

{% comment %} Process reviews and calculate statistics {% endcomment %}
{% if reviews_references != blank %}
  {% for review_ref in reviews_references %}
    {% assign review = review_ref %}
    {% assign star_rating = review.stars | plus: 0 %}
    {% assign total_stars = total_stars | plus: star_rating %}
    
    {% case star_rating %}
      {% when 5 %}
        {% assign five_star_count = five_star_count | plus: 1 %}
      {% when 4 %}
        {% assign four_star_count = four_star_count | plus: 1 %}
      {% when 3 %}
        {% assign three_star_count = three_star_count | plus: 1 %}
      {% when 2 %}
        {% assign two_star_count = two_star_count | plus: 1 %}
      {% when 1 %}
        {% assign one_star_count = one_star_count | plus: 1 %}
    {% endcase %}
  {% endfor %}

  {% if total_reviews.size > 0 %}
    {% assign average_rating = total_stars | divided_by: total_reviews.size | round: 1 %}
    {% assign five_star_percent = five_star_count | times: 100 | divided_by: total_reviews.size %}
    {% assign four_star_percent = four_star_count | times: 100 | divided_by: total_reviews.size %}
    {% assign three_star_percent = three_star_count | times: 100 | divided_by: total_reviews.size %}
    {% assign two_star_percent = two_star_count | times: 100 | divided_by: total_reviews.size %}
    {% assign one_star_percent = one_star_count | times: 100 | divided_by: total_reviews.size %}
  {% endif %}
{% endif %}

{% if total_reviews.size > 0 %}
<div class="product-reviews-section" id="product-reviews">
  <style>
    .product-reviews-section {
      max-width: 1024px;
      margin: 0 auto;
      padding: 24px;
      background-color: white;
    }

    .reviews-title {
      font-size: 24px;
      font-weight: bold;
      color: #111827;
      margin-bottom: 32px;
    }

    .rating-overview {
      margin-bottom: 32px;
    }

    .rating-summary {
      display: flex;
      align-items: center;
      gap: 16px;
      margin-bottom: 24px;
    }

    .rating-score {
      text-align: left;
    }

    .score-number {
      font-size: 48px;
      font-weight: bold;
      color: #111827;
      margin-bottom: 8px;
    }

    .stars {
      display: flex;
      gap: 4px;
      margin-bottom: 4px;
    }

    .star {
      width: 20px;
      height: 20px;
    }

    .star.filled {
      color: #fbbf24;
      fill: #fbbf24;
    }

    .star.empty {
      color: #e5e7eb;
      fill: #e5e7eb;
    }

    .stars.small .star {
      width: 16px;
      height: 16px;
    }

    .review-count {
      color: #6b7280;
      font-size: 14px;
    }

    .rating-breakdown {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .rating-row {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .rating-number {
      font-size: 14px;
      color: #374151;
      width: 12px;
    }

    .progress-bar {
      flex: 1;
      height: 8px;
      background-color: #f3f4f6;
      border-radius: 4px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      background-color: #fbbf24;
      border-radius: 4px;
    }

    .percentage {
      font-size: 14px;
      color: #6b7280;
      width: 36px;
      text-align: right;
    }

    .reviews-section-title {
      font-size: 20px;
      font-weight: bold;
      color: #111827;
      margin-bottom: 24px;
    }

    .reviews-container {
      display: flex;
      flex-direction: column;
      gap: 24px;
    }

    .review {
      padding: 16px 0;
      border-bottom: 1px solid #f3f4f6;
    }

    .review:last-child {
      border-bottom: none;
    }

    .review-header {
      display: flex;
      gap: 16px;
      margin-bottom: 12px;
    }

    .avatar {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: #e5e7eb;
      background-size: cover;
      background-position: center;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 500;
      color: #374151;
      font-size: 14px;
      flex-shrink: 0;
    }

    .review-content {
      flex: 1;
    }

    .reviewer-info {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 4px;
    }

    .reviewer-name {
      font-weight: 500;
      color: #111827;
    }

    .review-date {
      color: #6b7280;
      font-size: 14px;
    }

    .review-rating {
      margin-bottom: 8px;
    }

    .review-text {
      color: #374151;
      line-height: 1.5;
      font-size: 14px;
    }

    .load-more {
      margin-top: 24px;
      text-align: center;
    }

    .load-more-btn {
      background: none;
      border: 1px solid #e5e7eb;
      padding: 8px 16px;
      border-radius: 6px;
      color: #374151;
      cursor: pointer;
      font-size: 14px;
      transition: background-color 0.2s;
    }

    .load-more-btn:hover {
      background-color: #f9fafb;
    }
  </style>

  <h1 class="reviews-title">{{ section.settings.title | default: product.title | append: ' Reviews' }}</h1>

  <!-- Rating Overview -->
  <div class="rating-overview">
    <div class="rating-summary">
      <div class="rating-score">
        <div class="score-number">{{ average_rating | default: '0.0' }}</div>
        <div class="stars">
          {% assign rounded_rating = average_rating | floor %}
          {% assign plus_one = rounded_rating | plus: 1 %}
          {% for i in (1..5) %}
            {% if i <= rounded_rating %}
              <svg class="star filled" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            {% elsif i == plus_one %}
              <svg class="star" viewBox="0 0 24 24">
                <defs>
                  <linearGradient id="half-fill-{{ section.id }}" x1="0" x2="100%" y1="0" y2="0">
                    <stop offset="50%" stop-color="#fbbf24" />
                    <stop offset="50%" stop-color="#e5e7eb" />
                  </linearGradient>
                </defs>
                <path fill="url(#half-fill-{{ section.id }})" d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            {% else %}
              <svg class="star empty" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            {% endif %}
          {% endfor %}
        </div>
        <div class="review-count">{{ total_reviews.size }} review{% if total_reviews.size != 1 %}s{% endif %}</div>
      </div>
    </div>

    {% if section.settings.show_rating_breakdown %}
    <!-- Rating Breakdown -->
    <div class="rating-breakdown">
      <div class="rating-row">
        <span class="rating-number">5</span>
        <div class="progress-bar">
          <div class="progress-fill" style="width: {{ five_star_percent }}%"></div>
        </div>
        <span class="percentage">{{ five_star_percent }}%</span>
      </div>
      <div class="rating-row">
        <span class="rating-number">4</span>
        <div class="progress-bar">
          <div class="progress-fill" style="width: {{ four_star_percent }}%"></div>
        </div>
        <span class="percentage">{{ four_star_percent }}%</span>
      </div>
      <div class="rating-row">
        <span class="rating-number">3</span>
        <div class="progress-bar">
          <div class="progress-fill" style="width: {{ three_star_percent }}%"></div>
        </div>
        <span class="percentage">{{ three_star_percent }}%</span>
      </div>
      <div class="rating-row">
        <span class="rating-number">2</span>
        <div class="progress-bar">
          <div class="progress-fill" style="width: {{ two_star_percent }}%"></div>
        </div>
        <span class="percentage">{{ two_star_percent }}%</span>
      </div>
      <div class="rating-row">
        <span class="rating-number">1</span>
        <div class="progress-bar">
          <div class="progress-fill" style="width: {{ one_star_percent }}%"></div>
        </div>
        <span class="percentage">{{ one_star_percent }}%</span>
      </div>
    </div>
    {% endif %}
  </div>

  <!-- Reviews Section -->
  <div class="reviews-section">
    <h2 class="reviews-section-title">Reviews</h2>

    <div class="load-more">
      <button style="display: none;" id="show-less-reviews" class="load-more-btn">Show Less Reviews</button>
    </div>

    <div class="reviews-container">
      {% assign reviews_per_page = section.settings.reviews_per_page | default: 3 | plus: 0 %}
      {% for review in reviews_references %}
        {% assign review_index = forloop.index0 %}
        <div class="review {% if review_index >= reviews_per_page %}hidden-review{% endif %}"{% if review_index >= reviews_per_page %} style="display: none;"{% endif %}>
          <div class="review-header">
            {% if review.customer_image != blank %}
              <div class="avatar" style="background-image: url('{{ review.customer_image | img_url: '80x80', crop: 'center' }}');"></div>
            {% else %}
              <div class="avatar">
                {% assign name_parts = review.customer_name | split: ' ' %}
                {{ name_parts[0] | slice: 0, 1 | upcase }}{% if name_parts.size > 1 %}{{ name_parts.last | slice: 0, 1 | upcase }}{% endif %}
              </div>
            {% endif %}
            <div class="review-content">
              <div class="reviewer-info">
                <span class="reviewer-name">{{ review.customer_name }}</span>
                {% if review.date != blank %}
                  <span class="review-date">{{ review.date | date: '%B %d, %Y' }}</span>
                {% endif %}
              </div>
              <div class="review-rating">
                <div class="stars small">
                  {% assign review_rating = review.stars | plus: 0 %}
                  {% for i in (1..5) %}
                    {% if i <= review_rating %}
                      <svg class="star filled" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
                      </svg>
                    {% else %}
                      <svg class="star empty" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
                      </svg>
                    {% endif %}
                  {% endfor %}
                </div>
              </div>
              {% if review.review != blank %}
                <p class="review-text">{{ review.review }}</p>
              {% endif %}
            </div>
          </div>
        </div>
      {% endfor %}
    </div>
    {% if total_reviews.size > reviews_per_page %}
      <div class="load-more">
        <button class="load-more-btn" id="load-more-reviews">Load More Reviews</button>
      </div>
    {% endif %}
  </div>

  <script>
  document.addEventListener('DOMContentLoaded', function() {
    const reviewsPerPage = {{ section.settings.reviews_per_page | default: 3 }};
    const reviews = document.querySelectorAll('.review.hidden-review');
    const button = document.getElementById('load-more-reviews');
    const showLess = document.getElementById('show-less-reviews');

    if (button) {
      button.addEventListener('click', () => {
        let count = 0;
        for (let i = 0; i < reviews.length; i++) {
          if (reviews[i].style.display === 'none' && count < reviewsPerPage) {
            reviews[i].style.display = 'block';
            count++;
          }
        }

        // Hide button if no more hidden reviews
        const remaining = Array.from(reviews).filter(r => r.style.display === 'none');
        if (remaining.length === 0) {
          button.style.display = 'none';
        }

        if (showLess) showLess.style.display = 'inline-block';
      });
    }

    if (showLess) {
      showLess.addEventListener('click', () => {
        for (let i = 0; i < reviews.length; i++) {
          reviews[i].style.display = 'none';
        }
        showLess.style.display = 'none';
        if (button) button.style.display = 'inline-block';
      });
    }
  });
  </script>
</div>
{% endif %}

{% schema %}
{
  "name": "Product Reviews",
  "tag": "section",
  "class": "product-reviews-section",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "label": "Section Title",
      "default": "Reviews",
      "info": "Leave blank to use product title"
    },
    {
      "type": "checkbox",
      "id": "show_rating_breakdown",
      "label": "Show Rating Breakdown",
      "default": true
    },
    {
      "type": "select",
      "id": "reviews_per_page",
      "label": "Reviews Per Page",
      "options": [
        {
          "value": "3",
          "label": "3"
        },
        {
          "value": "5",
          "label": "5"
        },
        {
          "value": "10",
          "label": "10"
        }
      ],
      "default": "3"
    }
  ],
  "presets": [
    {
      "name": "Product Reviews",
      "category": "Product"
    }
  ]
}
{% endschema %}
```

---

## 5. Code Deep-Dive & Key Mechanics

### Dynamic Rating Summary & Calculations
The section aggregates all linked metaobjects in Liquid:
1. `reviews_references` accesses the metaobject references list: `product.metafields.custom.da_stuff.value`.
2. Liquid loops through the array, tallying `total_stars` and maintaining counts for `five_star_count` down to `one_star_count`.
3. `average_rating` is computed via `total_stars | divided_by: total_reviews.size | round: 1`.

### Half-Star SVG Gradient Fill
Rather than importing heavy external icon libraries (FontAwesome, Lucide), the section renders SVG star shapes and handles partial ratings with an inline SVG `linearGradient`:

```html
<svg class="star" viewBox="0 0 24 24">
  <defs>
    <linearGradient id="half-fill-{{ section.id }}" x1="0" x2="100%" y1="0" y2="0">
      <stop offset="50%" stop-color="#fbbf24" />
      <stop offset="50%" stop-color="#e5e7eb" />
    </linearGradient>
  </defs>
  <path fill="url(#half-fill-{{ section.id }})" d="..."/>
</svg>
```
This shades 50% gold (`#fbbf24`) and 50% neutral grey (`#e5e7eb`).

### Progress Bar Percentages
For each star tier (1 through 5), the bar width is calculated on the server and applied directly as CSS inline widths:
```liquid
{% assign five_star_percent = five_star_count | times: 100 | divided_by: total_reviews.size %}
<div class="progress-fill" style="width: {{ five_star_percent }}%"></div>
```

### Initials Fallback for Avatars
If a customer image is not provided (`customer_image == blank`), Liquid splits the customer's full name and renders their initials:
```liquid
{% assign name_parts = review.customer_name | split: ' ' %}
{{ name_parts[0] | slice: 0, 1 | upcase }}
{% if name_parts.size > 1 %}
  {{ name_parts.last | slice: 0, 1 | upcase }}
{% endif %}
```
*Example:* "John Smith" renders `JS`.

### Client-Side Pagination (Load More / Show Less)
The section renders all reviews in the DOM, but hides items beyond `reviews_per_page` with `display: none` and class `.hidden-review`. Vanilla JavaScript progressively unhides batches when the user clicks **Load More Reviews**, and resets the list when clicking **Show Less Reviews**.

---

## 6. Theme Customizer Setup & Product Template Placement

1. Go to **Online Store** > **Themes** in Shopify Admin.
2. Click **Customize** on your active theme.
3. In the top template selector dropdown, select **Products** > **Default product**.
4. In the left-hand sidebar, click **Add section**.
5. Locate and select **Product Reviews**.
6. Drag the section into your preferred position (typically below the Product Information / Description block and above Related Products).
7. Configure Section Settings in the right sidebar:
   - **Section Title**: Customize the heading or leave blank to automatically append product name.
   - **Show Rating Breakdown**: Toggle progress bars on/off.
   - **Reviews Per Page**: Choose between `3`, `5`, or `10`.
8. Click **Save**.

---

## 7. Enhancements & Production Considerations

### 1. Fixing Metafield Key Nismatch
The original tutorial code uses the arbitrary metafield handle `custom.da_stuff`:
```liquid
{% assign reviews_references = product.metafields.custom.da_stuff.value %}
```
For clean production code, rename your metafield definition to `custom.product_reviews` and update line 1:
```liquid
{% assign reviews_references = product.metafields.custom.product_reviews.value %}
```

### 2. Float Division & Star Accuracy
Liquid performs integer division by default (e.g., `9 / 2 = 4`, not `4.5`). To guarantee accurate decimal averages, append `.0` to float conversions:
```liquid
{% assign average_rating = total_stars | times: 1.0 | divided_by: total_reviews.size | round: 1 %}
```

### 3. SEO Schema (AggregateRating & Review JSON-LD)
To get Google Star rich snippets on search engine result pages (SERPs), add JSON-LD structured data inside the section:

```liquid
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": {{ product.title | json }},
  "image": {{ product.featured_image | image_url: width: 800 | json }},
  "description": {{ product.description | strip_html | truncate: 160 | json }},
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "{{ average_rating }}",
    "reviewCount": "{{ total_reviews.size }}"
  }
}
</script>
```

### 4. Zero-Review State Handling
If a product has no reviews, the section currently hides itself (`{% if total_reviews.size > 0 %}`). If you want to show a polite empty state with an invitation to review, replace the conditional wrapper with:
```liquid
{% if total_reviews.size > 0 %}
  <!-- Reviews UI -->
{% else %}
  <div class="product-reviews-section empty-state">
    <h3>No reviews yet</h3>
    <p>Be the first to review {{ product.title }}!</p>
  </div>
{% endif %}
```

---

## 8. App vs. Custom Metaobject Comparison

| Feature | Third-Party App (Loox/Judge.me) | Custom Metaobject Section |
| :--- | :--- | :--- |
| **Monthly Cost** | $15 – $100+/mo | **$0 / Free Forever** |
| **Page Speed Impact** | 100KB – 400KB external JS | **0KB extra network overhead** |
| **Theme Styling** | Uses 3rd-party widget styling / iframes | **Matches theme CSS natively** |
| **Data Ownership** | Locked in vendor database | **100% inside Shopify Metaobjects** |
| **Review Moderation** | App dashboard | **Shopify Admin (`Content > Metaobjects`)** |
| **Automated Email Request Flows** | Built-in email flows | Requires Shopify Flow / Klaviyo integration |
