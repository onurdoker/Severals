# goit-js-hw-09

A small, multi‑page vanilla JavaScript project built with Vite. It includes:

- An image Gallery page using SimpleLightbox (01-gallery.html)
- A Feedback Form page that persists state to localStorage (02-form.html)
- An Index page that links to the above demos (index.html)

This repository is based on a GoIT vanilla app template, adapted for Homework 9.


## Stack

- Language: JavaScript (ES Modules), HTML5, CSS3
- Build tool: Vite 6
- PostCSS: postcss, postcss-sort-media-queries
- Vite plugins: vite-plugin-html-inject, vite-plugin-full-reload
- UI library used in gallery: simplelightbox
- Package manager: npm (package-lock.json present)


## Requirements

- Node.js LTS installed (recommended). Vite 6 typically requires Node 18+. TODO: verify the exact supported Node version for your environment.
- npm (bundled with Node.js)


## Getting started

1. Install dependencies
   - npm install
2. Start the dev server
   - npm run dev
   - Open http://localhost:5173 (default Vite port). The page reloads automatically on changes.
3. Build for production
   - npm run build
4. Preview the production build locally
   - npm run preview


## Scripts

- dev — start Vite dev server
- build — build production assets with a base path suitable for GitHub Pages
- preview — serve the built assets locally for preview/testing

From package.json:

```
{
  "scripts": {
    "dev": "vite",
    "build": "vite build --base=/goit-js-hw-09/",
    "preview": "vite preview"
  }
}
```


## Entry points and app pages

Vite is configured to treat every HTML file in src/ as an entry (see vite.config.js):

- src/index.html — landing page linking to examples
- src/01-gallery.html — image gallery using SimpleLightbox
  - JS: src/js/01-gallery.js
  - CSS: src/css/gallery.css
- src/02-form.html — feedback form with localStorage persistence
  - JS: src/js/02-form.js
  - CSS: src/css/form.css

Shared assets/styles live under:

- src/css — page styles (e.g., index.css)
- src/img — static images (if any)
- src/js — page scripts
- src/partials — HTML partials (if used)


## Project structure (abridged)

- README.md
- package.json / package-lock.json
- vite.config.js
- src/
  - index.html
  - 01-gallery.html
  - 02-form.html
  - css/
    - index.css
    - gallery.css
    - form.css
  - js/
    - 01-gallery.js
    - 02-form.js
  - img/
  - partials/
- assets/ (documentation images from the original template)


## Configuration notes

- Vite root is set to src/ and output to dist/ (see vite.config.js)
- Multiple HTML entries are auto‑discovered via glob (./src/*.html)
- The build output base is set to /goit-js-hw-09/ which matches a GitHub Pages deployment under the repository name

Relevant vite.config.js bits:

```
export default defineConfig(({ command }) => ({
  root: 'src',
  build: {
    rollupOptions: {
      input: glob.sync('./src/*.html')
    },
    outDir: '../dist'
  },
  plugins: [injectHTML(), FullReload(['./src/**/**.html'])]
}));
```


## Environment variables

- None are required for local development or build at this time.
- TODO: If you introduce environment‑specific settings, prefer using Vite env files (.env, .env.development, .env.production) with prefixes like VITE_.


## Testing

- There are currently no automated tests in this repository.
- TODO: Add tests (e.g., using Vitest + @testing-library) and document how to run them.


## Deployment (GitHub Pages)

This project is preconfigured for GitHub Pages via the build base path.

1. Ensure the build script in package.json uses the repo name as base:
   - "build": "vite build --base=/goit-js-hw-09/"
2. Build and push the production files to a gh-pages branch using your preferred method, or set up a GitHub Action.
   - Template repos often use a workflow at .github/workflows/deploy.yml. If it doesn’t exist here, you can add one. TODO: Add/verify CI workflow for automated deploys.
3. In the GitHub repo, go to Settings → Pages and set the source to the gh-pages branch (root folder) if using that flow.
4. Your site will be available at: https://<your-username>.github.io/goit-js-hw-09/

Troubleshooting a blank page on GitHub Pages:

- Check the browser console for 404 errors on JS/CSS. This usually means the base path is incorrect. The base must match "/<REPO_NAME>/".


## License

- License: ISC (as declared in package.json)
- TODO: Add a LICENSE file to the repository root for clarity.


## Acknowledgements

This project was scaffolded from the GoIT vanilla app template and adapted for Homework 9. Thanks to the authors and maintainers of Vite and the listed plugins/libraries.
