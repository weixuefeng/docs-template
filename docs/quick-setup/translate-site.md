---
sidebar_position: 4
---

# Translate Site

This section will cover:

- Basics on Translation in Docusaurus
- Pre-configs for Chinese Lanugages (zh)
- Add/remove a language
  - Docs location
  - Blog posts location
  - Pages location
- Translate default strings, navbar and footer, theme etc.

## Basics on Translation in Docusaurus

This template has a French translation for docs, but only one doc, `i18n/fr/docusaurus-plugin-content-docs/start.md`, is translated.

Because **English** is set to the _default_ language, for other languages, if there is no translation file, the **English** one will be used.

## Pre-configs for Chinese (zh) π¨π³π­π°π²π΄πΉπΌπΈπ¬

This boilerplate is using a Local Search plugin with index for Chinese (zh) support pre-configurated.

The local search plugin uses `nodejieba` to index Chinese language. It requires specified nodejs versions, and this is pre-configured in `.nvmrc` file.

If you won't be doing Chinese translation or using other search index services, you can remove `.nvmrc` file and remove `nodejieba` from your project:

```bash
yarn remove nodejieba
```

## Add/remove a language

This example will guide you to add **Spanish (es)** πͺπΈ to your website.

### Configure i18n

Update `defaultLocale` and `locales` in docusaurus config file

- defaultLocale: default language
- locales: languages in this site

Add `es` to locales:

```js {3,4}title="docusaurus.config.js"
const config = {
  i18n: {
    defaultLocale: 'en',
    locales: ['en', 'fr', 'es'],
  },
```

Update search setting in docusaurus config file, add `es` to the language:

```js {5} title="docusaurus.config.js"
const config = {
  plugins: [
    [require.resolve('@cmfcmf/docusaurus-search-local'), {
      // language of your documentation, see next section
      language: ["en", "fr", "es"],
    }]
  ],
```

### Translate a doc

Docs for `es` are placed under `i18n/es/docusaurus-plugin-content-docs/current/`

```bash
mkdir -p i18n/es/docusaurus-plugin-content-docs/current/

cp docs/start.md i18n/es/docusaurus-plugin-content-docs/current/start.md
```

Translate `i18n/es/docusaurus-plugin-content-docs/current/start.md` in Spanish.

### Translate a blog post

Blog posts for `es` are placed under `i18n/es/docusaurus-plugin-content-blog`

Copy your blog Markdown files to `i18n/es/docusaurus-plugin-content-blog`, and translate them:

### Translate pages

Pages for `es` are placed under `i18n/es/docusaurus-plugin-content-pages`

```bash
mkdir -p i18n/es/docusaurus-plugin-content-pages
cp -r src/pages/**.md i18n/es/docusaurus-plugin-content-pages
cp -r src/pages/**.mdx i18n/es/docusaurus-plugin-content-pages
```

## Translate other strings

Translate Navbar, Footer, Global strings in Docs and Blog, i18n strings in code is a ton of works. This template is using `docusaurus-theme-classic`, and it should be no setup for the UI translation out of the box.

Docusaurus provide a quick way to generate json files for all strings supports i18n by running:

```bash
# replace `es` for your desired language
yarn run write-translations -- --locale es
```

This will generate the following files:

```diff {5,8,11,12,14}
  project-root
  βββ i18n
  β   βββ es
  β       βββ docusaurus-plugin-content-blog
+ β       β   βββ options.json
  β       β
  β       βββ docusaurus-plugin-content-docs
+ β       β   βββ current.json
  β       β
  β       βββ docusaurus-theme-classic
+ β       β   βββ footer.json
+ β       β   βββ navbar.json
  β       β
+ β       βββ code.json
  .
```

You can continue translating other strings with the generated json files.

## Run local dev server in another language

```bash
yarn start -- --locale es
```
