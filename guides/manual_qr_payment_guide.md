# Technical Implementation Guide: Manual Payments with QR Codes (Venmo, Cash App, Zelle) on Shopify

**Target Store:** Clothing & Apparel Retail  
**Platforms:** Shopify Online Store & Shopify POS  

---

## 1. Executive Summary & Shopify Architectural Constraints

For clothing brands, offering alternative wallet channels like **Venmo**, **Cash App**, or **Zelle** captures mobile-first customers and social commerce buyers. However, implementing this on Shopify requires navigating specific platform rules:

### Core Platform Constraints
1. **PCI-DSS & Sandbox Checkout:** Shopify restricts direct HTML/JavaScript injection on the native checkout steps. You **cannot embed raw image tags (QR codes)** directly in the payment method selection screen.
2. **Text-Only Native Input:** Native manual payment methods only accept plain text instructions during the payment step.
3. **Checkout Extensibility (Modern Standard):** Legacy `checkout.liquid` and "Additional Scripts" have been phased out. Displaying visual blocks (like QR code images or interactive copy widgets) on the **Thank You / Order Confirmation** page requires **Checkout UI Extensions** (Checkout Extensibility).

---

## 2. Solution Architecture & Comparison

```
                                 SHOPIFY CHECKOUT FLOW
                                           │
         ┌─────────────────────────────────┼────────────────────────────────┐
         ▼                                 ▼                                ▼
  [Option 1: Automated]            [Option 2: Extensibility]         [Option 3: Notification]
  Official PayPal/Venmo            Manual Method + QR Block          Manual Method + Email/SMS
         │                                 │                                │
  • Instant automated capture       • Manual payment status           • Zero app overhead
  • Native Venmo app integration    • Visual QR on Thank You page     • QR sent via Klaviyo/Shopify
  • Standard gateway transaction    • Manual staff verification       • High customer friction
```

### Option 1: Official Automated Integration (PayPal with Venmo Enabled)
Venmo is owned by PayPal. In supported regions (notably the US), enabling **PayPal** on Shopify automatically enables Venmo as an express checkout button and an integrated payment option.
* **How it works:** The buyer clicks Venmo $\rightarrow$ Opens the Venmo app or generates an authentic Venmo desktop QR $\rightarrow$ Payment is confirmed instantly $\rightarrow$ Order is marked **Paid** automatically.
* **Best for:** Most clothing stores prioritizing automated fulfillment, fast shipping, and zero manual reconciliation.

### Option 2: Custom Manual Payment Method + QR Code on Thank You Page (Recommended for Direct Transfers)
Set up a custom manual payment option in Shopify Admin and inject the QR code on the **Thank You** page via **Checkout Extensibility**.
* **How it works:** 
  1. Customer selects `Venmo / Cash App QR Transfer` at checkout.
  2. Customer completes checkout; order is saved as **Payment Pending / Unpaid**.
  3. On the **Thank You (Order Status)** page, a custom UI extension displays the QR code, merchant handle (`@YourClothingBrand`), and explicit instructions to add the Order # in the transfer note.
  4. Once payment arrives, store staff marks the order as **Paid** in Shopify Admin.
* **Implementation:**
  * **No-Code / Low-Code:** Install a Checkout Extensibility app from the Shopify App Store (e.g., *Payster - QR Code Payments*, *ReConvert*, or *Checkout Customizer*). Add the app block to the **Thank You** page via **Settings > Checkout > Configurations > Customize**.
  * **Custom In-House Extension:** Build a custom app extension targeting `purchase.thank-you.block.render` using the Shopify CLI.

### Option 3: Manual Payment + Dynamic Email / SMS Flow
* **How it works:** Set up the manual payment method, and automatically dispatch an immediate notification (via Shopify Notifications or Klaviyo) containing the QR code image and deep link.
* **Best for:** Stores with zero budget for apps that want a fallback for orders placed via manual methods.

---

## 3. Cost & Fee Structure

| Item | Option 1: Official PayPal/Venmo | Option 2: Manual Method + App Block | Option 3: Manual Method + Email Flow |
| :--- | :--- | :--- | :--- |
| **Shopify Platform Transaction Fee** | Standard gateway rates (~2.5% – 2.9% + 30¢) | **0%** (Shopify does not charge transaction fees on manual methods) | **0%** |
| **Provider Transfer Fee** | Standard gateway rates (deducted automatically) | **1.9% + $0.10** (Venmo for Business standard rate) | **1.9% + $0.10** (Venmo for Business) |
| **App / Software Cost** | $0/month | ~$5 – $19/month (or $0 if built with custom CLI extension) | $0/month |
| **Operational Labor** | **None** (Fully automated) | **Moderate to High** (Staff must verify payment before dispatch) | **Moderate to High** (Manual verification) |

> ⚠️ **Important Compliance Notice:** Using a personal Venmo account for commercial sales violates Venmo's Terms of Service and invites frozen accounts. Always establish a verified **Venmo for Business** profile.

