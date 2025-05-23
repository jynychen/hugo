---
title: IsMenuCurrent
description: Reports whether the given Page object matches the Page object associated with the given menu entry in the given menu.
categories: []
keywords: []
params:
  functions_and_methods:
    returnType: bool
    signatures: [PAGE.IsMenuCurrent MENU MENUENTRY]
aliases: [/functions/ismenucurrent]
---

```go-html-template
{{ $currentPage := . }}
{{ range site.Menus.main }}
  {{ if $currentPage.IsMenuCurrent .Menu . }}
    <a class="active" aria-current="page" href="{{ .URL }}">{{ .Name }}</a>
  {{ else if $currentPage.HasMenuCurrent .Menu . }}
    <a class="ancestor" aria-current="true" href="{{ .URL }}">{{ .Name }}</a>
  {{ else }}
    <a href="{{ .URL }}">{{ .Name }}</a>
  {{ end }}
{{ end }}
```

See [menu templates] for a complete example.

> [!note]
> When using this method you must either define the menu entry in front matter, or specify a `pageRef` property when defining the menu entry in your site configuration.

[menu templates]: /templates/menu/#example
