# btx-bounce-pages

Static HTML bounce pages hosted on GitHub Pages.

Stripe's hosted flows (Identity verification, Connect onboarding) require a real
`https://` return URL and reject custom app schemes like `btxapp://...` directly.
These pages are the intermediary: Stripe redirects the browser here when the user
finishes (or abandons) the flow, and the page immediately bounces the browser on
into the app via the real deep link.

They were originally served from Supabase Edge Functions, but Supabase rewrites
`text/html` responses to `text/plain` on the shared `*.supabase.co` domain unless
a paid Custom Domain add-on is used (see
https://supabase.com/docs/guides/functions/limits). GitHub Pages has no such
restriction, so these pages moved here instead.

- `/identity-verification-redirect/` → `btxapp://identity-verification-return`
- `/stripe-connect-redirect/` → `btxapp://stripe-connect-return`
- `/billing-portal-return/` → `btxapp://billing-portal-return`
