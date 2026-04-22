# Privacy Page Update Spec

**Target repo:** `cyclescope/modelportfolio-privacy` (the canonical GitHub Pages source at https://cyclescope.github.io/modelportfolio-privacy/).

This repo (`schiang418/modelportfolio-privacy`) is a staging/reference copy — mirror any approved changes into the `cyclescope` repo.

**Target file:** `index.html`

**Reason for update:** The CycleScope Model Trades iOS app has an in-app purchase (IAP) subscription tier managed via RevenueCat. The current privacy policy does not disclose this. Apple's App Review compares your App Privacy questionnaire and this page against actual app behavior. Shipping without these updates risks a Guideline 5.1.1 / 3.1.2 rejection.

---

## Summary of changes

1. **Bump "Last updated" date** to the date the edit is made.
2. **Add a new "Subscriptions & In-App Purchases" section** under Terms of Service.
3. **Expand "Information We Collect"** to include subscription data.
4. **Add RevenueCat** to the "Third-Party Services" list.
5. **Update "Data Storage & Security"** to mention the `subscriptions` table and RevenueCat-hosted purchase metadata.
6. **Add one line to "Data Sharing"** clarifying that subscription purchase data is shared with RevenueCat and Apple as processors.

Do **not** change the Financial Disclaimer section. Do **not** change the contact email. Preserve the existing CSS and overall page structure.

---

## Exact edits

### Edit 1 — "Last updated" date

**Find** (around line 89):
```html
<p class="subtitle">Privacy Policy, Financial Disclaimer &amp; Terms of Service &mdash; Last updated: March 25, 2026</p>
```

**Replace with** (use the actual date of the edit; example shown):
```html
<p class="subtitle">Privacy Policy, Financial Disclaimer &amp; Terms of Service &mdash; Last updated: April 22, 2026</p>
```

---

### Edit 2 — Expand "Information We Collect"

**Find** (around lines 137–144) the `<ul>` under "Information We Collect":
```html
<ul>
  <li><strong>Apple Sign-In Data:</strong> When you sign in with Apple, we receive your name
    (if you choose to share it), email address (which may be a private relay address), and a
    unique Apple user identifier.</li>
  <li><strong>Account Record:</strong> We store your user ID, name, email, and sign-in provider
    in our database to authenticate your sessions.</li>
</ul>
```

**Add** two additional `<li>` items at the end of the same `<ul>`, immediately before `</ul>`:
```html
  <li><strong>Subscription Status:</strong> If you purchase a Pro subscription, we store your
    subscription state (active / expired / cancelled), product identifier, and subscription
    period in our database so the app can unlock paid features.</li>
  <li><strong>Purchase Receipts:</strong> Apple provides us with a purchase receipt at the time
    of subscription, which is validated through our subscription processor (RevenueCat). We do
    not receive or store your Apple ID, payment method, or billing address.</li>
```

---

### Edit 3 — Add RevenueCat to "Third-Party Services"

**Find** (around lines 163–169) the `<ul>` under "Third-Party Services":
```html
<ul>
  <li><strong>Apple Sign-In:</strong> For authentication. Subject to
    <a href="https://www.apple.com/legal/privacy/">Apple's Privacy Policy</a>.</li>
  <li><strong>Polygon.io:</strong> For stock price and chart data. Your personal information
    is not shared with Polygon.io; only stock ticker symbols are sent to retrieve market data.</li>
</ul>
```

**Add** two additional `<li>` items at the end of the same `<ul>`, immediately before `</ul>`:
```html
  <li><strong>Apple In-App Purchase:</strong> Subscription purchases are processed by Apple.
    Billing, payment, and renewal are handled entirely by Apple. Subject to
    <a href="https://www.apple.com/legal/internet-services/itunes/">Apple Media Services Terms</a>.</li>
  <li><strong>RevenueCat:</strong> We use RevenueCat to manage and validate subscriptions. When
    you purchase or restore a subscription, your app-assigned user identifier and the Apple
    purchase receipt are sent to RevenueCat. RevenueCat does not receive your name, email, or
    payment details. Subject to
    <a href="https://www.revenuecat.com/privacy">RevenueCat's Privacy Policy</a>.</li>
```

---

### Edit 4 — Update "Data Storage & Security"

**Find** (around lines 172–177):
```html
<p>
  Your account data is stored in a PostgreSQL database hosted on Railway, a cloud platform with
  industry-standard security practices. All communication between the app and our servers uses
  HTTPS encryption. Authentication tokens are stored securely on your device using iOS Keychain
  (via Expo SecureStore).
</p>
```

**Replace with:**
```html
<p>
  Your account and subscription data are stored in a PostgreSQL database hosted on Railway, a
  cloud platform with industry-standard security practices. Subscription metadata (status,
  product identifier, expiry) is additionally mirrored on RevenueCat's servers for receipt
  validation. All communication between the app and our servers uses HTTPS encryption.
  Authentication tokens are stored securely on your device using iOS Keychain (via Expo
  SecureStore).
</p>
```

---

### Edit 5 — Update "Data Sharing"

**Find** (around lines 186–190):
```html
<h3>Data Sharing</h3>
<p>
  We do not sell, rent, or share your personal information with third parties. We may disclose
  information only if required by law or to comply with a legal process.
</p>
```

**Replace with:**
```html
<h3>Data Sharing</h3>
<p>
  We do not sell, rent, or share your personal information with third parties for marketing
  purposes. We share limited data with Apple and RevenueCat strictly as payment and subscription
  processors, as described in the Third-Party Services section above. We may disclose
  information only if required by law or to comply with a legal process.
</p>
```

---

### Edit 6 — Add "Subscriptions & In-App Purchases" section

**Find** (around line 209) the start of Terms of Service:
```html
<h2>Terms of Service</h2>

<h3>Acceptance of Terms</h3>
```

**Add** a new section immediately **after** `<h2>Terms of Service</h2>` and **before** `<h3>Acceptance of Terms</h3>`:

> Actually, place the new section at the end of the Terms of Service block, immediately **before** the `<!-- ============================================================ -->` comment that precedes the Contact section (around line 271). This keeps the acceptance/description ordering natural.

Insert:
```html
<h3>Subscriptions &amp; In-App Purchases</h3>
<p>
  CycleScope Model Trades offers an optional <strong>Pro subscription</strong> that unlocks
  premium features (model portfolios, detailed weekly scans, stock charts, performance
  analytics). The following terms apply:
</p>
<ul>
  <li><strong>Price and duration:</strong> The Pro subscription is $49.99 USD per month and
    auto-renews monthly until cancelled. Pricing in other currencies is set by Apple's App Store
    based on your region.</li>
  <li><strong>Payment:</strong> Payment is charged to your Apple ID at confirmation of purchase.</li>
  <li><strong>Auto-renewal:</strong> The subscription automatically renews at the end of each
    billing period unless auto-renewal is turned off at least 24 hours before the end of the
    current period. Your Apple ID will be charged for renewal within 24 hours before the end of
    the current period.</li>
  <li><strong>Managing or cancelling:</strong> You can manage or cancel your subscription at any
    time from your device's Settings &rarr; Apple ID &rarr; Subscriptions. Cancellation takes
    effect at the end of the current billing period; no partial refunds are issued for the
    unused portion of a period.</li>
  <li><strong>Refunds:</strong> Refund requests are handled by Apple, not by CycleScope. You may
    request a refund through <a href="https://reportaproblem.apple.com">reportaproblem.apple.com</a>.</li>
  <li><strong>Restoring purchases:</strong> If you reinstall the app or switch devices (using
    the same Apple ID), you can restore your subscription from within the app's Settings screen.</li>
</ul>
```

---

## Acceptance checklist (for the editing agent)

- [ ] "Last updated" date reflects the date of the edit.
- [ ] "Information We Collect" lists Subscription Status and Purchase Receipts.
- [ ] "Third-Party Services" includes Apple IAP and RevenueCat with working external links.
- [ ] "Data Storage & Security" mentions RevenueCat mirroring subscription metadata.
- [ ] "Data Sharing" clarifies that Apple and RevenueCat are processors.
- [ ] A "Subscriptions & In-App Purchases" section exists under Terms of Service with price,
      auto-renewal, cancellation, refund, and restore details.
- [ ] The Financial Disclaimer block is unchanged.
- [ ] The contact email (`support@cyclescope.net`) is unchanged.
- [ ] No CSS or layout changes.
- [ ] Changes applied to `cyclescope/modelportfolio-privacy` (the canonical repo), not only to
      `schiang418/modelportfolio-privacy`.

## After merging

Verify the live page at https://cyclescope.github.io/modelportfolio-privacy/ reflects the
changes (GitHub Pages can take up to a minute to redeploy). Test that all four external links
(Apple privacy, Apple Media Services, RevenueCat privacy, Apple report-a-problem) open
correctly.
