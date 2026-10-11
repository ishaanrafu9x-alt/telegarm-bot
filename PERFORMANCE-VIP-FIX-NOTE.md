# Performance + VIP Fix

## Cloudflare Mini App
- `public/index.html`: VIP users bypass all ads and unlock directly through `/api/ad-complete`.
- `public/index.html`: thumbnails use lazy loading, fixed dimensions, and lighter offscreen rendering.
- `public/assets/premium-video-logo.webp`: resized/compressed for its actual display size.
- `worker.js`: thumbnail responses are resized to 640x360 and delivered as AVIF/WebP when supported, with Cloudflare edge caching. If transformation is unavailable, the Worker falls back to the original thumbnail.
- `worker.js`: successful direct video delivery no longer forces a bot-chat redirect response; it returns `chatUrl` so the Mini App can try the Telegram handoff and show a manual fallback button.
- Existing Firestore collections, Telegram file_ids, admin panel, posting/scheduling, auto-delete bookkeeping, and bot token variables are preserved.

## Deploy
Run from this project folder:

```bash
npm install
npx wrangler deploy
```

Do not delete/reset the existing Firebase project or collections.
