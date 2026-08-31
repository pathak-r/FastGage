# Structra landing page

Static page for `fastgage.co/structra/`. Also fills the **Marketing URL** field in
App Store Connect.

Deploy: copy this folder’s `index.html` and `assets/` into `structra/` (GitHub Pages
serves `/structra/`). No build step, no dependencies, no framework.

```
site/
  index.html                         single file — markup, CSS and JS inline
  assets/screen-*.jpg                app screens (light iOS UI)
  assets/og.png                      1200×630 link preview
  assets/structra-sample-report.pdf  the downloadable sample
```

Copy is written in plain English for UAE readers (short sentences, concrete words,
keep local terms like handover / snagging / villa).

Visual direction: light iOS grouped background (`#F2F2F7`), system-blue CTAs
(`#007AFF`). Brand ochre on the wordmark rule and eyebrows. Cormorant Garamond
for titles; system sans for UI. Hero uses a washed `evidence-crack.jpg` plane
plus grain. The boxed-defect animation sits after the three steps.

The page is mostly **how it works**, with Get the app and a sample report.
Screens are regenerated mockups from the app theme tokens. The sample PDF uses
fictional property data — stated on the PDF itself.

## Before it goes live

- The `og:*` and `twitter:*` URLs are absolute and hardcoded to
  `https://www.fastgage.co/structra/`. If the path differs, change them — otherwise
  WhatsApp and LinkedIn will fetch a 404 and the link will paste bare.
- `assets/og.png` must be publicly reachable at that path for the rich preview card.
- Footer privacy link points at `/structra/privacy/`.
- Test the preview with [WhatsApp's link debugger](https://developers.facebook.com/tools/debug/)
  after deploying; both platforms cache aggressively, so get it right before you share it.

## CTAs

Primary: [App Store](https://apps.apple.com/in/app/structra-inspect/id6795109088)
Secondary: `assets/structra-sample-report.pdf`

## Regenerating assets

From the Structra app repo (not this site):

```bash
cd ../Structra/appstore/generator
python3 screens.py       # app screens from the theme tokens
python3 site_assets.py   # writes to appstore/site/assets when run from generator/
```

`site_assets.py` mirrors `lib/report-pdf.ts` — same markup, same CSS, same severity
colours — so the sample PDF stays in step with what the app actually exports. Copy
the JPGs and PDF into this folder’s `assets/` (and into `structra/assets/` for
GitHub Pages).
