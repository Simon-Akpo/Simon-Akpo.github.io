# Simon Akporowhe — Portfolio

Built with [Astro](https://astro.build) (static output, ships zero client-side
JS by default) and deployed to GitHub Pages via GitHub Actions.

## Run it locally

```bash
npm install
npm run dev       # http://localhost:4321
npm run build     # outputs to dist/
npm run preview   # preview the production build
```

## Adding your real screenshots

Every project image on the site is a styled placeholder ("Add screenshot" +
the expected file path) rendered by `src/components/ImageSlot.astro` until a
real file lands at that exact path — **no code changes needed**, it swaps in
automatically on the next build/deploy.

The predictive maintenance dissertation charts are already in place, copied
from `MSc-Dissertation-EquipmentFailurePrediction/outputs/figures/` in
Documents. Still outstanding:

| Section | File to add |
|---|---|
| Employee Attrition — Overview page screenshot | `public/images/projects/employee-attrition/overview.png` |
| Employee Attrition — Deep Dive page screenshot | `public/images/projects/employee-attrition/deep-dive.png` |
| Customer Support — dashboard screenshot | `public/images/projects/customer-support/dashboard.png` |

Filenames must match exactly (case-sensitive). Any image size works — these
three slots crop to a fixed aspect ratio via `object-fit: cover`, so export
screenshots reasonably large (1600px+ wide) for a sharp result. (The chart
images use `object-fit: contain` instead, since cropping a chart can cut off
axis labels.)

The gallery captions/order/aspect-ratios for the dissertation case study are
editable in `src/pages/projects/predictive-maintenance.astro` (the `gallery`
array at the top) if you want to reorder, swap in different charts, or add
more than 8.

## Other things you'll likely want to personalize

- `public/images/og-cover.svg` — the placeholder social-share image (shown
  when the link is pasted into LinkedIn/Slack/etc). It's a generated SVG;
  swap it for a designed 1200×630 PNG/JPG at the same path if you want a
  polished share card, and update the `image` prop path in
  `src/layouts/Layout.astro` if you rename the file.
- LinkedIn URL is set in `src/components/Footer.astro` and
  `src/components/Contact.astro`.
- The case study currently emphasizes scope (8 algorithms, 3.9M+ records, 10
  years) rather than a specific accuracy number. Real results are documented
  in `MSc-Dissertation-EquipmentFailurePrediction/outputs/report.md`
  (LightGBM: test F1 0.859, ROC AUC 0.969, 91.2% accuracy) — add one to
  `src/pages/projects/predictive-maintenance.astro` if you want to feature it.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the
site with Astro and publishes it to GitHub Pages. See the setup notes shared
alongside this repo for the one-time manual step (enabling Pages in the repo
settings).
