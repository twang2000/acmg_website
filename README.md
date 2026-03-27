# scuacmg.com static website

This repository hosts a static GitHub Pages website for `scuacmg.com`.

## Why your previous "DNS check unsuccessful" happened

The most common issue is deployment source mismatch:

- GitHub Pages was set to **Deploy from branch**
- But the selected branch/folder (`main / root`) did not exist or was not configured correctly.

This repository currently uses the `work` branch, so selecting `main / root` will fail until a `main` branch exists.

## Recommended deployment setup (most reliable)

Use **GitHub Actions** as the Pages source.

1. Go to **Repo Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push changes to `work` or `main`.
4. Wait for workflow **Deploy static site to GitHub Pages** to succeed.

## DNS setup for `scuacmg.com`

At your DNS provider, set these records:

- `A` record for host `@` → `185.199.108.153`
- `A` record for host `@` → `185.199.109.153`
- `A` record for host `@` → `185.199.110.153`
- `A` record for host `@` → `185.199.111.153`
- `CNAME` record for host `www` → `<your-github-username>.github.io`

Then in GitHub Pages custom domain, set `scuacmg.com` and enable **Enforce HTTPS** after DNS propagates.

## Notes

- `CNAME` in repo root is already set to `scuacmg.com`.
- Main page body is intentionally empty for now; only header/navigation is scaffolded.
