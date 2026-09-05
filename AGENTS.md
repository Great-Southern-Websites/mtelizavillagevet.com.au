# Working on this site

This is a Quarkus Roq static site for Mt Eliza Village Vet. Keep it that way.

- Content lives in `content/` (front matter + Markdown or HTML), layouts and partials in
  `templates/`, styles in `public/css/main.css`, images in `public/images/`.
- Links between pages use `{=site.url('path')}`; images use `{=site.image('name.png')}`
  or `{=site.url('images/name.png')}`. Never hard-code the domain.
- `quarkus.qute.alt-expr-syntax=true` is on: Qute expressions are `{=expr}`. Wrap inline
  `<script>` and `<style>` bodies in `{| ... |}` so braces are left alone.
- Every page must render well at 360px wide. Tap targets at least 44px. Respect
  `prefers-reduced-motion`.
- Writing style: plain Australian English, no em or en dashes, no marketing filler, no
  exclamation marks, no emoji, nothing the clinic did not say. The elf hands you the full
  list as STYLE.md when it asks for work.
- Verify before you finish: `QUARKUS_HTTP_PORT=8765 QUARKUS_ROQ_GENERATOR_BATCH=true mvn -q -B package quarkus:run`
  must succeed and `target/roq/index.html` must exist.
- Do not add build tooling, server code, or third-party scripts beyond the embeds the site
  already relies on (the online booking link, the Facebook feed).

## Blog posts

This site's collection is `blog`, not `posts`: articles go in
`content/blog/YYYY-MM-DD-slug.md` with front matter `title` and `description`; the
layout `blog-post` comes from `site.collections.blog.layout` in
`config/application.properties`. The listing page is `content/blog.html`; do not create a
second one. When a request talks about "posts" or "news", it means this blog collection.
