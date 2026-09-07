# Project Instructions & Agent Guidelines (ACSS 4.x)

## 1. Project Context & Boundaries

> [!IMPORTANT]
> **This is a standalone Astro project — NOT a WordPress / Etch builder environment.**
> - Do **not** look for or invoke Etch tools (`etch-connector`, `nibwp-*`, `novamira-*`, `scwp-acss-mcp`).
> - There is no WordPress database, live builder tab, or per-element Etch styles layer here.
> - Component styling belongs inside `.astro` component `<style>` blocks or standard CSS files in `src/styles/`.

---

## 2. Development & Dev Server

When starting the dev server, use background mode:
```bash
astro dev --background
```
Manage the background server with:
- `astro dev status`
- `astro dev logs`
- `astro dev stop`

---

## 3. Styling & CSS Architecture (Astro + ACSS 4.x)

This project consumes an **Automatic.css (ACSS) 4.x** design kit exported from SchemaWP (`etch-design-kits.com`).

### Core Rules:
- **Token Source**: `src/styles/tokens.css` (imported via `src/styles/global.css`).
- **Methodology**: Strict BEM methodology (`.c-block`, `.c-block__element`, `.c-block--modifier`).
- **No Utility Frameworks**: No Tailwind CSS, no utility-class soup, no inline `style=""` attributes.
- **Component Styling**: Write clean CSS in component `<style>` blocks using native ACSS custom properties.

### Mandatory: CSS Logical Properties
Always author flow-relative logical properties instead of physical dimensions:
- **Padding**: Use `padding-block` and `padding-inline` (never `padding-top/bottom/left/right`).
- **Margins**: Use `margin-block` and `margin-inline` (never `margin-top/bottom/left/right`).
- **Sizing**: Use `max-inline-size`, `inline-size`, `block-size`, `min-block-size` where suitable.
- **Positioning**: Use `inset`, `inset-block-start`, `inset-block-end`, `inset-inline-start`, `inset-inline-end` (never physical `top/bottom/left/right`).
- **Borders & Dividers**: Use `border-block-start`, `border-block-end`, `border-inline-start`, `border-inline-end`.

### ACSS 4.x Token Verification & Constraints:
- **Discover, Don't Guess**: **Never invent or recall tokens from memory.** Always inspect `src/styles/tokens.css` to verify that a token exists before using it in a `var()`.
- **Spacing Scale**: `--space-xs` through `--space-xxl` (the largest step is `xxl`, NOT `2xl`; sub-xs steps like `3xs`/`2xs` do not exist in default 4.0 scale). Spacing, section-spacing, text sizes, and button sizes all end in `xxl`. Only icons use `2xl`.
  - Bridge variables: `--space-{large}-to-{small}` (e.g. `--space-xl-to-m`, `--space-l-to-xs`, `--space-xxl-to-m`).
- **Section Spacing**: `padding-block: var(--section-space-m);` (scale is `--section-space-xs` through `--section-space-xxl`; also bridge variables like `--section-space-l-to-m`).
- **Layout & Section Alignment**:
  - Container: `max-inline-size: var(--content-width); margin-inline: auto; padding-inline: var(--gutter);`
  - Grid & Component Gaps: `gap: var(--grid-gap, var(--space-m));`
  - Contextual Gaps: `--content-gap: var(--space-m);`, `--container-gap: var(--space-xl);`
- **Colors & Shades**:
  - Palette families: `--primary`, `--base`, `--secondary`, `--accent`, `--neutral`
  - Shades: `-hover`, `-light`, `-semi-light`, `-semi-dark`, `-dark`, `-ultra-light`, `-ultra-dark`.
  - Base neutrals: `--white`, `--black` (defined with `light-dark()`).
  - Contextual tokens: `--text-light`, `--text-light-muted`, `--text-dark`, `--text-dark-muted`, `--bg-light`, `--bg-dark`, `--bg-ultra-light`, `--bg-ultra-dark`. No `--text-primary` or `--text-muted`.
- **Transparency**: Never use `--*-trans-*`. Use CSS `color-mix()`:
  ```css
  color-mix(in oklch, var(--primary) 15%, transparent)
  ```
- **Radius**: Use `border-radius: var(--radius);` (ACSS 4.0 uses a single global radius token; also `--radius-50`, `--radius-circle`, `--radius-none`, `--radius-m`).
- **Borders & Dividers**: `--border`, `--border-light`, `--border-dark`, `--border-size`, `--border-color-dark`, `--border-color-light`, `--divider`.
- **Shadows**: `--box-shadow-1`, `--box-shadow-2`, `--box-shadow-3`.
- **Transitions**: `--transition`, `--transition-duration`, `--transition-timing`, `--transition-delay`.

---

## 4. Documentation References

Consult these guides before working on Astro features:
- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles](https://docs.astro.build/en/guides/styling/)
