# R&D: Facebook Shops Setup & Page Visibility

> **Source Video:** [Getting Facebook Shops Seen On Facebook Pages (YouTube)](https://www.youtube.com/watch?v=bo5ivXjEoek&t=132s)
> **Key Focus:** Making your Facebook Shop visible to visitors, configuring call-to-action buttons, managing page tabs/sections in the New Pages Experience, and connecting Commerce Manager.
> **Related Reference:** For full Meta Ads, Advantage+, and Meta Business Suite operations, see [meta-ads-research.md](./meta-ads-research.md).
>
> **Last Updated:** October 2026

---

## References

| # | Source | URL | Notes |
|---|--------|-----|-------|
| 1 | Getting Facebook Shops Seen On Facebook Pages | https://www.youtube.com/watch?v=bo5ivXjEoek&t=132s | Primary source video |
| 2 | Meta Commerce Manager Documentation | https://www.facebook.com/business/help/1648788025308551 | Official catalog & shop setup |
| 3 | Meta for Developers – Commerce Platform | https://developers.facebook.com/docs/commerce-platform | API auth & token reference |
| 4 | Facebook Login for Business | https://developers.facebook.com/docs/facebook-login/business | OAuth 2.0 integration guide |
| 5 | Meta Business Suite – Security Center | https://business.facebook.com/security | 2FA & business verification |
| 6 | Meta New Pages Experience Help | https://www.facebook.com/help/323314944908922 | Page interface guide |
| 7 | Meta Commerce Eligibility Requirements | https://www.facebook.com/policies/commerce/requirements | Mandatory compliance policy |

---

## 1. Executive Summary

Having a fully configured Facebook Shop requires two distinct layers:
1. **Authentication & Authorization Foundation (Meta Business / Commerce Platform):**
   - Establishing identity and administrative rights via **Meta Business Portfolio (Business Manager)** with **2FA**, **Business Verification**, and **Full Control** access permissions.
   - For automated/custom sync or app integrations, using **Facebook Login for Business** (OAuth 2.0 flow) or **System User Access Tokens** assigned with necessary scopes (`catalog_management`, `business_management`).
   - Maintaining **Domain Verification** and complying with Meta's Commerce Eligibility Requirements (including the requirement for supported checkout models and authentic presence).
2. **Customer-Facing Page Visibility & Discovery:**
   - Exposing the shop to page visitors by configuring the primary CTA action button as **"View Shop"**.
   - Prioritizing the **"Shop" tab or pinned section** directly on the Facebook Page navigation.
   - Ensuring proper linkage in **Meta Commerce Manager** between the catalog, sales channel, and the Facebook Page.

---

## 2. Core Architectures & Interface Models

> [!IMPORTANT]
> As of **2025**, the Classic Pages layout is largely deprecated. The **New Pages Experience (NPE)** is now the standard for all business Pages. The Classic Pages interface may still be visible in some markets, but Meta has removed support for many Classic Pages features.

```
+-------------------------------------------------------------------+
|                        Facebook Page                              |
|                                                                   |
|   [ Banner Image / Logo ]                                         |
|                                                                   |
|   [Primary Action CTA: "View Shop"] ---> Opens Meta Commerce Shop |
|                                                                   |
|   Navigation Tabs / Pinned Section:                               |
|   [ Shop (Pinned/Top Priority) ] [ Posts ] [ About ] [ Photos ]  |
+-------------------------------------------------------------------+
                                  |
               Synced via Meta Commerce Manager Catalog
```

---

## 3. Meta Authentication, Authorization & Security Architecture

According to official **[Meta for Developers Commerce Platform](https://developers.facebook.com/docs/commerce-platform)** and **Meta Business Suite** guidelines, authenticating and securing a Meta Shop requires complying with specific identity and token models:

```
+-----------------------------------------------------------------------------+
|                           Meta Business Portfolio                           |
|                      (Security Center & Access Control)                     |
+--------------------------------------+--------------------------------------+
                                       |
          +----------------------------+----------------------------+
          |                                                         |
          v                                                         v
+------------------------------------+   +------------------------------------+
|  Business Admin Authentication     |   |   API & Integration Authentication |
+------------------------------------+   +------------------------------------+
| - Mandatory Two-Factor Auth (2FA)  |   | - Facebook Login for Business      |
| - Legal Business Verification      |   |   (OAuth 2.0 flow for 3rd parties) |
| - "Full Control" Access Assignment |   | - System User Access Tokens        |
| - Primary Domain Verification      |   |   (Permanent server-to-server sync)|
+------------------------------------+   +------------------------------------+
                  \                                 /
                   \                               /
                    v                             v
+-----------------------------------------------------------------------------+
|                            Commerce Manager                                 |
|          (Catalog Management, Product Eligibility, Checkout Settings)       |
+-----------------------------------------------------------------------------+
```

### A. Business Suite & Administrative Authentication
1. **Mandatory Two-Factor Authentication (2FA):**
   - All administrators and members handling the Meta Business Portfolio must have 2FA enforced. Accounts failing 2FA are barred from modifying commerce assets or payouts.
2. **Business Verification (Security Center):**
   - In Meta Business Suite > **Security Center**, verify official legal entity credentials (Certificate of Incorporation, Tax ID, Utility Bill).
   - Verification unlocks higher API rate limits, product tagging legitimacy, and resolves account restrictions.
3. **Role-Based Access Control (RBAC):**
   - Managing commerce requires **Full Control** over the Business Portfolio and assigned administrator permissions on both the linked Facebook Page and the Catalog.
   - As of 2026, the New Pages Experience uses **Task Access** or **Full Control** — the old Editor/Moderator roles have been replaced.
4. **Domain Verification:**
   - Verify ownership of the store domain via DNS TXT record or HTML meta tag in Business Settings > Brand Safety > Domains.
5. **Privacy Policy Update (July 2026):**
   - Meta consolidated privacy controls in July 2026. The "Your activity off Meta technologies" opt-out has been restructured, affecting how off-platform data (website conversions) is used for ad personalization and retargeting. Ensure your Shopify pixel events are configured accordingly.

### B. Developer & API Authentication (Commerce Platform)
For direct API access (custom catalog feeds, inventory synchronization, order management):
1. **Facebook Login for Business:**
   - The recommended standard for apps/platforms connecting to client shops.
   - Uses OAuth 2.0 authorization code flow where merchants grant scoped access via Meta's permission dialog.
2. **System Users & System User Access Tokens:**
   - For backend/automated server-to-server scripts (e.g. ERP or Shopify automated sync).
   - Created in **Meta Business Settings > Users > System Users**.
   - Admin System Users generate long-lived/non-expiring access tokens tied directly to the business.
3. **Required Permission Scopes:**
   - `catalog_management`: Manage product items, feeds, collections, and catalog batch updates.
   - `business_management`: Read and manage business assets and permissions.
   - `pages_read_engagement` / `pages_manage_metadata`: Configure page buttons, tabs, and action CTA buttons.
4. **Commerce Eligibility & Checkout Compliance:**
   - As of late 2025, Meta completed the transition to **mandatory website checkout** for all shops. Customers discover products within Facebook/Instagram but are redirected to your external website (e.g., Shopify) to complete purchases. Ensure you have a valid `checkout_url` configured in Commerce Manager shop settings.
   - Post-purchase activities (returns, refunds, order updates) must now be handled directly on your Shopify website, not within Commerce Manager.

---

## 4. Step-by-Step Configuration Guide

> [!NOTE]
> As of 2026, the **New Pages Experience (NPE)** is the standard. Classic Pages instructions are included for legacy reference only.

### Approach A: Classic Pages Interface *(Legacy – may no longer be available in your market)*

1. **Change the Main Action Button to "View Shop":**
   - Navigate to your Facebook Page in admin view.
   - Hover over or click the primary CTA button (often defaulted to "Follow" or "Send Message").
   - Click **"Edit Button"** (or go to Page Settings > Templates and Tabs).
   - Select **"View Shop"** as the primary action.
   - *Verification:* Click the button and select **"Test Button"** or switch to your personal profile view to confirm the shop opens.

2. **Enable and Reorder the "Shop" Tab in Page Navigation:**
   - On the left sidebar menu, go to **Settings** > **Templates and Tabs**.
   - Under the **Tabs** section, locate **Shop** and ensure the toggle is set to **ON**.
   - Click and drag the **Shop** tab to the very top (just below "Home").

---

### Approach B: New Pages Experience (NPE) *(Current Standard — 2026)*

Under the New Pages Experience, Facebook treats Pages similarly to independent user profiles.

1. **Switch to Page Profile Mode:**
   - Click your profile icon in the top-right corner.
   - Click **"Switch profile"** and select the Facebook Page you want to manage.

2. **Configure the Action Button:**
   - Click the **three dots (`...`)** located next to the "Manage" button.
   - Select **"Edit Action Button"**.
   - Choose **"View Shop"** (or edit existing action button).
   - If the option is not available, ensure your Commerce Manager catalog and shop approval have completed.

3. **Pin the Shop Section to the Top of the Profile:**
   - Scroll down to the Page sections.
   - Click the **three dots (`...`)** on the page options.
   - Select **"Edit Pin to section"** / **"Manage Sections"**.
   - Select the **Shop** section and toggle **Pin to top**.

4. **Configure Mandatory Website Checkout URL:**
   - In Meta Commerce Manager > **Shop Settings** > **Checkout**, ensure the website checkout destination URL is set to your Shopify store.
   - This is now required for all shops (in-app checkout is no longer available for most businesses globally).

---

## 5. 2026 Platform Updates

| Update | Details |
| :--- | :--- |
| **Mandatory Website Checkout** | Completed late 2025 — all shops must route purchases to an external website. In-app checkout is no longer available for most businesses. |
| **Muse AI Shopping Agent** | Launched September 8, 2026 — Meta's autonomous AI agent can browse, compare products, and complete purchases for users via one-time virtual card numbers. Supports Shop Pay. Integrated with select major retailers. |
| **AI Mode in Facebook Search** | AI-powered personalized product recommendations in Facebook search results, bridging discovery and shopping. |
| **New Pages Experience as Standard** | Classic Pages legacy interface deprecated in most markets; NPE with Task Access model is now universal. |
| **AI-Enhanced Commerce Manager Catalogs** | Automatic product image enhancement and automated description updates to match website content. |
| **Meta Privacy Control Consolidation (July 2026)** | Restructured off-platform activity controls impacting ad personalization and retargeting signals. |

---

## 6. Key Troubleshooting & Failure Modes

| Issue / Symptom | Root Cause | Resolution |
| :--- | :--- | :--- |
| **"View Shop" button option missing** | Shop setup is either incomplete or pending review in Meta Commerce Manager. | Open Meta Commerce Manager, complete catalog onboarding, legal details, and wait for Meta review approval. |
| **Test button redirects to wrong shop** | Multiple pages or incorrect page linked during Commerce Manager onboarding. | Go to **Meta Business Suite / Commerce Manager > Settings > Business Assets** and verify the active Page linked to the catalog. |
| **Shop tab/section grayed out in NPE** | Facebook enforces shop visibility defaults for active commerce-enabled pages. | Ensure your page category is set to e-commerce/retail and verify Commerce Manager status. |
| **Visitors see classic profile while admin sees NPE** | Phased rollouts and caching across regional Facebook CDNs. | Test in an Incognito / Private window logged out or using a non-admin account. |
| **Checkout redirecting incorrectly** | Checkout URL not configured in Commerce Manager after the 2025 in-app checkout transition. | In Commerce Manager > Shop Settings > Checkout, set your Shopify store URL as the checkout destination. |

---

## 7. Best Practices & Optimization Checklist

- [ ] **Enforce 2FA on Business Portfolio:** Ensure all admins and members have two-factor authentication enabled.
- [ ] **Complete Meta Business Verification:** Submit legal documentation in Meta Business Suite > Security Center.
- [ ] **Verify Primary Domain:** Verify the root e-commerce domain via DNS/meta-tag in Brand Safety & Suitability.
- [ ] **Assign Full Control RBAC / Task Access (NPE):** Confirm the operating account has full control over the Business Portfolio, Facebook Page, and Catalog.
- [ ] **Use System Users for Automated API Integration:** Configure Admin System Users and generate dedicated tokens.
- [ ] **Configure Valid Website Checkout URL:** Set your Shopify store URL as the checkout destination in Commerce Manager (mandatory post-2025 transition).
- [ ] **Verify Page linkage in Meta Business Suite:** Ensure the business page is explicitly mapped to the active Commerce Manager account.
- [ ] **Audit customer perspective:** Regularly switch out of admin mode or use a secondary account to test the customer journey.
- [ ] **Coordinate with Shopify sync:** Ensure products are approved in Shopify's Facebook & Instagram sales channel before showcasing on the page.
- [ ] **Keep CTA aligned with promotions:** Keep the CTA pinned to "View Shop" during active campaigns.
- [ ] **Review Privacy Control Impact (July 2026):** Audit your pixel and CAPI data pipelines after Meta's July 2026 privacy control restructuring.
