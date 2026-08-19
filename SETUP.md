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

Customer flow:
- Form 1 asks for phone number only.
- If the phone already exists in `customers`, the returning customer skips the profile form and can book immediately.
- If the phone is new, Form 2 asks for name, email and occupation (`student`, `job`, or `business`).
- The new customer profile is saved once, so future visits need only the phone number.

No OTP is used, per the MVP requirement.

Site customization:
Every public page calls `loadSiteSettings()` on startup. That calls `applySiteSettings()`, which applies the brand, logo, colors, font, text, layout, favicon, custom CSS and custom HTML at runtime.
