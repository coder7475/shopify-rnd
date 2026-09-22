# Customer Account Domain Setup Guide: Naza Noor

A step-by-step administrator and troubleshooting guide for setting up and verifying
a custom branded customer accounts domain (`customer-account.nazanoor.com`) for Naza Noor.

---

## Quick Reference Summary

| Property | Value |
| :--- | :--- |
| **Subdomain** | `customer-account.nazanoor.com` |
| **DNS Provider** | GoDaddy (Nameservers: `ns59.domaincontrol.com`, `ns60.domaincontrol.com`) |
| **Target Host (Shopify)** | `shops.myshopify.com` |
| **Current Status** | DNS Error / CNAME Missing or Not Propagated |
| **Feature Used** | Shopify New Customer Accounts (Passwordless 6-Digit Code Login) |

---

## Why a Branded Customer Account Domain Matters

By default, Shopify redirects customer account logins to a generic store URL
(`qyzcd2-j5.account.myshopify.com`).

Configuring `customer-account.nazanoor.com`:
* **Brand Consistency:** Customers stay on your domain throughout their entire
  session without confusing third-party redirects.
* **Higher Security & Trust:** Shoppers feel safe entering verification codes
  on an official `nazanoor.com` subdomain.
* **Seamless Post-Purchase Access:** Customers can track orders, request
  self-serve returns, and manage saved shipping addresses directly within
  your branded portal.

---

## Step-by-Step Setup Guide

### Step 1: Add the CNAME Record in GoDaddy

1. Open a web browser and sign in to the
   [GoDaddy Domain Portfolio](https://dcc.godaddy.com/control/portfolio).
2. Locate **nazanoor.com** in your domains list.
3. Click the three dots menu (or click the domain name) and select
   **Manage DNS** (or **DNS**).
4. In the DNS Records section, click **Add New Record**.
5. Fill in the exact fields below:

| Field | Exact Value to Enter | Notes |
| :--- | :--- | :--- |
| **Type** | `CNAME` | Select from the dropdown |
| **Name / Host** | `customer-account` | Do **NOT** enter the full domain. GoDaddy automatically appends `.nazanoor.com`. |
| **Value / Points to** | `shops.myshopify.com` | Ensure there are no extra spaces before or after. |
| **TTL** | `1/2 Hour` or `1 Hour` (or `Default`) | Lower TTL propagates faster across global DNS servers. |

6. Click **Save** to apply the record.

---

### Step 2: Verify the Domain in Shopify Admin

`customer-account.nazanoor.com` is already listed in your Shopify admin.

1. Go to **Settings > Domains**.
2. Click on `customer-account.nazanoor.com`.
3. Click **Verify connection**.
4. Shopify will provision a free SSL/TLS certificate automatically
   (usually 10–30 minutes, occasionally up to 24 hours).

---

### Step 3: Assign the Subdomain to Customer Accounts

After the domain shows as **Connected** with a green checkmark:

1. Go to **Shopify Admin > Settings > Customer accounts**.
2. Locate the **Accounts in online store and checkout** section.
3. Make sure **New customer accounts** is selected (recommended by Shopify
   for passwordless logins).
4. In the **URL / Domain** section, select `customer-account.nazanoor.com`.
5. Click **Save**.

Customers clicking the Account icon on `nazanoor.com` will now be directed
to `https://customer-account.nazanoor.com`.

---

## How to Test and Verify

### Method 1: Terminal (Instant Check)

```bash
dig +short CNAME customer-account.nazanoor.com @8.8.8.8
```

* **Expected output:** `shops.myshopify.com.`
* **Blank output:** Record not yet added or GoDaddy DNS still updating.

### Method 2: Web Browser

Visit [whatsmydns.net](https://www.whatsmydns.net/#CNAME/customer-account.nazanoor.com)
and confirm green checkmarks worldwide pointing to `shops.myshopify.com`.

---

## Troubleshooting & Common Mistakes

| Problem | Root Cause | Solution |
| :--- | :--- | :--- |
| **"CNAME already exists" in GoDaddy** | A conflicting record exists for `customer-account`. | Delete the conflicting record, then re-add the CNAME. |
| **Full domain in Name field** | Entering `customer-account.nazanoor.com` creates a double-appended hostname. | Edit the record — set **Name** to just `customer-account`. |
| **"SSL Pending" in Shopify** | Certificate issuance in progress. | Wait 15–60 minutes. Do not remove or reconnect the domain. |
| **"DNS Error: Missing CNAME" in Shopify** | GoDaddy DNS changes not yet propagated. | Wait 15 minutes, then click **Verify connection** again. Can take up to 48 hours globally. |

---

## Verification Checklist

- [ ] Added CNAME: Name = `customer-account`, Points to = `shops.myshopify.com` in GoDaddy.
- [ ] Confirmed no duplicate or conflicting records exist for `customer-account`.
- [ ] Clicked **Verify connection** in **Settings > Domains**.
- [ ] SSL certificate status shows **Active / Secure**.
- [ ] Set `customer-account.nazanoor.com` as active URL in **Settings > Customer accounts**.
- [ ] Tested account icon on `nazanoor.com` — confirms seamless redirect.

---

*Last updated: September 14, 2026*
