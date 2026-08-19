# Salon Booking MVP — Setup

1. Create a Supabase project.
2. Open SQL Editor and run `schema.sql`.
3. Create a Storage bucket named `site-assets` (public if you want direct image URLs).
4. Create an Auth user for the salon owner.
5. Insert that user's UUID into `admins`:
   `insert into admins(user_id,is_admin) values ('AUTH_USER_UUID', true);`
6. In every HTML file replace:
   - `YOUR_SUPABASE_URL`
   - `YOUR_SUPABASE_ANON_KEY`
7. Change `CHANGE_ME_ADMIN_PASSCODE` in `admin.html`.
8. Deploy the folder to GitHub Pages.
9. Add your own services, hours and branding from `admin.html`.

Important MVP note:
The supplied prompt specifies phone-number booking but does not define an OTP/authentication flow. This implementation therefore uses the `customers` table for customer identification and uses Supabase Auth only for the admin gate. Before production use, add a real phone OTP/auth flow and tighten customer/booking RLS so users cannot enumerate other customers or bookings.

Site customization:
Every public page calls `loadSiteSettings()` on startup. That calls `applySiteSettings()`, which applies the brand, logo, colors, font, text, layout, favicon, custom CSS and custom HTML at runtime.
