# Maria Aguilera — Artist Portfolio

Single-page portfolio site supporting Maria Aguilera's campaign in **The People's Artist 2026** (presented by Johnny Depp, supporting The Art of Elysium).

**Live site:** https://[your-site].netlify.app
**Vote daily:** [vote URL on peoplesartist.org]
**Voting window:** May 4 – August 6, 2026

## Stack

- Plain HTML + CSS (no framework, no build step)
- Hosted on **Netlify** (continuous deploy from `main` branch)
- Domain via **Cloudflare Registrar**
- Total cost: ~$10/year (domain only)

## Repo layout

```
.
├── index.html         # the entire site (single page)
├── netlify.toml       # Netlify config (cache + security headers)
├── images/            # artwork photos + headshot + share card
│   └── README.txt     # filename conventions
├── DEPLOY.md          # step-by-step deploy guide
└── README.md          # this file
```

## Editing

Open `index.html` in any text editor. Search for `[ARTIST NAME]`, `[VOTE_URL]`, `[FIRST NAME]`, etc. — those are the placeholders to fill in.

To add a new painting: drop the image into `images/` and copy one of the `.piece` blocks in `index.html`.

Push to `main` and Netlify rebuilds in ~30 seconds.

## Deploy

See [DEPLOY.md](./DEPLOY.md).
