# Project: xiongxianfei.github.io

Personal blog of 熊贤飞 (Xianfei). Built with Hugo + hugo-theme-stack, deployed to GitHub Pages.

- **URL**: https://xiongxianfei.github.io
- **Languages**: Bilingual — `zh-cn` (primary), `en` (secondary)
- **Theme**: [hugo-theme-stack v3](https://github.com/CaiJimmy/hugo-theme-stack) via Hugo Modules (not vendored)

## Build & Dev Commands

```bash
hugo server -D              # local dev server (includes drafts)
hugo --minify --gc          # production build (what CI runs)
```

Update theme:
```bash
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v3
hugo mod tidy
```

## Project Structure

```
config/_default/           # Site config (TOML split files)
├── config.toml            #   Base config: title, language, baseurl
├── params.toml            #   Theme params: sidebar, footer, widgets, comments
├── menu.toml              #   Social links (GitHub, Twitter, LinkedIn, Email)
├── languages.toml         #   Bilingual config (zh-cn + en)
├── markup.toml            #   Markdown rendering settings
├── permalinks.toml        #   URL structure
└── related.toml           #   Related content config

content/
├── post/                  #   Blog posts (one directory per post)
│   └── <slug>/
│       ├── index.zh-cn.md #     Chinese version
│       └── index.en.md    #     English version
└── page/                  #   Static pages (about, links, archives, search)

assets/
├── scss/custom.scss       #   Appearance overrides (indigo accent, Noto Serif SC)
├── icons/                 #   Custom SVG icons extending the theme (brand-linkedin, mail)
└── img/avatar.png         #   Sidebar avatar image

layouts/
└── _partials/head/
    └── custom-font.html   #   Google Fonts override (Noto Serif SC + Lato)

static/                    #   Static files served as-is (favicon, etc.)
.github/workflows/         #   CI: deploy.yml (build + deploy), update-theme.yml (daily cron)
```

## Key Conventions

- **Bilingual posts**: Every post needs both `index.zh-cn.md` and `index.en.md` in its directory
- **Theme overrides**: Don't edit the theme directly. Override templates in `layouts/` mirroring the theme's structure; override styles in `assets/scss/custom.scss`
- **Custom icons**: Place SVG files in `assets/icons/` — they extend/override the theme's built-in icon set
- **CJK support**: `hasCJKLanguage = true` must stay enabled in `config.toml` for correct word count and summaries
- **Config format**: All config is TOML, split across files in `config/_default/`

## Deployment

- Push to `master` → GitHub Actions builds with `hugo --minify --gc` → deploys to `gh-pages` branch
- Theme is auto-updated daily via cron workflow (`.github/workflows/update-theme.yml`)
- Never commit: `public/`, `resources/`, `.hugo_build.lock` (in `.gitignore`)

## Known TODOs

- Social URLs in `menu.toml` (Twitter, LinkedIn, Email) are still placeholders — need real values
- Comments are disabled; Giscus planned once GitHub Discussions is enabled on the repo
- `static/favicon.png` is referenced in config but may not exist yet
- Avatar at `assets/img/avatar.png` is the default placeholder
