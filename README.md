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

Every project image on the site is currently a styled placeholder ("Add
screenshot" + the expected file path) rendered by `src/components/ImageSlot.astro`.
**You don't need to touch any code** — just drop a file at the exact path
below and it replaces the placeholder automatically on the next build/deploy.

| Section | File to add |
|---|---|
| Predictive maintenance — homepage preview | `public/images/projects/predictive-maintenance/hero-chart.png` |
| Predictive maintenance — gallery (case study page) | `public/images/projects/predictive-maintenance/01-data-pipeline.png` |
| | `public/images/projects/predictive-maintenance/02-model-comparison.png` |
| | `public/images/projects/predictive-maintenance/03-feature-importance.png` |
| | `public/images/projects/predictive-maintenance/04-confusion-matrix.png` |
| | `public/images/projects/predictive-maintenance/05-roc-curves.png` |
| | `public/images/projects/predictive-maintenance/06-precision-recall.png` |
| | `public/images/projects/predictive-maintenance/07-failure-timeline.png` |
| | `public/images/projects/predictive-maintenance/08-shap-summary.png` |
| Employee Attrition — Overview page screenshot | `public/images/projects/employee-attrition/overview.png` |
| Employee Attrition — Deep Dive page screenshot | `public/images/projects/employee-attrition/deep-dive.png` |
| Customer Support — dashboard screenshot | `public/images/projects/customer-support/dashboard.png` |

Filenames must match exactly (case-sensitive). Any image size works — each
slot crops to a fixed aspect ratio via CSS `object-fit: cover`, so export
screenshots reasonably large (1600px+ wide) for a sharp result.

The gallery captions/order for the dissertation case study are editable in
`src/pages/projects/predictive-maintenance.astro` (the `gallery` array at the
top) if you want to reorder, rename, or add more than 8 charts.

## Other things you'll likely want to personalize

- `public/images/og-cover.svg` — the placeholder social-share image (shown
  when the link is pasted into LinkedIn/Slack/etc). It's a generated SVG;
  swap it for a designed 1200×630 PNG/JPG at the same path if you want a
  polished share card, and update the `image` prop path in
  `src/layouts/Layout.astro` if you rename the file.
- LinkedIn URL is set in `src/components/Footer.astro` and
  `src/components/Contact.astro`.
- Dissertation result metrics (accuracy, best model, etc.) weren't specified
  when this site was built — the case study currently emphasizes scope (8
  algorithms, 3.9M+ records, 10 years) rather than a specific accuracy
  number. Add one in `src/pages/projects/predictive-maintenance.astro` if
  you want to feature it.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the
site with Astro and publishes it to GitHub Pages. See the setup notes shared
alongside this repo for the one-time manual step (enabling Pages in the repo
settings).
