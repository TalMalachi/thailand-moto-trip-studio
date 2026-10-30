# Motor Trip Studio

Private cloud trip planner in Hebrew with Supabase Auth and PostgreSQL. GitHub Pages hosts code only. Trip data is protected by owner-based RLS. No account identifiers, passwords, or server keys belong in this repository.

Sign in with the existing invited account and password. Public registration is disabled. First password setup uses a recovery email link, subject to the email provider's rate limits. After signing in, use Change password to choose a new password. The app never stores passwords. Only Supabase stores their hashes.

The full unbundled source is in cloud-source.zip. Unzip it, run npm ci, npm test, and npm run build with Node.js 22 or newer. Dependency versions are pinned in package-lock.json.

The database schema and access isolation tests are in supabase/. Cloud writes require successful server acknowledgment. Settings offers JSON backup export and previewed additive import. Offline writing is not supported.

Route opens with an interactive OpenStreetMap map and a daily-plan sub-menu. Each marker offers Google Maps and Waze links. General destination markers are explicitly approximate; optional stop latitude/longitude fields provide exact pins and survive backups. Tile imagery requires an Internet connection; navigation links remain available in the point list. Leaflet license is in THIRD_PARTY_NOTICES.txt.

The mobile interface uses four primary tabs and a More menu for overview, equipment, and settings. Account details contain password and sign-out controls. Record notes expand in place; failed saves retain the editor draft. The design system is documented in design-system/motor-trip-studio/MASTER.md.


After login, the destination picker shows all owner-visible trips. Destinations have an independent active flag and isolated trip items. Inactive destinations remain editable; this flag is organizational and does not change access permissions. Use New destination to create a future trip such as Vietnam. Existing Thailand data is retained.

The multi-destination schema upgrade is in supabase/multi-destinations.sql (already applied to the existing project). Destination updates use optimistic versions and owner-based RLS. Password recovery redirects use the current application base URL; Supabase must allow the published /motor-trip-studio/ URL.

## Destination planning agent

Destination edit includes a planning questionnaire, input approval, cost allowance and safe run review. Server enforcement: 20 ILS/account/month, 5 ILS/run, no customer billing, no purchases or messages. Real AI execution remains disabled until server-side provider credentials and verified, unexpired pricing are configured. See docs/planning-agent.md for secure activation and operational limitations.
