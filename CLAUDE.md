# Project context for Claude

## What this is

A single-page artist portfolio site for **Maria Aguilera** (Cristian's mom), who is a finalist (or applicant — confirm) in **The People's Artist 2026** competition (presented by Johnny Depp, supporting The Art of Elysium).

**GitHub repo:** https://github.com/lunthra-com/maria-aguilera-art

The site's #1 job is converting visitors into **daily voters** for the contest, not just showcasing art.

## Critical timeline

- **Voting opens:** May 4, 2026
- **Top-20 round:** May 4 – May 14
- **Top-15 round:** May 14 – May 21
- **Finals:** July 3 – July 9 (votes reset)
- **Grand prize announced:** on/before August 6, 2026
- **Today's reference:** site work began May 2, 2026 (~2 days before voting opened)

Public votes once/day, free. Winner is decided entirely by public vote. Prize: $25K + Artforum feature + LA salon showcase.

## Stack & deployment

- Plain HTML + CSS, no framework, no build step
- Hosted on **Netlify free tier** with **continuous deploy from GitHub `main` branch**
- Domain via **Cloudflare Registrar** (~$10/yr, suggested `firstnamelastname.art` or `.com`)
- See `DEPLOY.md` for the full setup walkthrough

## Design decisions already made

- **White background, charcoal accents** (mom's call — "the art will have the color")
- Cormorant Garamond serif headings, Inter sans-serif body
- Warm gallery → modern white gallery (Chelsea/Marfa feel, not cottage)
- Mobile-first; most votes will come from phones via shared links
- Single-page, scrolling layout — no nav clicks between content and the vote button
- Vote CTA appears 3 times: hero area, sticky-feeling vote bar, footer
- Live countdown to August 6 voting close
- One-tap share buttons (text/email/Facebook/X/copy) with pre-written messages

## Repo layout

```
.
├── index.html         # the entire site (single file)
├── netlify.toml       # cache + security headers, no build step
├── README.md          # GitHub project description
├── DEPLOY.md          # GitHub → Netlify walkthrough
├── CLAUDE.md          # this file — context for AI sessions
├── .gitignore         # OS junk + raw image files
└── images/
    └── README.txt     # filename conventions
```

## Placeholders that still need real values

In `index.html`, find/replace these tokens (each appears multiple times):

| Token            | What to put there                                          |
| ---------------- | ---------------------------------------------------------- |
| `[ARTIST NAME]`  | Mom's full name as she signs work                          |
| `[FIRST NAME]`   | Just first name                                            |
| `[CITY, STATE]`  | Where she paints                                           |
| `[VOTE_URL]`     | Direct vote link on peoplesartist.org (waiting on this)    |
| `[SITE_URL]`     | Final live URL — fill in after first deploy                |
| `[EMAIL]`        | Contact email                                              |
| `[Painting Title 1..6]` | Titles + medium/size lines for the 6 gallery slots  |
| `[OPENING PARAGRAPH]` etc. | 3-paragraph artist bio                          |

Image files needed in `images/`: `headshot.jpg`, `painting-1.jpg`...`painting-6.jpg`, `share-card.jpg` (1200×630).

## Status

- [x] Site shell built (white gallery aesthetic)
- [x] Vote CTAs, countdown, share row, gallery grid, about section, footer
- [x] Repo files (.gitignore, netlify.toml, README, DEPLOY guide)
- [ ] Real artist name, bio, vote URL, images
- [ ] GitHub repo created and first push
- [ ] Netlify connected to repo
- [ ] Custom domain bought + pointed at Netlify
- [ ] Launch day group-text + social posts drafted
- [ ] Daily-reminder cadence set up

## Next actions (priority order)

1. Get content from mom (name, vote URL, bio, images) → fill placeholders
2. Create GitHub repo + connect Netlify (DEPLOY.md Steps 2–3) — can do with placeholders to test pipeline
3. Buy domain at Cloudflare, point at Netlify
4. Draft launch-day texts/social posts for May 4
5. Set up daily-reminder ritual (group chat, calendar reminder)

## Conventions for editing

- Edit `index.html` directly — no preprocessor, what you see is what ships
- Adding a painting = duplicate one `.piece` block, swap `src` + title + medium line
- Push to `main` → Netlify rebuilds in ~30 seconds
- Keep image files small (long edge ~1600px, under 500 KB each — squoosh.app for compression)
- Don't commit raw `.psd`/`.tiff`/`.RAF` — `.gitignore` already excludes them
