# Professional Sender Email & Domain Authentication Guide: Naza Noor

A complete, step-by-step administrator guide for configuring a professional branded
email address (e.g., `info@nazanoor.com` or `support@nazanoor.com`) in Shopify,
authenticating domain records (DKIM) in GoDaddy, and ensuring 100% email inbox delivery.

---

## Quick Reference Summary

| Property | Value |
| :--- | :--- |
| **Domain** | `nazanoor.com` |
| **DNS Provider** | GoDaddy (Nameservers: `ns59.domaincontrol.com`, `ns60.domaincontrol.com`) |
| **Email Inbox Host** | GoDaddy Professional Email / SecureServer (`mailstore1.secureserver.net`) |
| **Shopify Sender Email** | e.g., `info@nazanoor.com` or `support@nazanoor.com` |
| **Authentication Standard** | 4 CNAME Records (DKIM + Return-Path) + DMARC TXT Record |
| **Current Live DMARC** | `v=DMARC1; p=quarantine; adkim=r; aspf=r; rua=mailto:dmarc_rua@onsecureserver.net;` (Active) |

---

## Why Professional Email Authentication Matters

Major email providers (Google/Gmail, Yahoo, Apple Mail, and Microsoft Outlook) enforce
strict sender authentication standards. If your store sends order confirmations, shipping
updates, or marketing emails from a custom domain without proper authentication:

1. **Emails Land in Spam or Get Blocked:** Without DKIM, Gmail and Yahoo will reject or
   send your store emails directly to junk folders.
2. **"Via Shopify" Warning:** Unauthenticated emails show as
   `nazanoor.com via shopifyemail.com`, confusing customers and reducing trust.
3. **Phishing & Spoofing Protection:** DMARC ensures malicious actors cannot send
   fraudulent emails pretending to be Naza Noor.

---

## Choosing Your Inbound Strategy: Email Forwarding vs. Dedicated Business Inbox

The video tutorial explains the two options available to receive and handle customer inquiries:

```
                      CUSTOMER SENDS EMAIL TO info@nazanoor.com
                                       │
                ┌──────────────────────┴──────────────────────┐
                ▼                                             ▼
       OPTION A: EMAIL FORWARDING               OPTION B: DEDICATED BUSINESS INBOX
       (Free / Simple)                          (Professional / Recommended)
                │                                             │
      GoDaddy / Forwarding Service                  Google Workspace, Zoho Mail,
      redirects email to your personal              or GoDaddy Webmail
      Gmail / Outlook inbox                         
                │                                             │
      ✅ Free to receive                             ✅ Dedicated login for business
      ⚠️ Replying reveals personal address           ✅ Reply directly as info@nazanoor.com
         (unless SMTP "Send As" is configured)      ✅ Better deliverability & brand trust
```

---

### Option A: Email Forwarding (Forward to Personal Gmail / Outlook)

If you don't want to pay for an additional email inbox subscription and want customer emails sent to `info@nazanoor.com` or `support@nazanoor.com` to land directly in your personal Gmail:

