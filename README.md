# My Money

A private, responsive personal finance tracker in GBP.

## Features
- Main, Use, Savings balances
- Automatic income split (default: Main 50%, Use 30%, Savings 20%)
- Spending categories: Food, Beauty, Toys, Transport, Other
- JPY, HKD, CNY and GBP entries converted to GBP using a public exchange-rate API
- Main transfer confirmation; no transfers out of Savings
- Weekly spending summary and transaction history
- Firebase email/password authentication using a username alias

## Setup (required before sign-in works)
1. Create a Firebase project at https://console.firebase.google.com/ .
2. Add a **Web app** and copy its public Firebase config values into `index.html`. Do not paste private keys.
3. Under **Authentication > Sign-in method**, enable **Email/Password**. Do **not** enable public self-registration in the website.
4. Under **Authentication > Users**, manually add **one user**. For a username `hayley`, enter `hayley@mymoney.invalid` as its email alias and choose a strong password **inside Firebase**, never in ChatGPT. The alias cannot receive password-reset emails. If you want password recovery, use a real email instead and adjust the login code accordingly.
5. Copy the newly created user's **UID** into the `OWNER_UID` constant in `index.html`.
6. Create a Firestore database. Copy the contents of `firestore.rules` into **Firestore > Rules**, replace `REPLACE_WITH_OWNER_UID` with the same UID, and **Publish**. Never use Firestore test-mode rules for a deployed site.
7. Host the site on Firebase Hosting or another HTTPS static hosting service. A private GitHub repository is not itself a hosted website.

## Important limitations
- This is a manual tracker, not a bank account.
- The Savings lock and Main warning are **interface rules**, not bank controls. The current Firestore rules restrict access by account UID but do not enforce balance or transfer invariants on the server. A user with access to the authenticated browser could alter records; do not treat this as tamper-proof accounting.
- A username alias under `mymoney.invalid` cannot receive recovery emails. Consider using a real email for a production account.
- The current app performs balance updates and transaction-history writes separately; if a write fails, the records could diverge. This is a starter version, not production-grade financial software.
- Rates come from open.er-api.com, not Google, and may differ from the rate charged by your bank.
- Firebase project config is public by design; **never** commit passwords, service-account credentials, or secret API keys.

## Privacy
Keep this GitHub repository private. Configure Firebase Authentication and Firestore security rules before using it with personal records.
