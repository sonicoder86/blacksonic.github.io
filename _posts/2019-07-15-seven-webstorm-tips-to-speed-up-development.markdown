---
layout: post
title: 7 Webstorm Tips to Speed Up Development
date: 2019-07-28 15:09:00
description: 7 Webstorm Tips to Speed Up Development
---
Webstorm is an exceptionally good IDE for web development. It has many useful features to make our lives easier,  all of them aiming to automate the repetitive parts of coding. Looking back at my coding speed years ago seems like snail's pace. The difference is not in the speed of my typing, but in what features and plugins I have started to use in the editor. I've collected the things that add the most value to this speedup in this article.

### Live Templates

Live templates are useful to quickly insert frequently used code pieces. When you type the abbreviation of a live template and hit the tab button, the editor inserts the whole template. The template can have placeholders also: they have to be filled out to complete the insertion.

Let's look at an example. We develop in TDD (Test Driven Development) and write a lot of tests. Using Mocha and Jasmine as test frameworks, you have to insert `describe` and `it` blocks. Typing every character of these blocks is the repetitive way of doing it.

The quick way is to create a live template for the `describe` block (abbreviation: `de`).

{% highlight javascript %}
describe('$TESTGROUP$', function() {
  $END$
});
{% endhighlight %}

And create one for the `it` block (abbreviation: `it`).
 
{% highlight javascript %}
it('should $TESTCASE$', function() {
  $END$
});
{% endhighlight %}

The placeholders are started and ended with `$` signs. The placeholder `$END$` has a special meaning: this is the place of the cursor after the insertion.

### Search Actions

Lorem ipsum

### Refactoring

Lorem ipsum

### Prettier Plugin

Lorem ipsum

### Default Keymap

Lorem ipsum

### Keypromoter Plugin

Lorem ipsum

### Keyboard Shortcuts

Lorem ipsum

Although it has a subscription model to use, you can also opt-in for the Early Access Program and use it for free.
