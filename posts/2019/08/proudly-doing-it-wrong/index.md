---
announcements:
  mastodon: https://hackers.town/@randomgeek/102601881134003629
  twitter: https://twitter.com/brianwisti/status/1160754746397011968
caption: Yeah that's Visual Studio Code. I'm trying new things.
date: 2019-08-11T20:04:00-07:00
tags:
- screenshot
- javascript
- no i know
- i'll fix it
title: Proudly doing it wrong
year: '2019'
category: note
type: micro
previewimage: /images/2019/08/proudly-doing-it-wrong/cover.png
---

1. write a [site weight][] script that prints a report to the console
2. make the script write the report to a file, and include the file in [/now][]. Now site building looks like:
    1. build the site
    2. weigh the site
    3. build the site and include the new report
    4. upload!
3. (today) make the script write the info as JSON instead
4. throw in some [vue.js][] to fetch the JSON and reproduce the original report format almost exactly.
5. profit?

But hey at least I don't need to rebuild the site after weighing it. And when free time next allows I'll learn
a little more Vue.js and make the report prettier.

[site weight]: {{< ref "/post/2019/weighing-files-with-python/index.md" >}}
[/now]: /now
[vue.js]: https://vuejs.org/