#### How to Set Up Email Forwarding in GoDaddy:
1. Log in to your [GoDaddy Account](https://account.godaddy.com/).
2. Go to **My Products** > scroll down to **Additional Products** or **Domains**.
3. Under **nazanoor.com**, click **Manage** > **Email Forwarding** (or search for Email Forwarding in your GoDaddy dashboard).
4. Click **Create Forward** (or **Add Forwarding Rule**).
5. In the **Forward this address** field, enter: `info` (or `support`).
6. In the **To this address** field, enter your personal email (e.g., `yourname@gmail.com`).
7. Click **Save**.
8. Test it by sending an email from another email address to `info@nazanoor.com` and confirming it lands in your Gmail.

> ⚠️ **The Reply Trap with Email Forwarding:**
> When an email forwards to your Gmail, you can read it. However, if you click **Reply**, Gmail will default to replying with your **personal `@gmail.com` address**, exposing your personal email to customers.
> 
> **How to reply as `info@nazanoor.com` from Gmail (Send mail as):**
> 1. In Gmail, click **Settings (gear icon) > See all settings > Accounts and Import**.
> 2. In the **Send mail as** section, click **Add another email address**.
> 3. Enter your display name (`Naza Noor`) and address (`info@nazanoor.com`), and keep "Treat as an alias" checked.
> 4. Enter your SMTP details (e.g., GoDaddy's SMTP server `smtpout.secureserver.net` with port 465/SSL, or a free transactional SMTP like Brevo / Sendinblue).
> 5. Enter the verification code sent to your inbox. Once verified, you can select `info@nazanoor.com` in the **From** dropdown when composing or replying!

---

### Option B: Dedicated Business Email Host (Recommended in Video)

This is the standard approach shown in the tutorial. You get a real, independent mailbox where you log in, receive, and send replies directly as `info@nazanoor.com`.

| Provider | Typical Cost | Why Choose It |
| :--- | :--- | :--- |
| **Google Workspace** | ~$6 / user / month | The gold standard. Uses the official Gmail web and mobile interface with `@nazanoor.com`. Includes Drive and Meet. |
| **Zoho Mail** | **Forever Free** (up to 5 users) or ~$1 / mo | Most cost-effective. The free tier gives webmail access for custom domains with 5GB storage. |
| **GoDaddy Professional Email** | ~$2–$3 / month | Integrates directly with your existing GoDaddy MX records (`secureserver.net`). |

#### Setting Up Google Workspace or Zoho Mail:
1. **Sign Up:** Register at [Google Workspace](https://workspace.google.com/) or [Zoho Mail](https://www.zoho.com/mail/) using domain `nazanoor.com`.
2. **Domain Verification:** The provider will give you a TXT record (e.g. `google-site-verification=...` or `zoho-verification=...`). Add this TXT record in GoDaddy DNS.
3. **Point MX Records:**
   - **For Google Workspace:** Replace GoDaddy's MX records with:
     - `ASPMX.L.GOOGLE.COM` (Priority 1)
     - `ALT1.ASPMX.L.GOOGLE.COM` (Priority 5)
     - `ALT2.ASPMX.L.GOOGLE.COM` (Priority 5)
     - `ALT3.ASPMX.L.GOOGLE.COM` (Priority 10)
     - `ALT4.ASPMX.L.GOOGLE.COM` (Priority 10)
   - **For Zoho Mail:** Replace with Zoho MX records:
     - `mx.zoho.com` (Priority 10)
     - `mx2.zoho.com` (Priority 20)
     - `mx3.zoho.com` (Priority 50)
4. **Update SPF Record:** Update the TXT SPF record in GoDaddy:
   - For Google: `v=spf1 include:_spf.google.com ~all`
   - For Zoho: `v=spf1 include:zoho.com ~all`

---

## The 2 Systems Working Together

Regardless of whether you choose Forwarding (Option A) or a Dedicated Inbox (Option B), your store has two systems:

```
┌────────────────────────────────────────────────────────┐
│ 1. RECEIVING & REPLYING (Your Inbox or Forwarding)     │
│    Managed in GoDaddy, Google Workspace, or Zoho       │
│    Customer emails info@nazanoor.com -> You read/reply │
└───────────────────────────┬────────────────────────────┘
                            │
┌───────────────────────────┴────────────────────────────┐
│ 2. SENDING AUTOMATED NOTIFICATIONS (Shopify)           │
│    Managed in Shopify Admin + GoDaddy DNS              │
│    Order confirmations, receipts, tracking, marketing  │
└────────────────────────────────────────────────────────┘
```

---

## Using a Custom Email for Marketing & Selling

### What It Is

A custom branded email for marketing means all promotional campaigns, product
launches, abandoned cart reminders, and win-back flows send from
`info@nazanoor.com` (or `marketing@nazanoor.com`) rather than a generic
Shopify or third-party address.

This applies to:
* **Shopify Email** — built-in email marketing tool inside Shopify admin
  (Settings > Apps > Shopify Email). Send newsletters, promotions, and
  automated flows directly from your branded address.
* **Transactional Emails** — order confirmations, shipping updates, and
  return notifications triggered automatically by Shopify.
* **Abandoned Cart & Win-Back Automations** — automated sequences that
  re-engage shoppers who browsed or added to cart but didn't purchase.

### Why It Matters for Naza Noor

| Benefit | Impact |
| :--- | :--- |
| **Inbox placement** | Authenticated `@nazanoor.com` emails land in the Primary inbox, not Promotions or Spam. |
| **Open rates** | Branded sender names (`Naza Noor <info@nazanoor.com>`) consistently outperform generic addresses by 20–30% in open rate. |
| **Brand authority** | Every email reinforces that Naza Noor is a legitimate, established premium brand — not a dropshipper. |
| **Unsubscribe compliance** | Gmail and Yahoo 2024+ rules require one-click unsubscribe on bulk senders. Shopify Email handles this automatically when your domain is authenticated. |
| **Revenue from email** | For fashion and lifestyle brands, email typically drives 20–40% of total revenue when used consistently with weekly sends and automated flows. |

### Recommended Email Strategy for Naza Noor

#### Automated Flows (Set Once, Earn Always)
* **Welcome Series** — 3 emails over 5 days introducing the brand story,
  heritage textiles, and a first-purchase discount.
* **Abandoned Cart** — 2 emails: reminder at 1 hour, urgency nudge at 24 hours.
* **Post-Purchase** — Thank you + care instructions for handcrafted garments
  at day 1, cross-sell kaftans or kurti sets at day 7.
* **Win-Back** — Re-engage customers who haven't purchased in 90 days with
  a new arrival highlight or seasonal offer.

#### Broadcast Campaigns (Sent Manually)
* New collection launches (Eid, wedding season, festive drops).
* Restocks of popular Jamdani or Banarsi styles.
* Exclusive early access for repeat customers.

### Sender Address Recommendations

| Use Case | Recommended Address |
| :--- | :--- |
| Order confirmations & receipts | `orders@nazanoor.com` |
| Customer support replies | `support@nazanoor.com` |
| Marketing & newsletters | `hello@nazanoor.com` or `info@nazanoor.com` |
| New arrivals & campaigns | `collections@nazanoor.com` |

> ℹ️ All of the above require the same DKIM authentication steps in this guide.
> Each address you use as a Shopify sender must be authenticated separately,
> or you can authenticate the root domain (`nazanoor.com`) once to cover all
> addresses under it.

---

## Step-by-Step Setup Guide

### Step 1: Set Your Sender Email in Shopify Admin

1. Open **Shopify Admin**.
2. Navigate to **Settings > Notifications**.
3. Under the **Sender email** section, enter your branded email address:
   `info@nazanoor.com` (or `support@nazanoor.com`).
4. If Shopify displays *"Sender email isn't authenticated"*, click
   **Authenticate your domain**.
5. A modal will display **4 CNAME records** specifically generated for your store.

> ⚠️ **Important:** Keep this modal open, or copy all 4 Host and Value fields
> before closing. These values are unique to your store — do **not** use
> placeholder values from any external guide.

---

### Step 2: Add the 4 CNAME Authentication Records in GoDaddy

1. Log into your [GoDaddy Domain Portfolio](https://dcc.godaddy.com/control/portfolio).
2. Click on **nazanoor.com** > **DNS** (or **Manage DNS**).
3. Click **Add New Record** for each of the 4 CNAME records shown in Shopify.

#### GoDaddy Name Field Formatting Rule (Critical):
Shopify displays full hostnames like `s1._domainkey.nazanoor.com`.
In GoDaddy, you must **omit `.nazanoor.com`** — GoDaddy appends it automatically.

> ✅ **Correct:** `s1._domainkey`
> ❌ **Wrong:** `s1._domainkey.nazanoor.com`

#### The 4 CNAME Records to Add:

| Record # | Type | Name / Host | Value / Points To | TTL |
| :--- | :--- | :--- | :--- | :--- |
| **Record 1** | `CNAME` | *(DKIM prefix from Shopify modal)* | *(DKIM value from Shopify modal)* | `1 Hour` |
| **Record 2** | `CNAME` | *(DKIM prefix from Shopify modal)* | *(DKIM value from Shopify modal)* | `1 Hour` |
| **Record 3** | `CNAME` | *(DKIM prefix from Shopify modal)* | *(DKIM value from Shopify modal)* | `1 Hour` |
| **Record 4** | `CNAME` | *(Return-path prefix from Shopify modal)* | *(Return-path value from Shopify modal)* | `1 Hour` |

> ⚠️ **Copy exact values from your Shopify authentication modal.**
> These are unique to your store and cannot be obtained from any other source.

4. Click **Save** after adding each record.

---

### Step 3: Verify Domain Authentication in Shopify

1. Return to **Shopify Admin > Settings > Notifications**.
2. Click **Authenticate domain** (or **Verify**).
3. Status will update to:
   * ✅ **Authenticated:** All order confirmations, receipts, and marketing emails
     will send as `Naza Noor <info@nazanoor.com>` with no spam flags or
     "via shopifyemail.com" label.
   * 🕐 **Pending:** DNS records are still propagating. Allow 15–30 minutes
     (up to 24 hours) and refresh.

---

### Step 4: Verify DMARC Record Status

Both Google and Yahoo require a published DMARC record to accept marketing
and transactional emails.

* **Live Status for Naza Noor:** Your domain already has an active DMARC record
  configured in GoDaddy — no action needed:

  ```text
  Host: _dmarc
  Value: v=DMARC1; p=quarantine; adkim=r; aspf=r; rua=mailto:dmarc_rua@onsecureserver.net;
  ```

* This meets the Gmail and Yahoo 2024+ sender authentication mandate.

---

### Step 5: Test Your Outbound Email Delivery

1. Go to **Shopify Admin > Settings > Notifications**.
2. Click on **Order confirmation** > **Send test email**.
3. Send to a Gmail address and open the test email.
4. Click the three dots menu > **Show original**.
5. Confirm the following all show as **PASS**:
   * **DKIM: PASS**
   * **DMARC: PASS**

> ℹ️ **Note on SPF:** Shopify handles SPF for outbound store emails via its own
> shared infrastructure — you do not need to add a Shopify-specific SPF record
> in GoDaddy. Your existing GoDaddy SPF record covers your GoDaddy mailbox only
> (for replies you send manually). Both records serve different purposes and
> do not conflict.

---

## How to Check Live DNS via Terminal

```bash
# Check incoming mail MX records (GoDaddy Mailbox)
dig +short MX nazanoor.com @8.8.8.8

# Check DMARC authentication policy
dig +short TXT _dmarc.nazanoor.com @8.8.8.8

# Check your GoDaddy mailbox SPF record
dig +short TXT nazanoor.com @8.8.8.8
```

---

## Troubleshooting & Common Mistakes

| Problem | Root Cause | Solution |
| :--- | :--- | :--- |
| **"Authentication Failed" in Shopify** | Full domain entered in GoDaddy Name field. | Edit the record — set Name to prefix only, e.g., `s1._domainkey`. |
| **Customer replies aren't received** | Mailbox not created in GoDaddy, or MX records missing. | Confirm `info@nazanoor.com` exists as an active mailbox in GoDaddy Email dashboard, or set up email forwarding. |
| **"Via shopifyemail.com" still appears** | DKIM records not yet authenticated. | Complete Steps 2 & 3. Once verified, the "via" label disappears in Gmail and Outlook. |
| **Marketing emails going to Promotions tab** | Normal Gmail behaviour for bulk senders. | Encourage customers to move your email to Primary and add you to contacts at the first touchpoint (welcome email). |
| **Spam rate warning in Google Postmaster** | Sending to unengaged subscribers. | Use double opt-in via Shopify Forms and remove subscribers inactive for 90+ days. |

---

## Verification Checklist

- [ ] Branded email address created in GoDaddy (`info@nazanoor.com` or
      `support@nazanoor.com`).
- [ ] Sender email entered in **Shopify Admin > Settings > Notifications**.
- [ ] Opened Shopify authentication modal and copied all 4 CNAME records.
- [ ] Added all 4 CNAME records to GoDaddy DNS with correct Name prefixes
      (no `.nazanoor.com` appended).
- [ ] Clicked **Authenticate domain** in Shopify — status shows green.
- [ ] Confirmed live DMARC record is active (`_dmarc.nazanoor.com`).
- [ ] Sent test order confirmation to Gmail — **DKIM: PASS** and **DMARC: PASS**
      confirmed in "Show original".
- [ ] Welcome series automation created in Shopify Email.
- [ ] Abandoned cart flow activated.
- [ ] Post-purchase follow-up sequence scheduled.


### References 

- [Setup Domain & Business Emails for Shopify](https://www.youtube.com/watch?v=fPtk9jJ5rIQ) – Video tutorial for custom domains and mailboxes.

---

*Last updated: September 14, 2026*
