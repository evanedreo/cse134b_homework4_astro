---
title: "Astro Content Collections Deep Dive"
description: "A practical walkthrough of how content collections keep large sets of Markdown posts organized, type-safe, and queryable."
pubDate: 2024-10-10
tags: ["astro", "content-collections", "markdown", "tooling"]
hero: "Model your content once, then let Astro enforce it for every post."
---

Astro’s **content collections** are one of the most useful tools for serious content sites.

Instead of sprinkling Markdown files all over `src/pages`, you define a collection—like `blog`—and describe what every
entry in that collection must contain:

- `title`: the post’s display name.
- `description`: a short summary used on cards and meta tags.
- `pubDate`: a real JavaScript `Date` (validated via Zod).
- `tags`: an array of strings you can use for filtering and grouping.

Inside `src/content/config.ts`, we use `defineCollection` and a Zod schema to enforce this for every blog post. If you
forget a `title` or pass an invalid date, Astro catches it at build time instead of shipping a broken page.

## Querying content

Once a collection is defined, Astro gives you a small but powerful API:

- `getCollection('blog')` returns all posts (plus their metadata).
- You can filter, sort, and map over entries just like regular data.

This is what powers:

- The homepage “recent posts” section.
- The dedicated blog index at `/blog/`.
- Static routes for each individual post.

Everything is still generated as HTML, but the developer experience feels closer to working with a headless CMS.


