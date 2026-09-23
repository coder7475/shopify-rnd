# R&D: Facebook Shops Setup & Page Visibility

> **Source Video:** [Getting Facebook Shops Seen On Facebook Pages (YouTube)](https://www.youtube.com/watch?v=bo5ivXjEoek&t=132s)  
> **Key Focus:** Making your Facebook Shop visible to visitors, configuring call-to-action buttons, managing page tabs/sections in Classic vs. New Pages Experience, and connecting Commerce Manager.

---

## 1. Executive Summary

Having a fully configured Facebook Shop is useless if page visitors cannot easily find it. By default, Facebook Pages feature generic call-to-action (CTA) buttons (such as "Follow", "Like", or "Send Message"). To drive traffic and direct conversions, merchants must deliberately expose their shop by:
1. Configuring the primary CTA action button as **"View Shop"**.
2. Adding and prioritizing the **"Shop" tab or pinned section** directly on the Facebook Page navigation.
3. Ensuring correct association in **Meta Commerce Manager / Business Manager** between the catalog/shop and the Facebook Page.

---

## 2. Core Architectures & Interface Models

Facebook maintains two page architectures with differing customization mechanisms:
- **Classic Pages Layout** (Settings > Templates and Tabs).
- **New Pages Experience (NPE)** (Profile switching, Manage Sections, Action Buttons, and Section Pinning).

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

## 3. Step-by-Step Configuration Guide

### Approach A: Classic Pages Interface

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
   - This allows users to browse your catalog directly within your Page without clicking out of the experience.

---

### Approach B: New Pages Experience (NPE)

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
   - Once pinned, any visitor viewing your profile will see your featured products and shop collection immediately below your bio/details.

---

## 4. Key Troubleshooting & Failure Modes

| Issue / Symptom | Root Cause | Resolution |
| :--- | :--- | :--- |
| **"View Shop" button option missing** | Shop setup is either incomplete or pending review in Meta Commerce Manager. | Open Meta Commerce Manager, complete catalog onboarding, legal details, and wait for Meta review approval. |
| **Test button redirects to wrong shop** | Multiple pages or incorrect page linked during Commerce Manager onboarding. | Go to **Meta Business Suite / Commerce Manager > Settings > Business Assets** and verify the active Page linked to the catalog. |
| **Shop tab/section grayed out in NPE** | Facebook enforces shop visibility defaults for active commerce-enabled pages. | Ensure your page category is set to e-commerce/retail and verify Commerce Manager status. |
| **Visitors see classic profile while admin sees NPE** | Phased rollouts and caching across regional Facebook CDNs. | Test in an Incognito / Private window logged out or using a non-admin account. |

---

## 5. Best Practices & Optimization Checklist

- [ ] **Verify Page linkage in Meta Business Suite:** Ensure the business page is explicitly mapped to the active Commerce Manager account.
- [ ] **Audit customer perspective:** Regularly switch out of admin mode or use a secondary account to test the customer journey.
- [ ] **Coordinate with Shopify sync:** If using Shopify, ensure products are approved in Shopify's Facebook & Instagram sales channel before attempting to showcase them on the page.
- [ ] **Keep CTA aligned with promotions:** If running a major product campaign, keep the CTA pinned to "View Shop" rather than "Send Message".
