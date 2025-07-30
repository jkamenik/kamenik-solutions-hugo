---
title: 'Emacs Full Screen'
date: 2015-02-10
lastmod: 2015-02-10

# Keywords help in classifying content
keywords:
  - Emacs Full Screen
  - Emacs
  - How to
---

On a Mac the short cut to put a window into full-screen mode is `ctrl + cmd + f`. Unfortunately this does not work directly for emacs. Here I will explain how I made it work.

{{< callout type=info >}}
This is only applicable to windowed versions of Emacs!
{{< /callout >}}

<!--more-->

First, I needed to figure out if it was possible to make emacs full screen. To do this I turned to the help system for a function `M+x fullscreen<tab>` did not turn up anything useful. Then I checked the apropos help command. `C+h a fullscreen` produced the following:

```
Type RET on an entry to view its full documentation.

toggle-frame-fullscreen     <f11>
   Toggle fullscreen mode of the selected frame.
```

That looks promising so I run it as an interact command: `M+x toggle-frame-fullscreen` and it does what I expect. Now to bind it to a key.

I added the following to my config:

```lisp
(global-set-key (kbd "C-s f") 'toggle-frame-fullscreen)
```

{{< callout type=info >}}
"s" is "super" which is what the "cmd" on a Mac maps to.
{{< /callout >}}

I run `C+x e` to evaluate the lisp code and then I use the keyboard combination `ctrl + cmd + f`, but nothing happens. What gives?

I use the help system describe-key to find out what it is bound to `C+h k <ret> ctrl + cmd + f` prints " is undefined."

As it turns out "ctrl + cmd" will almost always present as a numerical key value. Using the help system causes emacs to print what it sees when those buttons are pressed. It is simple matter of using angle bracket key form (like is printed). `(global-set-key (kbd "<C-s-268632070">) 'toggle-frame-fullscreen)` works like a champ!
