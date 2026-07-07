# Romee Panchal's Blog

The site is built with [Hugo](https://gohugo.io/) and a pinned
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) submodule.

## Local development

```sh
git submodule update --init --recursive
hugo server -D
```

Open `http://localhost:1313`.

## Writing

Create an article bundle with:

```sh
hugo new content posts/my-article/index.md
```

Every article should define `summary`, `keyInsight`, `difficulty`, `lastmod`,
tags, and optional series metadata. Reusable callouts are available through:

```md
{{< callout type="insight" title="Why this matters" >}}
Callout content.
{{< /callout >}}
```

Supported callout types are `insight`, `mental-model`, `takeaway`, `definition`,
`note`, `warning`, and `common-mistake`.

Diagrams use Mermaid:

```md
{{< mermaid caption="Request flow" >}}
flowchart LR
  Browser --> API --> Model
{{< /mermaid >}}
```

## Deployment

Pushing `main` runs `.github/workflows/deploy.yml`. GitHub Pages must use
**GitHub Actions** as its source; generated `public/` files are not committed.
