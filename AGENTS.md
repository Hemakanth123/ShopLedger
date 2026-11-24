# Stack

- Node.js application using Express and body-parser.
- Browser UI is served from `public/` by `server.js`.
- Runtime data is stored in `data/db.json` through `lib/store.js`.
- Dependencies are declared in `package.json`.

# Module map

- `routes/customers.js` — customer listing and Khata settlement routes.
- `routes/orders.js` — order listing, creation, lookup, and cancellation routes.
- `routes/products.js` — product and active-coupon routes.
- `routes/reports.js` — dashboard, GST reconciliation, pricing preview, and admin export routes.
- `lib/coupons.js` — coupon normalization, lookup, validation, and discount calculation.
- `lib/dates.js` — current dates, date-key normalization, and fiscal-year helpers.
- `lib/inventory.js` — product lookup, sellable-stock checks, stock changes, and summaries.
- `lib/invoice.js` — printable invoice figures and HTML rendering.
- `lib/ledger.js` — customer Khata balances, charges, reversals, and settlements.
- `lib/orders.js` — order creation, lookup, cancellation, and listing.
- `lib/pricing.js` — subtotals, discounts, GST-aware checkout totals, and line breakdowns.
- `lib/reports.js` — dashboard summaries and invoice/ledger reconciliation.
- `lib/store.js` — JSON database reads, writes, structure defaults, and audit entries.
- `lib/tax.js` — HSN GST-rate resolution and CGST/SGST splitting.

# Commands

- Start the app: `node server.js` or `npm start`.
- Run tests: `node --test` (no test suite is currently present).

# Rules

1. Write characterization tests before changing behaviour.
2. Change only the module(s) the ticket is about.
3. Tests never read or write `data/db.json`; use in-memory data.
4. Add no dependencies.
5. Make the smallest fix that works.

# Current ticket

Invoice total and GST breakdown do not match what the customer was billed.
Allowed files: `lib/invoice.js` (`lib/tax.js` only if truly needed).
