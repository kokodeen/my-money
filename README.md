# My Money — local-only edition

A minimalist money tracker with a username/password login and **no Firebase or backend**.

## What works
- One-time username/password setup on each browser
- Main, Use and Savings ledger balances (GBP)
- Automatic income allocation: 50% Main, 30% Use, 20% Savings by default; adjustable Savings share
- Food, Beauty, Toys, Transport and Other spending categories
- Expense tracking in GBP, JPY, HKD and CNY, with live rates from open.er-api.com
- Transfers from Main require confirmation; Savings transfers out are not offered
- Weekly spending chart and transaction history

## Start
Open `index.html` through an HTTPS static website host (such as Netlify or Cloudflare Pages). This private GitHub repository is **not** a hosted website. Local testing also works with a simple localhost server.

On first visit, create a username and password. On later visits in **the same browser**, sign in with them.

## IMPORTANT: Security and data limitations
- This is a **local-only demonstration**, not a secure online account.
- Username/password verification is local; it is **not server-side authentication**. Anyone who can access the browser's stored data can read or modify the financial records, bypass the lock, or delete them.
- Financial data is stored **unencrypted in localStorage**. Do not use on a shared or untrusted device. Never store actual banking credentials here.
- Clearing site data, switching browsers/devices or using private browsing may lose your records. **There is no cloud sync or backup** and no password recovery.
- Savings is an interface-only vault, not an actual bank account or tamper-proof savings lock.
- This version does not connect to bank accounts or move real money.
- The exchange-rate service is third-party, not Google, and conversion is indicative.
- For secure multi-device sync and account protection, a backend with authentication and access rules is required.

The previous Firebase rules file is no longer used by this version.
