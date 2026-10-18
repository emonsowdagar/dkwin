# PlayNova BD — responsive arcade starter

A Bengali, mobile/desktop-friendly starter for a casual games community. It includes:
- Responsive homepage and 40 game catalogue cards
- Four playable mini-games (memory match, quick math, Bengali quiz, tap challenge)
- Server-side registration/login with bcrypt password hashing and session cookies
- SQLite user and demo-ledger storage
- Starter admin summary for user accounts and demo transactions
- A payment endpoint that remains disabled until an approved provider integration is implemented

## Safety and payment scope
This project is for non-betting casual games. Demo points are not money, have no cash value, cannot be withdrawn, and do not buy chances to win cash/prizes. The app intentionally does not implement deposits to personal numbers, cash-outs, wagers, or fake payment success messages.

Real payment processing is NOT implemented in this starter. To enable a legitimate payment method, the site operator must qualify for and obtain an approved merchant account, then implement the provider's official server-side checkout API, signed webhook verification, idempotency, refund handling, audit logs, and applicable legal/privacy requirements. Never put secret keys in browser JavaScript. Do not set `PAYMENTS_ENABLED=true` until the actual adapter is implemented and tested in sandbox mode.

## Requirements
- Node.js 20 or newer
- npm

## Run locally
1. Copy `.env.example` to `.env`.
2. Replace `SESSION_SECRET` with a long random value.
3. Set a strong unique `ADMIN_PASSWORD` and a real admin email before the first run. The initial admin is only created if the database has no users yet.
4. Install and run:
   ```bash
   npm install
   npm start
   ```
5. Open `http://localhost:3000`.

The SQLite database `playnova.sqlite` is created beside `src/` automatically (project root). Keep it backed up and outside public web folders.

## Production checklist
- Use HTTPS and secure environment variables.
- Use a persistent disk/database and a production session store; the default express-memory session store is not suitable for production.
- Add CSRF protection, email verification, password reset, account lockout, monitoring, database backups, and security testing.
- Restrict the admin account, change its initial password, and add audit logging.
- Complete the official payment adapter and verified webhooks before accepting money.
- Publish terms, privacy notice, support contact, and eligibility/age rules; check applicable Bangladesh law and provider rules.

## Current limitations
The 40 entries are catalogue cards; four are playable. Other games need their own game logic. Admin is a starter summary, not a complete CMS. Payment integration is a disabled placeholder and must not be advertised as live.
