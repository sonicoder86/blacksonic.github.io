---
layout: post
title: 9 Webstorm Productivity Tips
date: 2019-07-28 15:09:00
description: 9 Webstorm Productivity Tips
tags: productivity, javascript, webdev, showdev
---
[Webstorm] is an excellent IDE for web development. It has many useful features to make our lives easier, all of them aiming to automate the repetitive parts of coding. Looking back at my coding speed years ago seems like snail's pace. The difference is not in my typing speed, but how much I know about the tool I use. Knowing the tool means knowing the features it offers. I've collected those features that add the most value to this speedup.

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

![Live Templates](https://thepracticaldev.s3.amazonaws.com/i/27yhd9sw3gdcvpim3yy8.gif)

### Search Everywhere

Searching for text in project files is a common feature in most IDEs, but searching for other things like actions in the menu bar or declarations are rare in other editors. The best thing you can search for files, menu actions,  and declarations with a single command: just double press the `Shift` button and [start searching everywhere][Search Everywhere].

![Search Everywhere](https://thepracticaldev.s3.amazonaws.com/i/3k8ow6bpl981zml7tz5c.gif)

### Prettier

[Prettier] is an opinionated code formatter supporting many languages like Javascript, Typescript, CSS, HTML, etc. By using it, you can save time and energy by automating code formatting.
You can add Prettier to Webstorm [through its plugin][Prettier Webstorm Plugin]. To make code formatting automatic, you have to add a file watcher also. [This file watcher][Prettier File Watcher] will listen to save events, and when it occurs, runs Prettier code formatting on the saved file.
If you don't like automatic code updates, it can be done manually with a keyboard shortcut.

![Prettier](https://thepracticaldev.s3.amazonaws.com/i/djkf62duzm0z7obvbzn9.jpg)

### Refactoring

When the code gets messy, or we find duplicate parts, we tend to do refactoring. If the code what we refactor is used in many places, it can be an error-prone task. [Webstorm helps us][Refactoring] in this situation with its built-in refactoring capabilities. If the target is a variable, we can rename, extract, inline, or move it elsewhere with a single mouse click. The same goes for methods.

![Refactoring](https://thepracticaldev.s3.amazonaws.com/i/591fltyi7z28vykg1pu4.png)

### Multi-cursor editing

Most of the time, we used to edit the code in one place where the cursor is waiting. There are occasions when we have to do the same editing in different places. The straightforward solution is to edit it in one place, copy it, and paste it to all the locations. The quicker way is to place the cursor to multiple locations by pressing the Alt key (⌥) and clicking the locations. The cursor appears at all the locations where we clicked, and typing happens where the cursors are.

![Multiple Cursor](https://thepracticaldev.s3.amazonaws.com/i/buxx9i0lgo2aqq4cei8q.gif)

A particular case is when the places we want to edit are in the same column. At this point, we can switch to column selection mode: instead of lines, we can select columns and edit the code inside these columns.

![Column Selection Mode](https://thepracticaldev.s3.amazonaws.com/i/a2dxbcyct51r8emjzbws.gif)

A third multiple-cursor use-case is when we select all the occurrences of the selected text (Edit > Find > Select All Accourences) and the typing/deletion happens everywhere.

### Code Navigation

If you use a library and you want to know how that class/function behaves, you have to search and open that file. [Webstorm makes this navigation][Code Navigation] a lot easier. Holding down the Command button (⌘) turns the cursor into definition revealing mode. If you hover an imported class/function, it shows its interface. Clicking the hovered element results in navigating to the definition. You can do the navigation without using the cursor by pressing Command + B. Now you know the definition, but want to go back to the previous place. Webstorm can navigate back to the last edit location (⌘ + ⌥ + ←), making code navigation extremely fast.

![Code Navigation](https://thepracticaldev.s3.amazonaws.com/i/a0hf2ne22qii9gy8564u.png)

### Key Promoter

Webstorm has more than 100 shortcuts by default for nearly all the actions and code modifications. Do you know all of them? I don't know either. However, [the key promoter plugin][Key Promoter] informs you if you don't use them. When you do an interaction that you can do with a keyboard shortcut, the plugin tells it in the bottom right corner.

![Key Promoter](https://thepracticaldev.s3.amazonaws.com/i/4lrnj4uav6039j32hk66.png)

### Keyboard Shortcuts

The promoter is a great way to learn the shortcuts for the things you use, but what about those you don't know? It pays off to read through the list of the shortcuts at least once. I have created a list about those that I find the most useful.

- Delete line (⌘ + ⌫)
- Move line up/down (⇧ + ⌥ + ↑ or ↓)
- Show preferences (⌘ + ,)
- Duplicate line or selection (⌘ + D)
- Search everywhere (double ⇧)
- Expand or shrink selection (⌥ + ↑ or ↓)
- Column selection mode (⌘ + ⇧ + 8)
- Find in path (⌘ + ⇧ + F)
- Replace in path (⌘ + ⇧ + R)
- Rename definition or variable (⇧ + F6)
- Go to declaration (⌘ + B, ⌘ + Click)
- Go to last edit location (⌘ + ⌥ + ← or →)
- Code completion (⌘ + Space)
- Multiple cursors (⌥ + Click)
- Show intentions (⌥ + ⏎)
- Trigger column selection mode (⌘ + ⇧ + 8)
- Show intentions (⌥ + ⏎)
- Comment/uncomment current line/selection (⌘ + /)
- Reformat code (⌘ + ⌥ + L)
- Select all occurrences (^ + ⌘ + G)

I have listed the default shortcuts on Mac. You can find the Windows and Linux equivalents on the [reference page][Shortcuts Reference]. They have even shortcut lists where they compare different lists to one another.

### Built-in Terminal

Why would you leave the IDE to use the command line if you have one inside it? Webstorm has a built-in terminal that supports multiple sessions, and you can access with a hotkey.

### Summary

We have gone through many different features that can speed up development and make you more productive. It is up to you whether you use them or not. The most important thing is to know about them. If you are starting to use a tool, learn about it. If you are developing with it for a while recheck its features in an orderly manner. Because you become more productive by mastering the tools you use.

[Webstorm]: https://www.jetbrains.com/webstorm/
[Live Templates]: https://www.jetbrains.com/help/webstorm/using-live-templates.html
[Test Driven Development]: https://technologyconversations.com/2013/12/20/test-driven-development-tdd-example-walkthrough/
[Search Everywhere]: https://www.jetbrains.com/help/webstorm/searching-everywhere.html
[Prettier]: https://prettier.io/
[Prettier Webstorm Plugin]: https://plugins.jetbrains.com/plugin/10456-prettier
[Prettier File Watcher]: https://prettier.io/docs/en/webstorm.html#running-prettier-on-save-using-file-watcher
[Refactoring]: https://www.jetbrains.com/help/webstorm/refactoring-source-code.html
[Key Promoter]: https://plugins.jetbrains.com/plugin/9792-key-promoter-x
[Shortcuts Reference]: https://www.jetbrains.com/help/rider/Reference_Keyboard_Shortcuts_Index.html
[Code Navigation]: https://www.jetbrains.com/help/webstorm/navigating-through-the-source-code.html
