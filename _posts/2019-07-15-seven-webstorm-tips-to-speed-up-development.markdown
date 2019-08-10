---
layout: post
title: 7 Webstorm Tips to Speed Up Development
date: 2019-07-28 15:09:00
description: 7 Webstorm Tips to Speed Up Development
---
[Webstorm] is an excellent IDE for web development. It has many useful features to make our lives easier, all of them aiming to automate the repetitive parts of coding. Looking back at my coding speed years ago seems like snail's pace. The difference is not in my typing speed, but in what features and plugins I have started to use. I've collected the things that add the most value to this speedup in this article.

### Live Templates

[Live templates] are useful to insert frequently used code pieces quickly. When you type the abbreviation and hit the tab button, the editor adds the whole template. The template can have placeholders also: they have to be filled out to complete the insertion.

Let's look at an example. We develop in TDD ([Test Driven Development]) and write many tests. Using Mocha and Jasmine as test frameworks, you have to insert `describe` and `it` blocks. Typing every character of these blocks is the repetitive way of doing it.

The quick way is to create a live template for the `describe` block (abbreviation: `de`).

```javascript
describe('$TESTGROUP$', function() {
  $END$
});
```

Also, create one for the `it` block (abbreviation: `it`).
 
```javascript
it('should $TESTCASE$', function() {
  $END$
});
```

The placeholders are started and ended with `$` signs. The placeholder `$END$` has a special meaning: this is the place of the cursor after the insertion.

![Live Template](https://thepracticaldev.s3.amazonaws.com/i/27yhd9sw3gdcvpim3yy8.gif)

### Search Everywhere

Searching for text in project files is a common feature in most IDEs, but searching for other things like actions in the menu bar or declarations are rare in other editors. The best thing you can search for files, menu actions, and declarations with a single command: just double press the `Shift` button and [start searching everywhere][Search Everywhere].

![Search Everywhere](https://thepracticaldev.s3.amazonaws.com/i/3k8ow6bpl981zml7tz5c.gif)

### Prettier Plugin

[Prettier] is an opinionated code formatter supporting many languages like Javascript, Typescript, CSS, HTML, etc. By using it, you can save time and energy by automating code formatting.
You can add Prettier to Webstorm [through its plugin][Prettier Webstorm Plugin]. To make code formatting automatic, you have to add a file watcher also. [This file watcher][Prettier File Watcher] listens to save events, and when it occurs, runs Prettier code formatting on the saved file.
If you don't like automatic code updates, it can be done manually with a keyboard shortcut.

![](https://thepracticaldev.s3.amazonaws.com/i/nr348lwjbosn6nrwdy43.png)

### Refactoring

When the code gets messy, or we find duplicate parts, we tend to do refactoring. If the code what we refactor is used in many places, it can be an error-prone task. [Webstorm helps us][Refactoring] in this situation with its built-in refactoring capabilities. If the target is a variable, we can rename, extract, inline, or move it elsewhere with a single mouse click. The same goes for methods.

![](https://thepracticaldev.s3.amazonaws.com/i/9tox73sly6zji7oiia3x.png)

### Default Keymap

Lorem ipsum

### Keypromoter Plugin

Lorem ipsum

### Keyboard Shortcuts

Lorem ipsum

Although it has a subscription model to use, you can also opt-in for the Early Access Program and use it for free.

[Webstorm]: https://www.jetbrains.com/webstorm/
[Live Templates]: https://www.jetbrains.com/help/webstorm/using-live-templates.html
[Test Driven Development]: https://technologyconversations.com/2013/12/20/test-driven-development-tdd-example-walkthrough/
[Search Everywhere]: https://www.jetbrains.com/help/webstorm/searching-everywhere.html
[Prettier]: https://prettier.io/
[Prettier Webstorm Plugin]: https://plugins.jetbrains.com/plugin/10456-prettier
[Prettier File Watcher]: https://prettier.io/docs/en/webstorm.html#running-prettier-on-save-using-file-watcher
[Refactoring]: https://www.jetbrains.com/help/webstorm/refactoring-source-code.html
