---
title: 'Hugo Wikilinks'
date: 2025-04-06

keywords:
  - Hugo Wikilinks
  - Hugo
  - Wikilinks
---

Wikilinks are a standard of many / most wiki software.  However, Hugo does not have support for them.  They have a simple form of `[[Page Title]]` or `[[Page Title|Display Text]]`, which makes them very useful for quick linking.  This is how I implemented something like them.

<!--more-->

## Shortcode Proof of Concept

First, let's start with a shortcode that gets us most of the logic.  The being that shortcode `{ {% wl "Hugo Wikilinks" %}}` would link to this page.

Some examples
- `wl "Hugo Wikilinks"`: {{% wl "Hugo Wikilinks" %}}
- `wl "Hugo Wikilinks" "Another name"`: {{% wl "Hugo Wikilinks" "Another name" %}}
- `wl "hugo wikilinks"`: {{% wl "Hugo Wikilinks" %}}
- `wl "invalid"`: {{% wl "invalid" %}}
- `wl "FOO" "bar"`: {{% wl "FOO" "bar" %}}

> [!NOTE]
> For ease we'll use the markdown form of calling shortcodes: `%` instead of `<`.

The contents of `layouts/shortcodes/wl.html`:

```plain {linenos=true}
{{- $title := .Get 0 }}
{{- $display := .Get 1 | default "" }}
{{- $page := "" }}

{{- range .Site.RegularPages }}
  {{- if eq (lower .Title) (lower $title) }}
    {{- $page = .}}
    {{- if eq $display "" }}
      {{- $display = .LinkTitle }}
    {{- end }}
  {{- end }}
{{- end }}

{{- if ne $page "" }}
  {{- printf "[%s](%s)" $display $page.RelPermalink }}
{{- else }}
  {{- $display | default $title }}
{{- end }}
```

- Line 1: Gets the Title of the page for comparison
- 2: Gets the display value override
- 5 - 12: Searches all regular pages (ones with valid titles) for the one that matches
  - 8 - 10: Uses the Page's Link Title if an override is not provided
- 14 - 18: Prints either the wiki link or the display string or the title

This is a 90% solution.  However, we can make it the 100% solution with a lot more logic.  So let's leave it here for now.

If you are interested in more of a solution then [milafrerichs/hugo-wikilinks](https://github.com/milafrerichs/hugo-wikilinks) has a good start.
