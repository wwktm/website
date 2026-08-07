# wwktm-website

Source for [wwktm.com](https://wwktm.com) — the Web Weekend Kathmandu community site.
A [Hugo](https://gohugo.io) static site.

## What's here

| Path | What it is |
|------|-----------|
| `/` | **wwktm landing page** — community intro, our three events (AI Conf, BarCamp, Tech Kura Kani), timeline, newsletter. Lives at `themes/wwktm/layouts/index.html` as a fully self-contained HTML document (Tailwind via CDN, no Hugo partials — it intentionally bypasses `baseof.html` by not defining any blocks). |
| `/2018/` | Web Weekend Kathmandu 2018 conference site (archived, don't touch) |
| `/2019/` | Web Weekend Kathmandu 2019 conference site (archived, don't touch) |
| `/2023/` | wwktm 2023 / call-for-papers content (archived) |

Static assets for the landing page (logos: `wwktm.svg`, `aiconf.svg`, `barcamp.svg`, `TKK.svg`, `favicon.png`) live in `static/` and are referenced with absolute paths (`/wwktm.svg`, …).

Redirects are managed in `static/_redirects` (Netlify).

## Development

```bash
brew install hugo
hugo serve        # preview at http://localhost:1313
hugo              # build to public/
```

Note: `config.toml` sets `[security] allowContent = ['.*']` — modern Hugo (v0.146+)
blocks raw HTML content files by default, and the archived 2018/2019 sections are HTML.
Don't remove that setting.

## Editing the landing page

The canonical copy of the landing page also exists in the `ai-confg` repo at
`wwktm/index.html` (used for design iteration). If you edit one, sync the other —
when copying into this repo, convert asset paths to absolute (`src="/wwktm.svg"` etc.)
and the favicon to `/favicon.png`.

## Deploy

Push to the connected branch; Netlify builds with `hugo` and publishes `public/`,
applying `static/_redirects`.
