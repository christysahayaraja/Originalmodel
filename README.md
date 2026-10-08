# A Cooked Again

Supabase-backed restaurant website (static HTML/CSS/JS) with customer login, an admin dashboard, menu and gallery management.

## Setup

1. **Supabase keys** – Dashboard → Project Settings → API Keys: copy the **publishable** key (`sb_publishable_...`).
2. **Config** – put the Project URL and key in `config.js`, or generate it:
   ```bash
   SUPABASE_URL=... SUPABASE_PUBLISHABLE_KEY=... npm run configure
   ```
   `npm run build` does the same on Netlify/Vercel and keeps `config.js` if no env vars are set.
3. **Database** – run `supabase/schema.sql` in the Supabase SQL Editor (tables, RLS policies, profile trigger; safe to re-run).
4. **Auth** – Authentication → Providers → Email: keep *Enable sign ups* on. If *Confirm email* is on, add your site's `login.html` URL under Authentication → URL Configuration.
5. The **first account created becomes Admin**.

## Run locally

Serve over http(s), not `file://`:
```bash
npx serve .
```

## Security

- `config.js` is public: only the Project URL and publishable/anon key belong in it.
- **Never** put a `service_role` / `sb_secret_` key in any website file.
- Passwords are handled only by Supabase Auth; RLS in `supabase/schema.sql` protects data.

## Troubleshooting

The login page runs a startup check and reports missing config, invalid URL, invalid key, or network/CORS problems.

## Scripts

| Command | Purpose |
|---|---|
| `npm run configure` | Generate `config.js` from env vars |
| `npm run build` | Same, but optional (for hosting platforms) |
| `npm run check` | Project scan |
