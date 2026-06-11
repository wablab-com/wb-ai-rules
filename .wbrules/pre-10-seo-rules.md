# SEO Rules (Web Only)

Load this file before starting any task that involves web frontend pages, public routing, metadata templates, or content structure.

## Page Metadata

- **Title Tags**: Ensure every page has a unique, descriptive, and keyword-relevant `<title>` tag. Keep titles between 50-60 characters and place the most important keywords at the beginning.
- **Meta Descriptions**: Provide a compelling, unique meta description for each page (between 150-160 characters) that accurately summarizes the content and includes a call to action.
- **Canonical Tags**: Implement `<link rel="canonical" href="...">` on every page to specify the preferred URL and prevent duplicate content issues across different parameters/routes.
- **Robots Directives**: Configure meta robots tags (e.g., `<meta name="robots" content="index, follow">` for public content or `noindex, nofollow` for staging/auth-locked pages).

## Document Structure & Semantic HTML

- **Heading Hierarchy**: Enforce a strict hierarchy starting with a single `<h1>` tag containing the page's primary topic. Use `<h2>`, `<h3>`, etc. in descending order without skipping levels.
- **Semantic Elements**: Structure pages using HTML5 semantic elements (e.g., `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`) rather than nesting generic `<div>` containers.
- **Interactive Element IDs**: Ensure all interactive elements have unique, descriptive IDs for browser automation, crawling, and accessibility testing.

## Links & Media

- **Descriptive Anchor Text**: Write descriptive text for links that contextually explains the destination. Avoid generic phrases like "click here" or "read more".
- **Image Accessibility**: Always provide descriptive, keyword-rich `alt` attributes for images. Leave `alt=""` only for purely decorative images.
- **Responsive Media**: Use responsive image elements (`<picture>`, `srcset`) and modern formats (e.g., WebP, AVIF) to optimize page load speeds.

## Structured Data

- **Schema Markup**: Add JSON-LD structured data schemas (e.g., Article, Product, Organization, FAQ, LocalBusiness) to help search engines understand page content and display rich snippets.

## Core Web Vitals & Performance

- **Speed & Stability**: Optimize Largest Contentful Paint (LCP) and Cumulative Layout Shift (CLS) through caching, lazy loading non-critical assets, and specifying size dimensions (`width` and `height`) on all media.