---

## 4. Operational Considerations for Apparel Stores

Fashion and apparel stores face specific risks with manual payment methods:

1. **Inventory Locking (Dead Stock Risk):**
   * Manual payment orders instantly reserve inventory even when the financial status is **Pending**.
   * If a customer abandons the transfer, high-demand clothing items (specific sizes like S or M) remain locked and unavailable to other paying customers.
   * **Mitigation (Shopify Flow):** Set an automated rule to check manual payment orders after **2 hours**. If still marked `PENDING`, cancel the order and restock the inventory automatically.
2. **Missing Order Numbers in Payment Notes:**
   * Customers frequently forget to add their order number or use a different name on their Venmo account than their shipping name.
   * Add a clear instruction: *"Enter Order # in the Venmo memo."*
3. **Refunds & Exchanges:**
   * Because payment is collected outside Shopify, refunds cannot be processed automatically via the Shopify Admin refund button. Store staff must initiate refunds manually inside the Venmo app.

---

## 5. Step-by-Step Configuration Guide

### Step 1: Create the Manual Payment Method in Shopify
1. Navigate to **Shopify Admin** > **Settings** > **Payments**.
2. Scroll to the **Manual payment methods** section.
3. Click **Add manual payment method** > **Create custom payment method**.
4. Set **Custom payment method name**:
   ```
   Venmo / Cash App QR Transfer
   ```
5. Set **Additional details** (Displayed at checkout payment step):
   ```text
   Pay easily via Venmo or Cash App. After clicking "Complete order", your QR code and payment instructions will appear on the confirmation page.
   ```
6. Set **Payment instructions** (Displayed on the Thank You page and confirmation email):
   ```text
   1. Open Venmo and scan our QR code, or transfer to: @YourClothingBrand
   2. Amount: Please pay the exact order total.
   3. CRITICAL: Enter your Order # in the payment note/memo.
   4. Your apparel order will be packed and shipped once payment is confirmed.
   ```
7. Click **Activate**.

---

### Step 2: Display the QR Code on the Thank You Page (Checkout Extensibility)

#### Using a Verified Checkout Extensibility App (Fastest)
1. Install a QR payment or Thank You page customizer app from the Shopify App Store (such as *Payster* or *ReConvert*).
2. Go to **Settings** > **Checkout** > click **Customize** under Checkout Configurations.
3. In the top dropdown menu, select **Thank You**.
4. In the left-hand sidebar, click **Add app block**.
5. Select your QR Code app block, upload your Venmo QR graphic, and set visibility rules so it displays specifically when the selected gateway is `Venmo / Cash App QR Transfer`.
6. Save and publish.

#### For Custom Developers (Shopify CLI Extension)
If building an in-house app extension, target `purchase.thank-you.block.render` using `@shopify/ui-extensions-react/checkout`:

```tsx
import {
  reactExtension,
  Image,
  BlockStack,
  Text,
  Banner
} from '@shopify/ui-extensions-react/checkout';

export default reactExtension('purchase.thank-you.block.render', () => <VenmoPaymentBlock />);

function VenmoPaymentBlock() {
  return (
    <Banner title="Complete Your Venmo Payment" status="info">
      <BlockStack spacing="loose" alignment="center">
        <Text size="base">Scan the QR code below using your Venmo app to finalize your order:</Text>
        <Image
          source="https://cdn.shopify.com/s/files/1/xxxx/xxxx/files/venmo-qr.png"
          accessibilityDescription="Venmo Payment QR Code"
          fit="contain"
          aspectRatio={1}
        />
        <Text bold size="medium">Venmo Handle: @YourClothingBrand</Text>
        <Text appearance="subdued" size="small">Remember to include your order number in the payment note.</Text>
      </BlockStack>
    </Banner>
  );
}
```

---

### Step 3: Set Up Inventory Protection via Shopify Flow

To prevent unpaid orders from holding fashion inventory indefinitely:
1. Open **Shopify Flow** and click **Create workflow**.
2. **Trigger:** `Order created`.
3. **Condition:** Check if `order.paymentGatewayNames` includes `Venmo / Cash App QR Transfer`.
4. **Action:** `Wait` $\rightarrow$ `2 hours`.
5. **Condition:** Check if `order.displayFinancialStatus` equals `PENDING`.
6. **Action:** `Cancel order` (Reason: `Customer`, Staff note: `Automated cancellation: Venmo transfer not received within 2 hours`) $\rightarrow$ Check **Restock items**.

---

## 6. Strategic Recommendation Matrix

* **Recommendation 1 (Best Overall):** Use **PayPal Complete Payments** with Venmo enabled. This provides native Venmo express buttons, automated verification, and instant inventory updates with zero fulfillment friction.
* **Recommendation 2 (Best for Low Platform Fees / Pop-up Brands):** Use **Option 2 (Manual Method + Checkout Extensibility App)** with an automated Shopify Flow cancellation rule to protect apparel inventory.
