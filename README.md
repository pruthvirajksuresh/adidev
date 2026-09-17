# Adidev Pharma

A responsive, static company website with a green-and-ivory design, original CSS artwork, accessible mobile navigation, company values, partnership information, and expandable FAQs.

Contact details and the product catalogue are deliberately marked as coming soon. Replace the introductory brand copy with approved company information before adding specific products, certifications, or business claims.

## Local development

Requires Node.js 22 or newer. No application dependencies are needed.

```sh
npm run dev
```

Visit http://127.0.0.1:5173/.

```sh
npm run check
npm run build
```

The build creates `dist/`, containing only public website files. All asset paths are relative so the website works at a GitHub Pages repository subpath.

## Publish on GitHub Pages

The local repository is initialized on `main`. A remote repository has **not** been created, and the website is **not yet published**.

With the [GitHub CLI](https://cli.github.com/) installed and authenticated:

```sh
gh auth login
gh repo create adidev --public --source=. --remote=origin

gh api --method POST repos/pruthvirajksuresh/adidev/pages -f build_type=workflow
git push -u origin main
```

Alternatively:

1. Create an empty public repository named `adidev` under your GitHub account. Do not initialize it with a README, license, or `.gitignore`.
2. Add the remote and push the local commit:

   ```sh
   git remote add origin https://github.com/pruthvirajksuresh/adidev.git
   git push -u origin main
   ```

3. In the repository, open **Settings → Pages → Source** and select **GitHub Actions**.
4. Open **Actions → Deploy website to GitHub Pages → Run workflow** if the first run failed before Pages was enabled.

After deployment succeeds, the expected address is `https://pruthvirajksuresh.github.io/adidev/`. Subsequent pushes to `main` deploy automatically.

The workflow follows [GitHub’s custom Pages workflow documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

## Editing the site

- `index.html`: company text, sections, navigation, and metadata.
- `assets/style.css`: colors, typography, CSS artwork, and responsive layouts.
- `assets/site.js`: mobile menu and current footer year.
- `.github/workflows/pages.yml`: build and deployment workflow.

The website has no backend, tracking, or form submissions. Fonts are loaded from Google Fonts, with local sans-serif fallbacks.
