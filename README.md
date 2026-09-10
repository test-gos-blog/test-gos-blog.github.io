# GrapheneOS Blog

This site is made with [Zola](https://www.getzola.org/).

Use `zola serve` for to view/develop locally. By default, it uses `http://127.0.0.1:1111`.

To build, use `zola build`, which creates a `public` directory.

## Adding a new post

Adding a post is simple. I've chosen to have the created date in the filename so they're sorted. Filenames use `YYYY-MM-DD-post-slug.md`.

Zola uses `+++` before and after the frontmatter, which is TOML. This site is set up to require two fields there, for example:

```
+++
title = "Post title"
description = "Post description (used in meta tags for description and og:description)"
+++
```

`updated` can be added if a post is updated. Posts list is sorted by the updated date.
`authors` accepts an array of authors. Authors do not show up on the main site, but are included in `atom.xml`. The default author is set in `zola.toml`.
`extra.category` / `extra.categories`, see next section.

## Categories

The main site doesn't feature categories to keep things simple. However, if categories are added, they show up in the `atom.xml` feed.

`extra.category` takes a string value. `extra.categories` takes an array.

## Attaching images

For the demo site, images are stored in `static/images/`. To add an image to a post, use `![alt](/images/image.jpg)`.

## CSS

This site copies the `main.css` file from the GrapheneOS main website, for now without any changes. Blog-specific CSS is saved in `main-blog.css`.