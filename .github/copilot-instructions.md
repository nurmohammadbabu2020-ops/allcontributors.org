# Project instructions

This repository contains the All Contributors website and documentation, built with Astro and Starlight. The bot and CLI implementations live in separate repositories; do not assume their code is present here.

## Project structure

- Documentation pages belong under `src/content/docs/`. English pages in `src/content/docs/en/` are the source content.
- Shared Astro components belong in `src/components/`; site styles belong in `src/styles/`.
- Starlight configuration is in `astro.config.js`; related locale, sidebar, plugin, and redirect configuration is in `configs/`.
- Public files belong in `public/`; source images and other assets belong in `src/assets/`.
- Do not edit generated output in `dist/` or `.astro/`.

## Documentation and localization

- Follow the existing Starlight Markdown/MDX frontmatter, component, and link conventions.
- Manage translations through Crowdin. Do not create or update translated copies by hand unless the task specifically asks for it.
- If adding or moving a documentation page, update `configs/sidebar.config.ts` as needed, check links that point to the page, and update `configs/redirects.config.ts` when an old URL needs to keep working.
- Redirect targets must resolve to generated pages; the build validates this. The site uses locale-prefixed URLs, with the default locale configured in `astro.config.js`.

## Commands and validation

- Use pnpm, as declared by the `packageManager` field in `package.json`.
- Run `pnpm run sync` when Astro-generated types or content definitions need refreshing.
- Run `pnpm run lint` for ESLint checks and `pnpm run build` to validate and build the site.
- For changes affecting generated page links, build first, then run `pnpm run link-check-offline`. This checks local links without relying on network availability.
- CI also runs `pnpm dedupe --check`. There is no test script in `package.json`.
- `pnpm run check` is available for Astro diagnostics; run it when changes to components, content schemas, or Astro/TypeScript code warrant it.

## Change scope

- Make focused changes and preserve existing behavior and conventions.
- Keep locale definitions in `configs/locales.config.ts` consistent with the site's locale configuration.
- Avoid modifying the root `README.md` contributor table unless the task specifically concerns it.
