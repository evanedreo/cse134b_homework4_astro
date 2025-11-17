---
title: "Minimal JavaScript Patterns for Static Sites"
description: "Patterns you can borrow to keep your Astro site almost entirely static while still feeling thoughtful and modern."
pubDate: 2024-10-05
tags: ["minimal-js", "ux", "design", "best-practices"]
hero: "Use markup, CSS, and build-time work before reaching for client-side JavaScript."
---

It is surprisingly easy to reach for JavaScript when you do not need it.

Dropdown? JS. Tabs? JS. Animated button? Definitely JS… right?

In a static-site world—especially one focused on performance—the better question is:

> Could this be done with **HTML, CSS, or build-time work instead of runtime JavaScript**?

## Pattern 1: Use semantic HTML as your “framework”

The fastest component library you will ever ship is the one that is already in the browser:

- `<details>` + `<summary>` gives you disclosure widgets for free.
- `<nav>`, `<header>`, `<main>`, and `<footer>` handle most layout semantics.
- `<article>` and `<section>` give structure to posts and docs.

Astro encourages this because you are not forced into a client-side framework mental model. Each page is just HTML with
some sugar.

## Pattern 2: Reach for CSS before JS

A small amount of well-structured CSS can replace entire interactive components when your content is static:

- Use **flex and grid** for layout instead of script-driven positioning.
- Use the `:target` selector for in-page navigation and “tabbed” content.
- Leverage `prefers-reduced-motion` for animation that degrades gracefully.

In this project, the homepage hero, card hover states, and layout responsiveness are all handled with CSS. Astro simply
bundles those styles and ships them once.

## Pattern 3: Precompute as much as possible at build time

Instead of loading data on the client, try to answer these questions:

- Can this be computed when we run `astro build`?
- Is it okay to rebuild when content changes instead of fetching at runtime?

Blog archives, tag pages, static navigation, and “related posts” often fall into this category. In this demo, the
homepage and blog index both use `getCollection('blog')` to build lists of posts up front.

The result is a site that still feels curated and alive—but with a JavaScript payload that rounds to zero.


