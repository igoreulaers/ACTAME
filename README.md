# ACTAME project website

Source for the ACTAME project site — **Arctic Conservation Tool for Area-based
Measures and Ecosystems**, the joint PAME/CAFF project (2025–2027) developing a
pan-Arctic area-based conservation planning tool, led by the Norwegian Polar
Institute.

Built with [Quarto](https://quarto.org/), rendered and deployed to GitHub Pages
by GitHub Actions on every push to `main`.

**Live site:** <https://igoreulaers.github.io/ACTAME/>

## Getting it live (one-time)

1. Create an empty repository on GitHub named **`ACTAME`** (no README, no
   `.gitignore` — this folder already has them).
2. Push this folder:

   ```bash
   git remote add origin git@github.com:igoreulaers/ACTAME.git
   git branch -M main
   git push -u origin main
   ```

3. In the repository on GitHub: **Settings → Pages → Build and deployment →
   Source: GitHub Actions**. That is the only setting that needs changing.
4. The `Render and publish site` workflow runs on the push and the site appears
   at <https://igoreulaers.github.io/ACTAME/> a minute or two later. Later
   pushes to `main` republish automatically.

If the repository ends up with a different name or owner, update `site-url` and
`repo-url` in `_quarto.yml` to match — those are the only two places the URL is
written down.

## Editing the site

| To change | Edit |
|---|---|
| Home page | `index.qmd` |
| Project background, approach, phases | `about.qmd` |
| The tools listing | `tools.yml` (content) / `tools.qmd` (page text) |
| Team, expert group, partner logos | `team.qmd` |
| Reports, meetings, publications, citation | `publications.qmd` |
| Contact, contributing, licensing | `contact.qmd` |
| Navigation, site title, footer | `_quarto.yml` |
| Colours, typography, card and hero styling | `styles.scss` |
| Images, logos, thumbnails, favicon | `assets/` |

Pages marked with a shaded **placeholder** note contain scaffolding to be
replaced as the project fills in — team members, outputs and partner logos.

### Adding a tool

The Tools page is generated from `tools.yml`. Add one entry and commit; the card
appears on the next build:

```yaml
- title: "Tool name"
  subtitle: "One line on what it is"
  description: >
    Two or three sentences on what it does and who it is for.
  path: "https://github.com/igoreulaers/REPO-NAME"   # repo, live app, or a page here
  image: assets/tool-placeholder.svg                 # optional thumbnail
  categories: [R package, Live, Phase 2]             # status + type tags
  date: "2026-01-01"                                 # used for sorting
  author: "Norwegian Polar Institute"                # optional
```

Use one status tag per entry — `Live`, `In development` or `Planned` — plus any
type or phase tags. Tags become the filter buttons on the page. A copyable
template is at the bottom of `tools.yml`.

Drop a thumbnail into `assets/` (SVG or PNG, roughly 300 × 160) or leave
`image` out for a text-only card.

## Working on it locally

Requires [Quarto](https://quarto.org/docs/get-started/) — R is *not* needed, as
no page executes code.

```bash
quarto preview     # live preview at localhost, reloads as you edit
quarto render      # build once into _site/
```

`_site/` and `.quarto/` are generated and git-ignored; the site published by
Actions is always built fresh from source.

## Licence

Website content: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) —
see `LICENSE`. Software listed on the site is licensed per repository; spatial
layers carry the licences of their original providers.
