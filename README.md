# Astro + ACSS 4.x Starter

A minimalist, high-performance Astro starter template powered by **Automatic.css (ACSS) 4.x** design tokens, strict **BEM** CSS architecture, and **CSS logical properties**—with zero runtime overhead.

---

## Highlights

- **Fluid Mathematical Scalability**: Fully fluid typography and spacing curves powered by native ACSS 4.x CSS variables (`--space-xs` through `--space-xxl`, bridge scales, and fluid clamp formulas).
- **Modern Minimalist Dark Theme**: Sleek obsidian and carbon surfaces, high-contrast monochrome CTAs, and refined hairline borders using `oklch` color spaces and CSS `color-mix()`.
- **Self-Hosted Variable Fonts (Fontsource)**:
  - **Headings & Body**: Inter Variable (`@fontsource-variable/inter`)
  - **Code & Technical Labels**: JetBrains Mono Variable (`@fontsource-variable/jetbrains-mono`)
  - Zero third-party network requests, zero layout shift, and instant local font delivery.
- **Strict BEM Methodology**: Scoped, maintainable component classes (`.c-block__element--modifier`) and layout wrappers (`.l-container`, `.l-section`).
- **100% CSS Logical Properties**: Flow-relative properties (`padding-block`, `margin-inline`, `inline-size`, `inset-block-start`) authored across all styles.
- **Zero Runtime CSS Overhead**: Plain, standards-compliant CSS bundled at build time with zero client runtime or JavaScript styling dependencies.

---

## Project Structure

```text
astro-acss-starter/
├── public/
│   ├── favicon.ico
│   └── favicon.svg
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro     # Core HTML shell & self-hosted Fontsource imports
│   ├── pages/
│   │   └── index.astro          # Showcase landing page demonstrating BEM & ACSS tokens
│   └── styles/
│       ├── global.css           # Theme base, resets, container/section layout rules
│       ├── reset.css            # Lightweight modern CSS reset
│       └── tokens.css           # ACSS 4.x design kit tokens (palette, spacing, typography)
├── astro.config.mjs             # Astro project configuration
├── package.json
└── tsconfig.json
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18.17.1 or higher)
- [npm](https://www.npmjs.com/) (or pnpm / yarn)

### Using as a Template

This repository is configured as a GitHub **Template Repository**, allowing you to spin up a new project with a clean git history.

#### Option A: Via GitHub Web Interface
1. Visit the [`gdcrosbie/astro-acss-starter`](https://github.com/gdcrosbie/astro-acss-starter) repository.
2. Click the green **"Use this template"** button and select **"Create a new repository"**.
3. Set your repository name, choose visibility, and click **"Create repository"**.
4. Clone your new project and install dependencies:
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   npm install
   ```

#### Option B: Via GitHub CLI (`gh`)
Create, configure visibility, and clone your new project in a single command. Replace `my-project` with your desired repository name, and swap `--public` for `--private` as needed:

```bash
# Public repository:
gh repo create my-project --template gdcrosbie/astro-acss-starter --public --clone

# Private repository:
gh repo create my-project --template gdcrosbie/astro-acss-starter --private --clone

cd my-project
npm install
```

#### Option C: Standard Clone
Alternatively, clone directly and specify your own project directory name instead of `my-project`:

```bash
git clone https://github.com/gdcrosbie/astro-acss-starter.git my-project
cd my-project
npm install
```

### Development Server

Start the local development server:

```bash
npm run dev
```

To run the dev server in the background:

```bash
npx astro dev --background
```

Manage background sessions with:
- `npx astro dev status`
- `npx astro dev logs`
- `npx astro dev stop`

### Building for Production

Compile static assets to the `dist/` directory:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

---

## Design System & Styling Conventions

### 1. Token Source (`src/styles/tokens.css`)
All styling is driven by custom properties exported from ACSS 4.x:
- **Spacing Scale**: `--space-xs` through `--space-xxl` (step ends at `xxl`).
- **Bridge Spacing**: Responsive pairs such as `--space-xl-to-m`, `--space-l-to-xs`, `--space-xxl-to-m`.
- **Section Spacing**: `--section-space-xs` through `--section-space-xxl` (e.g. `padding-block: var(--section-space-m);`).
- **Layout Alignment**:
  - Container: `max-inline-size: var(--content-width); margin-inline: auto; padding-inline: var(--gutter);`
  - Grid Gaps: `gap: var(--grid-gap, var(--space-m));`
- **Colors & Transparency**:
  - Palette families: `--primary`, `--base`, `--secondary`, `--accent`, `--neutral`
  - Translucency: Authored using native `color-mix()` (e.g., `color-mix(in oklch, var(--white) 12%, transparent)`).
- **Radius**: Authored using `border-radius: var(--radius);` (`6px` default geometric radius) or `var(--radius-50)`.

### 2. Typography Rules
- **Headings & Body**: `--font-heading` and `--font-body` resolve to `Inter Variable` with `-0.025em` tracking for headings.
- **Monospace Elements**: `--font-mono` resolves to `JetBrains Mono Variable` for badges, tags, and inline `<code>`.

### 3. CSS Logical Properties
Always author flow-relative logical properties instead of physical dimensions:
- **Padding**: `padding-block`, `padding-inline` (never `padding-top/bottom/left/right`)
- **Margins**: `margin-block`, `margin-inline` (never `margin-top/bottom/left/right`)
- **Dimensions**: `inline-size`, `max-inline-size`, `block-size`, `min-block-size`
- **Borders**: `border-block-start`, `border-block-end`, `border-inline-start`, `border-inline-end`
- **Positioning**: `inset-block-start`, `inset-inline-start`, `inset`

---

## License

MIT License. Feel free to use this template for personal or commercial projects.
