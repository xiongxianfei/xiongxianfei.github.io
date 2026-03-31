# 熊贤飞的博客 · Xianfei's Blog

> 技术 · 思考 · 生活

Personal blog of [熊贤飞 (Xianfei)](https://github.com/xiongxianfei), built with [Hugo](https://gohugo.io/) and the [Stack](https://github.com/CaiJimmy/hugo-theme-stack) theme, hosted at [xiongxianfei.github.io](https://xiongxianfei.github.io).

## Tech Stack

- **Static site generator**: Hugo (extended)
- **Theme**: [hugo-theme-stack](https://github.com/CaiJimmy/hugo-theme-stack) (loaded via Hugo Modules)
- **Hosting**: GitHub Pages
- **CI/CD**: GitHub Actions — auto-deploy on push to `master`; theme auto-updated daily via cron

## Local Development

Prerequisites: [Git](https://git-scm.com/), [Go](https://go.dev/), [Hugo Extended](https://gohugo.io/installation/)

```bash
git clone https://github.com/xiongxianfei/xiongxianfei.github.io.git
cd xiongxianfei.github.io
hugo server -D
```

Then open http://localhost:1313 in your browser.

## Project Structure

```
config/_default/      # Site configuration (Hugo, params, menu, languages)
content/
  post/               # Blog posts (bilingual: index.zh-cn.md + index.en.md)
  page/               # Static pages (about, links, archives, search)
assets/
  img/                # Images (avatar, etc.)
  icons/              # Custom SVG icons
static/               # Static files served as-is
```

## Update Theme

```bash
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v3
hugo mod tidy
```

The theme is also updated automatically every day via a GitHub Actions cron job.

## Deploy

Push to `master` — GitHub Actions builds the site with `hugo --minify --gc` and deploys to the `gh-pages` branch automatically.
