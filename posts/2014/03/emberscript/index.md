---
aliases:
- /tools/2014/03/26_emberscript.html
- /post/2014/emberscript/
date: 2014-03-26T00:00:00Z
slug: emberscript
tags:
- coffeescript
- javascript
title: EmberScript
type: post
year: '2014'
category: tools
---
[Ember.js](http://emberjs.com/) is an impressive piece of work. It can also be painfully verbose. A little syntactic sugar would make that go down easier. [EmberScript](http://emberscript.com/) is [CoffeeScript](http://coffeescript.org/) with fine-tuning specifically for Ember.js. Fine-tuning includes bits like replacing `class` and `extends` with `Ember.class` and `Ember.extends`.
<!-- TEASER_END -->

The simple example from the documentation:
    
~~~ coffeescript
class PostsController extends Ember.ArrayController
  trimmedPosts: ~>
    @content.slice(0, 3)
~~~ 

would expand out to
    
~~~ javascript
var PostsController;
var get$ = Ember.get;
PostsController = Ember.ArrayController.extend({
  trimmedPosts: Ember.computed(function () {
    return get$(this, 'content').slice(0, 3);
  }).property('content.@each')
});
~~~ 

Even if your team is using [RequireJS](http://requirejs.org/), it should look better than the vanilla JavaScript.
    
~~~ coffeescript
require [
  "lodash"
  "cs!models/PostModel"
], (_, PostModel) ->
  class PostsController extends Ember.ArrayController
    trimmedPosts: ~>
      # ...
      @content.slice(0, 3)
  return PostsController
~~~ 

The challenge is that in order to simplify the code we write, we've added layers between us and the code that the browser actually sees. CoffeeScript could interact weirdly with our dependencies, and EmberScript will undoubtedly have its own issues. Automated tests become even more important.

I need to think on this some more.
