# Thailand Moto Trip Studio

Private cloud trip planner in Hebrew with Supabase Auth and PostgreSQL. GitHub Pages hosts code only. Trip data is protected by owner-based RLS. No account identifiers, passwords, or server keys belong in this repository.

Sign in with the existing invited account and password. Public registration is disabled. First password setup uses a recovery email link, subject to the email provider's rate limits. After signing in, use Change password to choose a new password. The app never stores passwords. Only Supabase stores their hashes.

The full unbundled source is in cloud-source.zip. Unzip it, run npm ci, npm test, and npm run build with Node.js 22 or newer. Dependency versions are pinned in package-lock.json.

The database schema and access isolation tests are in supabase/. Cloud writes require successful server acknowledgment. Settings offers JSON backup export and previewed additive import. Offline writing is not supported.
