# Shopify Inbox — RND

> **App / Channel:** [Shopify Inbox](https://apps.shopify.com/inbox)
> **Cost:** Free (native first-party tool included with all Shopify plans)
> **Access:** Shopify Admin → Sales channels → Inbox
> **Mobile Apps:** Available on iOS and Android for on-the-go merchant responses

---

## Overview

**Shopify Inbox** is Shopify's native real-time customer messaging application and sales channel. Rather than operating purely as a post-purchase support helpdesk, Shopify Inbox is architected as an **in-session sales enablement tool**. It connects merchants with live storefront visitors, provides live shopping cart visibility, enables direct in-chat product and discount sharing, and features an **AI Inbox Agent** (powered by Shopify Magic) that autonomously answers customer inquiries 24/7.

> [!NOTE]
> According to Shopify platform data, over **70% of Shopify Inbox conversations occur while a customer is actively considering a purchase**.

---

## Why It Matters

| Capability / Metric | Grounded Value |
|---|---|
| **High Pre-Purchase Intent** | 70%+ of chats are pre-checkout inquiries (sizing, fit, shipping speed, material). Fast answers prevent site abandonment. |
| **Real-Time Cart Context** | Agents see items currently in the customer's cart, items added/removed, and past order history without asking. |
| **Autonomous AI Inbox Agent** | Resolves routine policy, product, and shipping questions 24/7 without requiring human staffing. |
| **Direct Commerce in Chat** | Send product cards, links, and discount codes directly into the conversation stream. |
| **Multi-Surface Reach** | Unifies messages originating from your **Online Store chat widget** and the **Shop app**. |

---

## Core Features & Mechanics

### 1. 🤖 The AI Inbox Agent

The **Inbox Agent** is an opt-in generative AI assistant built natively into Shopify Inbox (powered by Shopify Magic). It automatically detects and resolves customer inquiries in real time.

**Knowledge Sources:**
The Inbox Agent autonomously trains on:
- Product titles, descriptions, options, pricing, and availability.
- Store policies (Shipping, Refund/Return, Privacy, Terms of Service).
- Custom FAQs and information configured in your **Knowledge Base**.

**What the AI Inbox Agent Handles:**
- **Product specifications & sizing:** "Does this jacket run true to size?", "Is this mug dishwasher safe?"
- **Shipping & delivery inquiries:** "How long does standard delivery take to California?", "Do you offer free shipping?"
- **Returns & refunds:** "What is your return window?", "Can I exchange an item?"
- **Personalized suggestions:** When shoppers are logged in via the **Shop app**, the agent leverages purchase history and preferences for contextual product recommendations.

**Agent Training & Configuration:**
- **Navigation:** Accessible in **Sales channels → Inbox → Training**.
- **Response Rating:** Merchants can test the agent in simulated scenarios, review recent conversations, and rate answers (Thumbs Up / Thumbs Down) to fine-tune future responses.
- **Tone Adjustment:** Configure the persona and greeting style to align with your brand voice.

---

### 2. ⚡ Instant Answers & "Track My Order"

Instant Answers are predefined question-and-answer pairs displayed in the storefront chat widget.

**How Instant Answers Interact with the Inbox Agent:**
- **When the Inbox Agent is INACTIVE:** The chat widget displays your custom **Instant Answers** as clickable buttons (e.g., "What is your return policy?"). Clicking a button instantly outputs the preset answer.
- **When the Inbox Agent is ACTIVE:** The AI Inbox Agent takes over the primary greeting and conversation flow, dynamically fielding customer questions.
- **"Track My Order" Persistence:** The native **"Track my order"** self-service lookup remains available to customers **regardless of whether the Inbox Agent is active or inactive**. Customers can input their order number and email to receive real-time fulfillment tracking updates.

**Steps to Configure Instant Answers:**
1. Navigate to **Sales channels → Inbox → Chat settings**.
2. Scroll to the **Instant answers** section.
3. Click **Create instant answer** or select from AI-suggested policy prompts.
4. Input the question prompt and corresponding answer text.
5. Toggle visibility on/off, or drag-and-drop to reorder.
6. Click **Save**.

---

### 3. 🛒 Live Cart & Customer Activity Visibility

During active chat sessions, the Inbox dashboard displays contextual customer data alongside the chat thread:

**Context Displayed to Agents:**
- **Current Cart Contents:** Real-time view of product titles, quantities, variant selections, and total cart value.
- **Cart Actions:** Real-time event log showing items added or removed during the browsing session.
- **Customer Profile:** Customer name, email, location, lifetime order count, and total lifetime spend (if recognized or signed into Shop).
- **Browsing Location:** The specific product page or collection page the customer is viewing when initiating the chat.

**Merchant Tactical Use Cases:**
- *Hesitating High-Value Cart:* If a customer with a $200+ cart asks about shipping, the agent can proactively offer free shipping or an incentive code.
- *Variant Clarification:* When a shopper asks "Does the medium fit baggy?", the agent immediately confirms they are looking at the specific medium SKU in their cart.

---

### 4. 🏷️ Sales Acceleration: In-Chat Discounts & Product Cards

Merchants and support staff can convert conversations into checkouts directly within the chat interface:

- **Send Product Cards:** Use the in-chat product search tool to pull items directly from your catalog. Sending a product renders an interactive card showing the product image, title, price, and a direct link to the product detail page.
- **Send Active Discount Codes:** Agents can select active discount codes created in **Discounts** (or generate specific chat promo codes like `VIPCHAT10`) and share them directly in the chat.
- **Quick Replies (Saved Responses):** Create standard reusable text snippets for frequently repeated manual messages (e.g., store hours, warranty registration steps).

---

### 5. 👥 Team Collaboration, Staff Permissions & Routing

For stores with multiple team members, Inbox provides team management controls:

- **Conversation Assignment:** Assign specific chats to individual staff members or reassign between team members.
- **Availability & Operating Hours:** Set explicit business hours. Outside of operating hours, the widget displays an automated "Away message" and manages customer expectations regarding response time.
- **Role-Based Access:** Team members can be given restricted staff permissions in **Settings → Users and permissions** (e.g., customer service roles that can access Inbox and view products without having permission to edit store settings or products).
- **Mobile Push Notifications:** Staff can receive push notifications on iOS and Android devices via the dedicated **Shopify Inbox app**, ensuring rapid response times.

---

### 6. 🎨 Storefront Widget Customization

Customize the chat interface to match the store's visual identity:
- **Button style & position:** Choose bottom-right or bottom-left placement; select icon style (chat bubble, speech icon, or text label).
- **Branding:** Set custom header colors, button colors, and greeting text.
- **First reply format:** Choose automated greetings or set expectation messages for when staff are offline.

---

## Performance & Conversation Analytics

Shopify Inbox includes native reporting in the Inbox dashboard:

**Key Metrics Tracked:**
- **Total Conversations:** Number of incoming chats across Online Store and Shop app.
- **Conversations Handled by AI vs. Staff:** Percentage of chats resolved autonomously by the Inbox Agent without escalation.
- **Average First Response Time:** Speed of merchant replies.
- **Sales Attributed to Chat:** Total revenue and orders placed within 30 days of a customer engaging in an Inbox chat session.

**Operational Action Framework:**

| Metric Signal | Diagnosis | Action |
|---|---|---|
| High volume of repetitive product questions | Information missing on PDP | Update product descriptions and add details to the AI Knowledge Base. |
| Low AI resolution rate / High escalation | Knowledge gaps in policies | Add explicit answers into store policies and train the Inbox Agent. |
| High pre-purchase chats, low conversion | Pricing or shipping objection | Test chat-exclusive discount codes or adjust shipping thresholds. |
| Delayed first response during business hours | Staff notification failure | Install Shopify Inbox mobile app; configure desktop audio/push alerts. |

---

## Limitations & When to Consider Alternatives

| Area | Native Shopify Inbox | Third-Party Helpdesks (e.g., Gorgias, Zendesk) |
|---|---|---|
| **Core Focus** | Pre-purchase sales, live storefront chat, Shop app chat | Full-scale post-purchase customer support & ticketing |
| **Email Ticketing** | ❌ No native email ticketing or thread management | ✅ Omnichannel email, ticket queues, SLA tracking |
| **Social DM Integration** | ⚠️ Focused on Web Storefront + Shop app | ✅ Connects Instagram DMs, Facebook Messenger, WhatsApp, email |
| **Order Actions in Chat** | View-only; track my order automated | Direct order cancellations, refunds, and address edits inside the ticket |
| **Cost** | **100% Free** on all Shopify plans | $50 – $750+/month depending on ticket volume |

---

## Official References

- [Shopify Help: Shopify Inbox Overview](https://help.shopify.com/en/manual/inbox)
- [Shopify Help: Setting Up the AI Inbox Agent](https://help.shopify.com/en/manual/inbox/inbox-agent)
- [Shopify Help: Configuring Instant Answers & Chat Settings](https://help.shopify.com/en/manual/inbox/chat-settings/instant-answers)
- [Shopify Help: Managing Conversations and Permissions](https://help.shopify.com/en/manual/inbox/manage-conversations)
- [App Store: Shopify Inbox](https://apps.shopify.com/inbox)
