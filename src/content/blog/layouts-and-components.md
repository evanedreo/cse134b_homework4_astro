---
title: "Designing Reusable Layouts and Components in Astro"
description: "How this project factors shared chrome, navigation, and post cards into reusable pieces that keep the static site consistent."
pubDate: 2024-10-14
tags: ["components", "layouts", "architecture", "cse134b"]
hero: "Build a layout once, reuse it for the homepage, blog, and static pages."
---

For a course assignment, it is not enough to just “have multiple pages.” You also need **clear, meaningful reuse of
layouts and components**.

In this project:

- `BaseLayout.astro` owns the global `<html>`, `<head>`, and `<body>` structure.
- `SiteHeader.astro` and `SiteFooter.astro` are imported by the layout and appear on every page.
- `PostCard.astro` renders a consistent summary view of each blog post.
- `TagList.astro` formats post tags in one place and is reused across listing pages.

This architecture means:

- You can add new pages (like `/about` or `/guides`) that automatically inherit the same chrome.
- You can change the header or footer in one file, and every page updates.
- You can tune the design of cards in one component instead of editing markup in multiple routes.

Astro encourages this modular approach while still compiling everything down to static HTML.


