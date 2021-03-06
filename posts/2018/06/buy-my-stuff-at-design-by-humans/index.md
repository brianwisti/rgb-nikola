---
date: 2018-06-12T00:00:00Z
draft: false
store:
- image: pegs-mandala-shirt.jpg
  link: https://www.designbyhumans.com/shop/t-shirt/men/pegs-mandala/933514/
  name: Pegs Mandala
tags:
- drawing
- infinite painter
- hugo
- buy me
title: Buy My Stuff At Design by Hümans
updated: 2018-06-26T00:00:00Z
url: /2018/06/12/buy-my-stuff
year: '2018'
category: craft
previewimage: /images/2018/06/buy-my-stuff-at-design-by-humans/cover.png
---


I opened a [store][] on the Design by Hümans site! I also made [Hugo][] warn me when I forget purchase links.

[store]: https://www.designbyhumans.com/shop/randomgeek/
[Hugo]: /tags/hugo
<!-- TEASER_END -->

Well, one design. I only got things going yesterday, with a quick sketch on a plain white background. Future
plans include adjusting old designs and creating new ones for the store, with an intended pace of roughly one
design per week.

Of course I already worked out the site integration. Everything on Random Geekery tagged ["buy me"][] should
have a direct link to its page on the [store][]. I get a lovely Hugo [`errorf`][] message if I forget the link.

    {{- if in .Params.tags "buy me" -}}
      {{- if isset .Params "purchase" -}}
        {{- with .Params.purchase -}}
          <p class="cover-link">
            <a href="{{ .url }}" target="_blank">{{ .caption }}</a>
          </p>
        {{- end -}}
      {{- else -}}
        {{ errorf "%s Tagged 'buy me' without purchase front matter!" .File.Path }}
      {{- end -}}
    {{- end -}}

My partial is a little clunky, but it worked. I can improve it later.

****

And then a couple weeks later I realized my needs would be better served by a new section than by a tag.

****

["buy me"]: /tags/buy-me
[`errorf`]: http://gohugo.io/functions/errorf/

