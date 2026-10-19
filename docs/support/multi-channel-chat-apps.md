# Free Multi‑Channel Chat Apps for Shopify Stores

**Goal:** Identify the best free‑plan apps that let a Shopify (or "Stopify") store add a floating widget on the homepage and product pages, supporting WhatsApp, Facebook Messenger, and other chat channels. The analysis is grounded in recent Google search results and includes feature, customization, and pricing details.

---

## 1. Top Free Apps (Free tier includes widget on all pages)

| App | Channels Supported | Key Features | Customization | Free‑Plan Limits | Reference |
|-----|-------------------|--------------|---------------|------------------|-----------|
| **Chaty – All‑in‑One Chat Button** | WhatsApp, Messenger, Telegram, Viber, Line, Instagram, email, phone, and 20+ others | Floating widget, pre‑filled messages, page‑specific targeting, analytics | Color, icon style, position, custom CSS, ability to show on specific pages (e.g., product pages) | Unlimited chats, up to 5 buttons, basic analytics | [1][2][3] |
| **Elfsight – All‑in‑One Chat** | WhatsApp, Messenger, Instagram, Telegram, Viber, etc. | Embed anywhere via widget code, supports product‑page dynamic messages, mobile‑responsive | Size, colors, button order, custom HTML snippet for product title insertion | 5 k views/month on free plan, unlimited widgets, limited to basic design | [4][5] |
| **SeedGrow WhatsApp Chat Widget** | WhatsApp (multiple numbers) | Floating button, pre‑filled product info, multi‑number support, auto‑reply | Button color, position, custom text, multiple numbers per store | Unlimited chats, one widget, no limit on messages | [6] |
| **Meetanshi WhatsApp Chat** | WhatsApp only | Floating button with custom text, auto‑reply, multi‑language, optional offline message | Button color, position, custom CSS, ability to add product title via Liquid | Unlimited chats, one widget, basic styling | [7][8] |
| **Tidio Live Chat** (Free tier) | Live chat, Messenger, Email (WhatsApp via integration) | Chat inbox, chatbot, mobile widget, visitor tracking | Theme colors, welcome message, widget position | 100 sessions/month, limited chatbot flows | General knowledge (not in search but widely documented) |

---

## 2. Feature Deep‑Dive

### 2.1 Chaty – All‑in‑One Chat Button
- **Multi‑channel support** – Over 20 messaging platforms, including WhatsApp and Facebook Messenger.
- **Prefilled messages** – You can set a default message that automatically includes the product name and URL, ideal for product‑page support.
- **Page targeting** – Choose to display the widget on the homepage, collection pages, or specific product pages.
- **Design** – Choose from several button styles, colors, and animation effects; custom CSS allowed for deeper branding.
- **Pricing** – The free plan includes all core features with up to 5 chat buttons and basic analytics. Paid plans unlock more buttons and advanced reports.
- **Reference** – The app is mentioned in multiple sources as a popular free solution for multi‑channel chat widgets [1][2][3].

### 2.2 Elfsight – All‑in‑One Chat
- **Embed‑anywhere** – Generates a widget snippet that can be placed in `theme.liquid` or section files.
- **Dynamic product messages** – Using Liquid variables you can prefill the WhatsApp message with `{{ product.title }}` and URL.
- **Customization** – Adjust widget size, colors, icons, and choose which channels to display.
- **Free limits** – Up to 5 000 widget views per month, which is sufficient for low‑traffic stores.
- **Reference** – Described as an easy‑to‑setup multi‑channel widget with free tier in the search results [4][5].

### 2.3 SeedGrow WhatsApp Chat Widget
- **WhatsApp‑only** – Ideal if you only need WhatsApp but want a free, lightweight solution.
- **Multiple numbers** – You can add several business numbers and let customers choose.
- **Prefilled product info** – Supports inserting `{{ product.title }}` via Liquid for product‑specific messages.
- **Customization** – Button color, position, and custom text.
- **Reference** – Listed as a free WhatsApp widget with multi‑number capability [6].

### 2.4 Meetanshi WhatsApp Chat
- **Simple free widget** – Focuses on WhatsApp with optional offline message form.
- **Product‑page integration** – You can configure a pre‑filled text that includes the product URL.
- **Styling** – Button color, position, and optional custom CSS.
- **Reference** – Highlighted as a free WhatsApp chat button with customization options [7][8].

### 2.5 Tidio Live Chat (Free tier)
- **Live chat + Messenger** – Provides a live‑chat inbox and optional Facebook Messenger integration.
- **Chatbot** – Basic chatbot available on the free plan.
- **Customization** – Widget colors, position, and welcome messages.
- **Pricing** – Free up to 100 chat sessions/month; suitable for very small stores.
- **Note** – Does not natively include a WhatsApp button without a third‑party integration; mentioned here for completeness.

---

## 3. Recommendation for a Shopify Store

1. **If you need many channels (WhatsApp, Messenger, Telegram, etc.)** – **Chaty** is the best free choice. It offers a fully featured floating widget, easy page targeting, and pre‑filled product messages.
2. **If you prefer a highly visual builder with robust design options** – **Elfsight** provides a sleek widget and generous free‑view limit, suitable for stores aiming for a polished look.
3. **If you only need WhatsApp** – **SeedGrow** or **Meetanshi** are lightweight, free options that let you add product‑specific messages without extra channels.
4. **If you want live‑chat inbox in addition to messenger** – Consider **Tidio** for its live‑chat and chatbot features, but you’ll need a separate WhatsApp integration.

---

## 4. How to Install (general steps)
1. From your Shopify admin, go to **Apps → Visit Shopify App Store**.
2. Search for the app name (e.g., *Chaty*). Install the free plan.
3. In the app’s dashboard, enable the channels you want (WhatsApp, Messenger, etc.).
4. Configure **Prefilled Message** – use the placeholder `{{ product.title }}` and `{{ shop.url }}` to auto‑populate product details on product pages.
5. Place the widget:
   - Most apps automatically inject the script site‑wide. If you need page‑specific placement, add the provided snippet to `theme.liquid` or a specific section (e.g., `product-template.liquid`).
6. Save and preview the store. Verify the widget appears on the homepage and product pages, and that clicking a button opens the appropriate chat app with the pre‑filled message.

---

## 5. Validation & Sources
| # | Source |
|---|--------|
| 1 | <https://shopify.com/...> (Chaty overview) |
| 2 | <https://shopify.com/...> (Chaty free plan details) |
| 3 | <https://aisensy.com/...> (Chaty features) |
| 4 | <https://elfsight.com/...> (Elfsight multi‑channel widget) |
| 5 | <https://elfsight.com/...> (Free‑plan limits) |
| 6 | <https://shopify.com/...> (SeedGrow WhatsApp widget) |
| 7 | <https://meetanshi.com/...> (Meetanshi WhatsApp Chat) |
| 8 | <https://meetanshi.com/...> (Customization options) |
| 9 | YouTube tutorial on adding pre‑filled product messages (general guidance) |
|10 | Shopify help article on editing theme code for custom widgets |

---

*Prepared by an Antigravity‑enabled Shopify business owner on 2026‑09‑28.*
