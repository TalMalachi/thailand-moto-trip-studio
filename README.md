# Thailand Moto Trip Studio

Private cloud trip planner in Hebrew, hosted on GitHub Pages with Supabase Auth and PostgreSQL.

The public repository contains application code only. Trip contents live in PostgreSQL behind Row Level Security. The browser uses a publishable key; never add a service-role key or database password to the frontend.

## Sign in

Use the email account invited by the project administrator. Open the one-time email link in the browser you want to use for the app. Public registration is disabled.

Successful edits are acknowledged only after the cloud write succeeds. Refresh from the cloud, or return to the app window, to see changes made on another device. Offline writing is not supported. A settings form or open editor is not automatically replaced by background refresh.

## Build and tests

The complete unbundled source is provided in `cloud-source.zip` alongside the deployed `index.html` and `app.js`.

```sh
unzip cloud-source.zip
npm ci
npm test
npm run build
```

Node.js 22 or newer is required by the pinned Supabase SDK. `src/` holds auth, repository, backup, configuration, and UI modules. The committed lockfile pins build dependencies.

## Database

`supabase/schema.sql` is the version-controlled snapshot of the cloud schema. `supabase/tests/access.sql` tests owner isolation, unauthorized writes, stale updates, and anonymous access in a rolled-back transaction. Run the access test on a dedicated test database before changes to the security model.

Schema changes should be applied through Supabase migrations. No trip contents or account identifiers belong in migrations or source control. Bind a trip to its invited user through an authorized administrative operation, never client-side email matching.

## Backups

Export JSON from Settings. Imports preview new items and add only missing source IDs. Existing records and trip settings are preserved. Legacy local backups are accepted; arbitrary text is rendered as text and only HTTP/HTTPS links are permitted.
