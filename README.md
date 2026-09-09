# Rose Cleaning

Marketing site for Rose Cleaning — a residential and commercial cleaning company
serving Toronto and the GTA.

## Contents

- `index.html` — the complete site. This is a single self-contained file: fonts,
  images, styles and scripts are all embedded, so it has no external
  dependencies and no build step.
- `.nojekyll` — tells GitHub Pages to serve the files as-is instead of running
  them through Jekyll.

## Before this goes live

Three things still need real values.

**1. The quote form does not deliver anything yet.** It posts to a placeholder:

```
action="https://formspree.io/f/YOUR_FORM_ID"
```

Replace that with a real endpoint or submissions are lost silently. Two options
that need no backend:

- **Formspree** — sign up at formspree.io, create a form, paste in the endpoint.
- **FormSubmit** — no signup; use `https://formsubmit.co/your@email.com` and
  confirm once by clicking the link sent on the first submission.

**2. The reviews are placeholder copy.** The six testimonials in the Kind words
section are illustrative, not real customers. Publishing invented testimonials
as genuine is deceptive advertising and is actionable under the Competition Act
in Canada. Replace them with real reviews before promoting the site.

**3. The headline figures are placeholders too** — `4.9`, `600+` reviews, `10+`
years, `12k+` cleans and `98%` rebook rate all came from the original design
template and are not measured numbers.

## Structure

Sections in order: hero, stats band, services, about, reviews, CTA, quote form,
footer. All quote buttons link to `#quote`.

## Editing

`index.html` is an exported design bundle: the page markup lives JSON-encoded
inside a `<script type="__bundler/template">` tag, and a runtime unpacks it on
load. Two consequences:

- Content edits are best made in the original design tool and re-exported over
  this file.
- The responsive layer added on top is a `<style>` block inside that template.
  Because the bundle styles every element inline, those rules need `!important`,
  and the runtime rewrites inline styles with a space after each colon — so
  attribute selectors must match `[style*="uppercase"]`, not
  `[style*="text-transform:uppercase"]`.

There is also no universal `box-sizing` reset in the bundle, so anything new
that combines `width`/`min-height` with padding should set `border-box` itself.

## Viewing it locally

Open `index.html` in a browser. That's the whole process.

## Deploying

Served by GitHub Pages from `main`. Pushing to `main` republishes it; a build
takes roughly 20–30 seconds.
