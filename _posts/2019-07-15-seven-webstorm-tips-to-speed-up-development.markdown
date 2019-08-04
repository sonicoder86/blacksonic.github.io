---
layout: post
title: 7 Webstorm Tips to Speed Up Development
date: 2019-07-28 15:09:00
description: 7 Webstorm Tips to Speed Up Development
---
Webstorm is an exceptionally good IDE for web development.
It has many useful features to make our lives easier, 
all of them aiming to automate the repetitive parts of coding.
Looking back at the speed of coding when I've started it seems like snail's pace.
The difference is not in the speed of my typing, but in what features and plugins I have started to use in the editor.
In this article I've collected the things I think added the most value in terms of speed.

### Live Templates

Live templates are useful to quickly insert frequently used code pieces. Every template has an abbreviation that activates the insertion. When you type the abbreviation into the code and hit the tab button, the editor expands into the template. The template can have variables also: variables have to be filled out when inserting the template.

Here is an example. We develop in TDD (Test Driven Development) and write a lot of tests. I have a live template for test cases: the abbreviation is `it` and the template is:

{% highlight javascript %}
it('should $DESCRIPTION$', function() {
  $END$
});
{% endhighlight %}

When I expand the `it` abbreviation it is expanded into the code piece and I have to write the desription after `should`.
When done with the variable editing, the cursor is placed to the `$END$` placeholder.

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
