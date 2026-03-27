# scuacmg.com static website

This repository hosts a static GitHub Pages website for `scuacmg.com`.

## Why your previous "DNS check unsuccessful" happened

The most common issue is deployment source mismatch:

- GitHub Pages was set to **Deploy from branch**.
- But the selected branch/folder (`main / root`) did not exist or was not configured correctly.

This repository currently uses the `work` branch, so selecting `main / root` will fail until a `main` branch exists.

## Recommended deployment setup (most reliable)

Use **GitHub Actions** as the Pages source.

1. Go to **Repo Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push changes to `work` or `main`.
4. Wait for workflow **Deploy static site to GitHub Pages** to succeed.

## DNS setup for `scuacmg.com` (apex + alternate name)

To avoid `InvalidDNSError` and "both domain and alternate name are improperly configured", create **all** of these records:

### Apex domain (`scuacmg.com`)

- `A` record for host `@` → `185.199.108.153`
- `A` record for host `@` → `185.199.109.153`
- `A` record for host `@` → `185.199.110.153`
- `A` record for host `@` → `185.199.111.153`

### Alternate name (`www.scuacmg.com`)

- `CNAME` record for host `www` → `<your-github-username>.github.io`

## Critical DNS provider checks

- Ensure the domain is actually registered and not expired.
- If using Cloudflare, set records to **DNS only** (gray cloud), not proxied.
- Remove conflicting old records (`URL redirect`, old `A`, old `CNAME`, parked domain records).
- Keep TTL at default/auto while propagating.

## GitHub Pages settings

1. **Settings → Pages → Custom domain**: `scuacmg.com`
2. Save and wait for DNS to propagate.
3. Confirm both `scuacmg.com` and `www.scuacmg.com` resolve correctly.
4. Enable **Enforce HTTPS** after checks pass.

## Quick verification commands

Run these locally and verify they return values:

```bash
dig +short scuacmg.com A
dig +short www.scuacmg.com CNAME
```

If either command returns empty output, GitHub will show `InvalidDNSError`.


## Do I need to keep my computer on?

No. You do **not** need to keep your computer running.

- DNS records live at your **domain registrar/DNS provider** (for example Namecheap, Cloudflare, GoDaddy).
- Website hosting is handled by **GitHub Pages** on GitHub's servers.
- After records are saved and propagated, your site stays online 24/7 even when your laptop is off.

## Notes

- `CNAME` in repo root is set to `scuacmg.com`.
- Main page body is intentionally empty for now; only header/navigation is scaffolded.
