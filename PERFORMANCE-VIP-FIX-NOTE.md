# Performance + VIP Fix

## Render Mini App copy
- `public/index.html`: VIP users bypass all ads and unlock directly.
- `public/index.html`: thumbnails use lazy loading, fixed dimensions, and lighter offscreen rendering.
- `public/assets/premium-video-logo.webp`: resized/compressed for its actual display size.
- `bot.js`: tokenless `/api/ad-complete` is accepted only when the user has an active VIP subscription; normal users still require the ad token.
- Successful direct delivery returns `chatUrl` instead of forcing the old redirect response.

Existing admin/bot/database systems are otherwise preserved.

## Deploy
If Render is connected to GitHub, push the changed files:

```bash
git add .
git commit -m "Optimize Mini App and fix VIP ad-free unlock"
git push origin main
```

Render will deploy the new commit automatically if auto-deploy is enabled.
