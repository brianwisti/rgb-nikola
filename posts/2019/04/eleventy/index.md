---
announcements:
  mastodon: https://hackers.town/@randomgeek/101882459939490036
  twitter: https://twitter.com/brianwisti/status/1114712015904366592
date: 2019-04-06T00:00:00Z
draft: false
series:
- Artisanal Blogging With Eleventy
tags:
- Node.js
- Eleventy
title: Eleventy
year: '2019'
category: tools
previewimage: /images/2019/04/eleventy/cover.jpg
---

Spring has sprung, and with it comes thoughts of new tools to build a Web site. Okay no the picture has
nothing to do with Web sites but isn't it pretty?

<!-- TEASER_END -->

I use [Hugo][] to build this site, and have for [a while][] now. Hugo builds fast, includes
loads of features, and by now has the added benefit of being familiar. It's
still fun to see what else people use for their sites, though.

[Eleventy][] caught my eye with its claims at being a
simpler static site generator. [Node.js][] powers Eleventy. That caught my
attention because of how much I've been using the platform at work recently.

[Hugo]: /tags/hugo
[a while]: {{< ref "/post/2015/hugo.md" >}}
[Eleventy]: https://www.11ty.io/
[Node.js]: https://nodejs.org/

Aided by the [core documentation][], I'll make a single page site with a
stylesheet. To my mind, that's the ["Hello World"][] of static site
generators. It covers the three core elements: content, layouts, and including
files outside of the content/layout flow (stylesheets, images, etc).

[core documentation]: https://www.11ty.io/docs/
["Hello World"]: https://en.wikipedia.org/wiki/%22Hello,_World!%22_program

****

## But I just want to blog

Use one of the [starter projects][], packaged with the configuration and plugins needed
for blogging in Eleventy. I don't know enough about Eleventy or Node.js to
tell you which one to use though!

****

[starter projects]: https://www.11ty.io/docs/starter/

## Starting fresh with `package.json`

I'll follow the [suggestion][] from docs and install Eleventy locally to
the site project.

[suggestion]: https://www.11ty.io/docs/local-installation/

``` shell
$ mkdir rgb-eleventy
$ cd rgb-eleventy
$ npm init
$ npm install --save-dev @11ty/eleventy
$ npx eleventy
Processed 0 files in 0.03 seconds
```

Yay, the process works! Now I need content.

## Content: Read Markdown, write HTML

I can stick with familiar Markdown content, since Eleventy supports it through
[markdown-it][]. Throw a couple sentences in `index.md`:

[markdown-it]: https://markdown-it.github.io/

``` markdown
# Random Geekery Blog

But in [Eleventy][].

[Eleventy]: https://www.11ty.io/
```

And rebuild the site.

``` shell
$ npx eleventy
Writing _site/index.html from ./index.md.
Processed 1 file in 0.07 seconds
```

So what's in `_site/index.html`?

``` html
<h1>Random Geekery Blog</h1>
<p>But in <a href="https://www.11ty.io/">Eleventy</a>.</p>
```

That's HTML, all right. But I need a full HTML page. Rather than make my content file more complex, I'll use a
layout template.

## Templates

Eleventy [layouts][] are similar to layouts in other site generators. They
provide a skeletal HTML file along with special directives. These files get
combined with your content files, creating complete pages that have a consistent
layout and design.

Rather than focus on all the templating languages Eleventy supports, I'll use
[Nunjucks][].
I don't want to spend time looking at all the templating languages supported by
Eleventy. I'll just use [Nunjucks][] since it appears frequently in the docs.

[layouts]: https://www.11ty.io/docs/layouts/
[Nunjucks]: https://mozilla.github.io/nunjucks/

My `_includes/layout.njk` is pretty much your basic minimal HTML 5 skeleton.

``` html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{title}}</title>
  </head>
  <body>
    <h1>{{title}}</h1>

    {{ content | safe }}
  </body>
</html>
```

`content` comes from the body of the content file, while `title` is in
`index.md`'s [front matter][]. That's also where I specify layout.

[front matter]: https://www.11ty.io/docs/data-frontmatter/

So yeah. I should probably add some front matter.

``` markdown

