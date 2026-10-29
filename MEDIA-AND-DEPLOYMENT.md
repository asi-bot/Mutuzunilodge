# Mutuzuni media integration and staging checklist

## Required media upload

Extract `mutuzuni-media-assets.zip` and upload **the files inside its `assets/` folder** to `public/assets/` on GitHub. Do not upload only the ZIP; the website needs the individual files.

Required paths:
- `public/assets/waterfall-hero.mp4` — homepage background video
- `public/assets/waterfall-trail.mp4` — trail section background video
- `public/assets/waterfall-still.jpg` — video fallback
- `public/assets/lodge-pool.jpg` — temporary image; verify subject before public release
- `public/assets/lodge-nature.jpg` — temporary image; verify subject before public release
- `public/assets/lodge-landscape.jpg` — temporary image; verify subject before public release
- `public/assets/logo-option-3.png` — selected full logo artwork

The small `public/assets/tree-emblem.svg` is a temporary navigation emblem, not a faithful reproduction of the selected logo. Replace with an approved transparent/cropped logo asset when available.

## Before deploying

1. Verify all media paths return HTTP 200 and videos play muted inline on mobile.
2. Review copyright, people/privacy consent, and whether each photo represents the lodge.
3. Confirm opening hours, trail safety, camping status and corporate programme activities.
4. Run the booking calculator on mobile and desktop; it only prepares WhatsApp enquiries, not confirmed reservations.
5. Keep any private admin unexposed until a real backend, server-side authentication and booking persistence exist.

## Fly.io

`fly.toml` is a **template**. Confirm an available Fly app name and account first. Fly.io authorisation on GitHub does not itself mean this project is deployed.

From a developer machine with Fly CLI and an authenticated account:

```sh
fly auth login
fly apps create <your-available-app-name>
# Update app in fly.toml to the created name
fly deploy
fly status
```

The container uses Nginx on port 8080. Do not claim the site is live until the deployed URL is tested.

## Next build

- Secure server-side admin with roles and audit log
- Database-backed corporate enquiries, visitor bookings and 200-person daily capacity checks
- Quote workflow and corporate programme scheduling
- Media management and actual client-approved logo integration
