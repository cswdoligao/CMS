CSWDO CASE MANAGEMENT SYSTEM — SPLIT PORTALS

Files
- index.html: Staff Portal (Social Workers and CSWD Officer)
- admin.html: Administrator Portal
- supabase/migrations/: SQL migration for admin module
- supabase/functions/admin-staff-account/: secure account-management Edge Function

GitHub Pages
1. Put index.html and admin.html in the repository root.
2. Enable GitHub Pages from main branch / root.
3. Staff URL: https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
4. Admin URL: https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/admin.html

Supabase
- Both portals use the same Supabase project and Authentication.
- Apply the required SQL migrations in order, including the earlier initial schema and case-team migration before the admin migration.
- Deploy the admin-staff-account Edge Function separately using Supabase CLI.
- Set secrets in Supabase only. Never commit a service-role key or place it in either HTML file.

Security notes
- The portal redirect is a user-interface safeguard, not the security boundary. Keep RLS policies enabled and tested; Edge Function must independently verify the caller is an active admin.
- Social Worker and CSWD Officer access is still enforced by Supabase RLS.
- Both portals currently sign in with email and password. Username-or-email login is NOT implemented in this package; it requires a secure username lookup/authentication endpoint.
- Do not enter real client information until all RLS policies, role access, backups, and account provisioning have been tested.
