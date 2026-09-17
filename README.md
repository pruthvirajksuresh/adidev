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

The repository is [pruthvirajksuresh/adidev](https://github.com/pruthvirajksuresh/adidev), with deployment from `main`.

Before the first deployment, open [Settings → Pages](https://github.com/pruthvirajksuresh/adidev/settings/pages) and select **GitHub Actions** under **Build and deployment → Source**. This creates the Pages site that the workflow needs. A `Get Pages site failed` / `Not Found` error at the configuration step means you should check this setting and the build job's `pages: read` permission.

With the [GitHub CLI](https://cli.github.com/) installed and authenticated:

```sh
gh auth login
# Run once if Pages has not been enabled in Settings:
gh api --method POST repos/pruthvirajksuresh/adidev/pages -f build_type=workflow
git push origin main
```

Alternatively:

1. In the repository, open **Settings → Pages → Source** and select **GitHub Actions**.
2. Open **Actions → Deploy website to GitHub Pages → Run workflow** and select `main` to deploy the latest workflow.

The workflow uses Node.js 24 actions. Do not add `enablement: true` with the default `GITHUB_TOKEN`: automatic Pages creation requires a separate, more privileged token. Enabling Pages in Settings avoids adding another credential.

After deployment succeeds, the expected address is `https://pruthvirajksuresh.github.io/adidev/`. Subsequent pushes to `main` deploy automatically.

The workflow follows [GitHub’s custom Pages workflow documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

## Editing the site

- `index.html`: company text, sections, navigation, and metadata.
- `assets/style.css`: colors, typography, CSS artwork, and responsive layouts.
- `assets/site.js`: mobile menu and current footer year.
- `.github/workflows/pages.yml`: build and deployment workflow.

The website has no backend, tracking, or form submissions. Fonts are loaded from Google Fonts, with local sans-serif fallbacks.
